# RVZ
## Introduction
'Robot VS Zombies' is a machine learning-based, survival-FPS, 3D Unity video-game, which utilizes a Recurrent Multilayer Neural Network Model to dynamically maintain the difficulty-level of gaming-sessions based on player's past performance. This automatic game-balancing system revolves around the broader subject of Dynamic Difficulty Adjustment (DDA), wherein various parameters, behaviors and scenarios pertaining to the game are changed on-the-fly during gameplay so as to make the video-game adaptive to the player's response. To study the scalability and viability of cloud gaming, the video-game was also hosted on the Amazon Cloud as a part of this project to exploit the valuable benefits that cloud-computing has to offer.

![DDA Idea Picture](ReadMe_Images/DDA_Concept.PNG)
## Game Access
### Download Links
The working copy of the video-game can be publicly accessed free-of-charge using the links below:
- [RVZ - Windows x86](https://goo.gl/fEfjAK)
- [RVZ - Windows x86_64](https://goo.gl/tVRqo1)

To run the video-game, simply download all of the files into one folder and run the executable file, 'RVZ.exe' 

### System Requirements
- Windows (32 or 64-bit machine)
- A modern Central Processing Unit (CPU) like Intel i5 Processor
- A decent Graphical Processing Unit (GPU) like NVidia GTX 960

## Objectives
The project provides an extension to the functionality of the traditional video games in the market. The dynamic game-balancing system coupled with the deployment of the game on a robust cloud infrastructure ensures a unique solution to the gamers, who are limited to graphical and computational resources as well as crave for an adaptive gaming experience. The objectives, in no particular order in accordance to importance, are mentioned below:
- To provide the gamer with a personalized gaming experience by periodically recording the player's in-game performance throughout the gaming-session. 
- To free the user from manually selecting the  difficulty during gameplay which can hinder the overall experience of the game.
- To eradicate the user's need for purchasing powerful computational machines that are usually expensive and subjected to obsoletion.  
- To decrease the dependency of hard-coded AI in video-games which are generally responsible for making games predictable and monotonous.

A quick use-case diagram highlights the stakeholders affected by this application:

![Use-Case Diagram](/ReadMe_Images/Use_Case_Diagram.PNG)

## Software Tools 
The software and environment graphics software, audio editing tools, coding environment, machine-learning package, data-visualizatopon used throughout the project are as follows:
- Unity 5 Game-Engine (C# programming language), for game-design and development 
- Microsoft Visual Studio IDE
- Blender, for 3D-modelling
- Adobe Photoshop, for photo-editing
- Audacity, for audio-editing
- Waikato Environment for Knowledge Analysis - Weka (Java Programming language), for machine-learning 
- Microsoft Excel, for data-visualization
- Amazon Web Services - AWS, for cloud-computing

## Governing Principles

### Dynamic Difficulty Adjustment (DDA)
The concept of DDA, which is to provide user-responsive game playing, is typically achieved by two basic approaches.

![Types of DDA](/ReadMe_Images/DDA%20_Types.PNG)

By replacing the traditional rule-based agents with learning-AI game bots, the Non-Player Character (NPC) becomes responsive to the player’s behaviors. These bots learn as they play with the human players, until when a stage arrives wherein the bots become experts in the game. However, at this point of time, the game can prove to be daunting for an unexperienced gamer, since the game bot has already learned most of the tricks and trades of the game.

By constantly updating various parameters through a series of pre-defined if-else statements and keeping track of the gamer’s responses, the gaming difficulty can be tailored to the player’s skill level. Such gaming parameters (for example, enemies’ weapon strength, bullet speed, etc.) can be changed dynamically during gameplay to manipulate the difficulty level of the game.

The project aims to demonstrate a hybrid implementation of both techniques, wherein the gamer’s parameters are calculated using certain statistics (for example, number of enemies killed in each round) and then fed to a learning classifier. The previously-trained learning classifier then outputs the new difficulty level in the game, and accordingly the gaming-difficulty parameters are updated. Likewise, the rule-based agents (NPCs) are maintained throughout to maintain a fixed set of rules that can be followed by the game bot.

### Cloud Gaming
Cloud gaming, also known as on-demand gaming. is the development and deployment of video games on robust and scalable-remote servers on the cloud, which can be accessed to the player through a thin-client interface to the server. This concept involves live-streaming the rendered video content of the game throughout a dedicated network requiring high bandwidth, and hence eradicates the need for powerful graphical, storage and computational resources for the gamer.

Although the concept has been introduced commercially very recently, the current cloud infrastructure provides numerous advantages for gamers. Players need not install the game on their machines at all, since they are completely hosted on the cloud servers at the datacenters. Regular backups of saved game data and the game itself is not needed, since the cloud servers provide good data redundancy and backup solutions. Game developers can now focus on building and enhancing the graphics without really giving too much attention on the limitations posed by each gamer’s machines, since the game is processed in the cloud. 

![Principle of Cloud Gaming](/ReadMe_Images/Principles_of_Cloud_Gaming.PNG)

Additionally, through signed service-level agreements (SLAs), the gamers can access the latest game releases without shelling out a lot of cash through subscription-based plans provided by cloud-service providers. The ongoing problem of game-piracy can be avoided to great extent, as the main-game content is accessible to the game developers and authorized personnel only. As long they have internet connection, any thin clients (mobile phones, PCs, laptops, etc.) can access the game on-the-fly. 

The project aims to deploy the final release of the adaptive video-game developed on an existing cloud platform so as to provide most of the aforementioned benefits of cloud gaming to its potential gamers. 

## Architecture and Model of the Proposed System
Video games are similar to software applications, except for the fact that they are specially catered for entertainment purposes. Each gaming-session consists of gaming-rounds, each of which vary in count as per the number of successful mission-completions. Depending on the difficulty-level set by the game, each gaming-round would be assigned a mission to eliminate a designated number of enemies for that difficulty-level. During the game, the player can collect 3-pickups:
- Health Pickups: Increases the gamer's health by a small amount [May be available upon eliminating an enemy]
- Turret-Hack Pickups: Shifts the target of the turrets from the player to its enemies for a short span of time [Can be located by viewing a stream of sparks projected by them to the sky]
- Machine-Gun Pickups: Equips the user with 4-rounds of a low reload-time fast machine gun [Can be located by observing the direction of the tip of a lying machine-gun prop] 

A generic class-diagram for any game character in the game can be viewed as:

![Class Diagram](/ReadMe_Images/Class_Diagram.PNG)

The video-game, in itself, consists of a complex number of loosely coupled components, all of which contribute specifically to a particulat type of functionality of the game project. A comprehensive view of the system architecture of the project is illustrated below:

![Project Architecture](/ReadMe_Images/Project_Architecture.PNG)

The video game will require a pool of resources for its development. At the most basic level, the game will compose of a number of game objects called models. Models are a collection of points whose surfaces are textured to represent the actual characters in the game. Sprites, on the other hand, are series of interrelated images of an object (playable or non-playable) which when rendered produce the animation of the specific game characters. Code snippets are pieces of programmed information, which may be used to organize the levels and sequence of a game. Music consists of all of the audio files in the game that are used to create sound effects (for example, sound of the gun trigger, chirping effects of the birds, enemy’s growl effect, etc.).The Artificial Intelligence (AI) Engine is the game component that powers all of the non-playable characters (NPCs) and give them life in the game. In addition to the game bots, the set of rules and AI algorithms, such as those for pathfinding, are embedded in the AI Engine. The Machine Learning (ML) Classifier is responsible for adjusting various parameters and values of the game bots to adapt their behaviors dynamically according to the gamer. The interactions between the AI Engine and the ML Classifier together make the Automatic Game Difficulty Adjuster, which controls the difficulty level of the video game.

Unlike in the traditional game-playing scenario, the video game is originally intended to reside entirely in the cloud’s data centers. The thin-client, which would be running on any operating system, would just require the installation of a remote-client software, such as a VNC client. When the thin-client gamer connects to the cloud via the Internet, a data center creates a virtual instance consisting of a CPU and GPU through resources allocation procedures. The data center, along with its virtual instances, provides all of the graphical and computing resources for the gaming environment. The clusters containing all of these data centers combined form the cloud infrastructure, and can together provide the game with an extensive reach to a global audience. 

Fortunately, most of the Models and Music for the video-game are made available off-the-shelf for educational purposes thanks to the vibrant and supportive community (acknowledged below). Moreovoer, the 3D-pathfinding problem was solved using Unity's A* search implementation of NavMeshAgents. 

![AI ML-Classifier Interaction](/ReadMe_Images/AI_ML_Component_Interaction.PNG)

For a clearer picture for DDA implementation, the above diagram highlights the intermediate log file, stored as an .arff file format, which stores the previous statistics of the player. The ML Classifier refers the game data tuple saved each round and predicts the new level. The AI Engine changes the difficulty of the agents using Difficulty Level Controller.

For developing the Recurrent Neural Network model, a gaming-statistics dataset comprising of 150 instances and 32 features (gaming-statistical attributes) were garnered from a diverse group of people with varying FPS gaming experience. During the data-preprocessing phase, the nominal data was converted into binary data. All of the data is then normalized to the range [-1,1], so as to improve the performance of the network. 

![Neural Network Model](/ReadMe_Images/ANN_Model.PNG)

Several models were developed and evaluated in the process with the help of feature-engineering was performed to ensure the selection of promising attributes. It was found that the most accurate model that can be derived finally consisted of only 5 (1 of which was a composite set of 5 asymmetric attributes) out of the 32 recorded game-statistics attributes. A 10-fold cross validation was used for the evaluation of the ANN model, which required splitting the dataset randomly into bins of equal size. The accuracy was recorded to be about 80%. The determination of model accuracy on unknown-data was difficult to be studied, due to the large uncertainity revolving around the application and enormous subjectivity of the data collected from varying-experienced gamers playing the game. However, during normal game-testing sessions, it was found that the Recurrent Neural Network was able to perform very well for intermediate-hardcore range of gamers. Furthermore, a test-dataset, created by a random sample of 10 instances from a group of random gamers was recorded. It shows that the model may overestimate the new-difficulty level of the game. It is highly likely for the model to perform even better if it were trained with more data.           

![Small Results Graph](/ReadMe_Images/Test_Results.PNG)

The machine-learning based video-game was hosted on an Amazon EC2 t2.micro instance available in the Singapore region. Due to absence of a good bandwidth and dedicated GPU, the video-game did noticeably lag, however it could be accessed through different computers thereby increasing reachability. It was possible to stream the game seamlessly on the purchase of strong and powerful instances such as g2 instances.    

## Quick Screenshots
1. Initial Game-Scene Development
![Screenshot 1](/ReadMe_Images/Screenshot_1.PNG)

2. Pre-Model-Training Phase
![Screenshot 2](/ReadMe_Images/Screenshot_2.PNG)

3. Pre-Model-Testing Phase
![Screenshot 3](/ReadMe_Images/Screenshot_3.PNG)

4. Game Production-Ready Stage
![Screenshot 4](/ReadMe_Images/Screenshot_4.PNG)

## Future Works
- Controlling DDA using Neural Networks outputs to adjust numerous other gaming-parameters dynamically, such as the speed of the enemies, manipulation in the number of pickups, etc.
- Game Optimization using object pooling and improving particle effects
- Additional weapon inventory with better player-weapon integration and animations
- Better Neural Network Model trained on big datasets coupled with overfitting-reducing techniques
- Better utilization of AWS instances such as g2 instances for complete cloud-gaming experience 

## Acknowledgement
- The Youtuber ' [Brackeys](https://goo.gl/qZoNdV) ' for his tutorial videos on learning the Unity Game-Engine, along with his resourceful website ' [DevAssets.com](http://devassets.com/) ' for providing 3D model assets for free-use. His unique way of teaching has enabled me to understand the fundamentals of 3D game-development well, and I highly recommend this resource for learning professional game-design and development.     
- The Youtuber '[Antti Martikainen Music](https://goo.gl/Eiv8N4) ' for his amazing gameplay music, ' [The Chase](https://www.youtube.com/watch?v=dpv8qTYyrsw) '. I highly recommend checking out his music albums on his [Website](http://anttimartikainen.com/) . Each of his compositions fits perfectly for an 'epic-music' genre game track.

## References
### Journal:
[1]     	C. H. Tan et al., “Dynamic game difficulty scaling using adaptive behavior-based AI,” IEEE Transactions on Computational Intelligence and AI in Games, vol. 3, no. 4, pp. 289–301, 2011

[2]      	P. Massoudi and A. H. Fassihi, “Achieving Dynamic AI Difficulty by Using Reinforcement Learning and Fuzzy Logic Skill Metering”, Games Innovation Conf. (IGIC), 2013 IEEE Int., pp. 163-168

[3]	J. Wang and Y. Tseng, “Dynamic Difficulty Adjustment by Fuzzy Rules Using in a Neural Network Controlled Game”, Natural Computation (ICNC), 2013 9th Int. Conf., pp. 277–281, 2013

[4]	D. Wheat, M. Masek, C. P. Lam, and P. Hingston, “Dynamic Difficulty Adjustment in 2D Platformers through Agent-Based Procedural Level Generation,” Proc. - 2015 IEEE Int. Conf. Syst. Man, Cybern. SMC 2015, pp. 2778–2785, 2016

[5]     	W. Xia, “Game Balancing with Ecosystem Mechanism”,  Data Mining and Adv. Comp. (SAPIENCE), Int. Conf., pp. 317-324, 2016

[6]	W. Huang et al., “Verifying Adaptation of Neuro-controlled Game Opponent by Cross Validation under Supervised and Unsupervised Player Modeling,” pp. 172–177.

[7]	S. He et al., “To Create Adaptive Game Opponent by Using UCT,” CIMCA 2008, IAWTIC 2008, and ISE 2008, Topp. 67–70, 2008.

[8]	Y. LeCun, Y. Bengio, and G. Hinton, “Deep learning,” Nature, vol. 521, no. 7553, pp. 436–444, 2015.

[9]	B. Mariano and S. G. M. Koo, “Is cloud gaming the future of the gaming industry?,” Int. Conf. Ubiquitous Futur. Networks, ICUFN, vol. 2015–August, pp. 969–972, 2015.

[10]	W. Cai et al., “A Survey on Cloud Gaming: Future of Computer Games,” IEEE Access, vol. 4, no. c, pp. 7605–7620, 2016.

[11]	W. Cai, M. Chen, and V. C. M. Leung, “Toward gaming as a service,” IEEE Internet Comput., vol. 18, no. 3, pp. 12–18, 2014.

[12]	J. Reeder, R. Miguez, J. Sparks, M. Georgiopoulos, and G. Anagnostopoulos, “Interactively Evolved Modular Neural Networks for Game Agent Control,” 2008.

[13]	W. Huang et al., “Verifying Adaptation of Neuro-controlled Game Opponent by Cross Validation under Supervised and Unsupervised Player Modeling,” pp. 172–177.

[14]	N. Sato, S. Temsiririrkkul, S. Sone, and K. Ikeda, “Adaptive Fighting Game Computer Player by Switching Multiple Rule-based Controllers,” in 3rd Intl. Conf. on Applied Computing and Information Technology/2nd Intl. Conf. on Computational Science and Intelligence, ACIT-CSI 2015 pp. 52–59, 2015.

[15]	B. Soni, P. Hingston, and S. Member, “Bots trained to play like a human are more fun,” pp. 363–369, 2008.

[16]	G. Wu and J. Tao, “Design and Application of Machine Learning Algorithm Computer in Connect6 of Computer Games System,” Proc. 2016 Chinese Control Decis. Conf., no. 5, pp. 4279–4282, 2016.

[17]	M. R. F. Mendonc and R. F. Neto, “Simulating Human Behavior in Fighting Games using Reinforcement Learning and Artificial Neural Networks,” 2015 14th Brazilian Symp. Comput. Games Digit. Entertain., no. i, 2015.

[18]	M. S. Emigh, E. G. Kriminger, A. Brockmeier, J. C. Principe, and P. M. Pardalos, “Reinforcement Learning in Video Games using Nearest Neighbor Interpolation and Metric Learning,” IEEE Trans. Comput. Intell. AI Games, vol. PP, no. 99, pp. 1–1, 2014.

[19]	K. O. Stanley, B. D. Bryant, S. Member, and R. Miikkulainen, “Real-Time Neuroevolution in the NERO Video Game,” vol. 9, no. 6, pp. 653–668, 2005.

[20]	D. Michael and J. Chang, “Dynamic Difficulty Adjustment in Computer Games,” Proc. Interact. Multimed. Conf., pp. 1--6, 2013.

[21]	R. Hunicke and V. Chapman, “AI for dynamic difficulty adjustment in games,” Challenges Game Artif. Intell. AAAI, pp. 91–96, 2004.

### Book:
[1]	S.Russell and P. Norvig, “Artificial Intelligence: A Modern Approach “, 2nd ed., 
India, Pearson Education

[2]	S.N. Sivanandam and S.N.Deepa“Principles of Soft Computing”, 2nd ed.

### Web Links:
[1]	Autodesk Incorporated, “Maya Documentation.” [Online]. Available: https://knowledge.autodesk.com/support/maya/getting-started/caas/simplecontent/content/maya-documentation.html.

[2]	A. S. Incorporated, “Photoshop User Guide.” [Online]. Available: https://helpx.adobe.com/photoshop/user-guide.html.

[3]	T. A. Team, “Audacity 2.1.2 Manual.” [Online]. Available: http://manual.audacityteam.org/.

[4]	U. Technologies, “Unity User Manual (5.5).” [Online]. Available: https://docs.unity3d.com/Manual/index.html.

[5]	U. Technologies, “Unity Asset Store.” [Online]. Available: https://www.assetstore.unity3d.com/en/#!/.

[6]	Wikipedia, “Deep Learning.” [Online]. Available: https://en.wikipedia.org/wiki/Deep_learning.

[7]      Wikpedia, “Cloud Gaming.” [Online]. Available: 
           https://en.wikipedia.org/wiki/Cloud_gaming.

## @the.desert.eagle
