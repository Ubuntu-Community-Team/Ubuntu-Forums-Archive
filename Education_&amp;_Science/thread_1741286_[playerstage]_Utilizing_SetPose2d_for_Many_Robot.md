---
title: "[player/stage] Utilizing SetPose2d for Many Robot"
date: 2011-04-27
forum: Education &amp; Science
---

### Post by abqorian on 2011-04-27
Hi all,

This thread is about SimulationProxy in Player/Stage robot simulation platform.

There is this function within class SimulationProxy called SetPose2d which [set the 2D pose of an object in the simulator, identified by the std::string.]("http://playerstage.sourceforge.net/doc/Player-2.1.0/player/classPlayerCc_1_1SimulationProxy.html")

This function is quite useful if one want to control the robot movement and position in simulation. From the documentation link above, this is how you use it:
```
SetPose2d (char *identifier, double x, double y, double a)
```

The ```
char *identifier
``` variable is filled by the name of the robot model one defined in *.cfg file.
As for my application, the cpp code looks like this:
```

1	SimulationProxy	sp(&robot,gIndex);
2	Position2dProxy		pp(&robot,gIndex);
3	x = pp.GetXPos();
4	y = pp.GetYPos();
5	o = pp.GetYaw();
6	sp.SetPose2d( (char *)string("robot1").c_str(),x,y, (o- DTOR(90)));

```

In the cfg file, I defined 4 robot models as robot1, robot2, and so on.
```

driver
(
	name "stage"
	provides ["simulation:0"]
	plugin "libstageplugin"
	worldfile "AMiR.world"
)
driver
(
	name "stage"
	provides ["map:0"]
	model "cave"
)
driver(
	name "stage"
	provides ["position2d:0" "sonar:0"]
	model "robot1"
)
....and so on for other robot model

```


Sadly, to use this function one must hard coded the name of the robot model, i.e. "robot1". And it only works for the default port (6665).
My question for the forum is there a way in Player/Stage to get the name of the robot model mentioned/defined in cfg file?
So that I don't have to hard coded the robot model's name everytime I want to repose its position. I want to make line 6 in snippet above more general, e.g. look like this
```

// an example function to get the robot's name from cfg file
string robot = getRobotName(); 
sp.SetPose2d( (char *)string(robot).c_str(),x,y, (o- DTOR(90)));

```

Thank you all for your time and attention.
Look forward to hear from you soon
Excuse my bad English :D

---

### Post by abqorian on 2011-04-28
I finally decided to use the simplest method that I actually avoid, switch-case.

```
switch (port_number){
    case 6666: robot = "robot2"; break;
    case 6667: robot = "robot3"; break;
    :
    :
    default: robotname = "robot1"; 
}
```
then I call this function
```
sp.SetPose2d( (char *)string(robot).c_str(),x,y, (o- DTOR(90)));
```
However, I found out that the SimulationProxy prevented me to run another robot with port other than 6665 (the default).
If I run this command,
```
./program -p 6666
```
an error popped out:
```
playerc error   : got NACK from request
playerc error   : failed to get response
terminate called after throwing an instance of 'PlayerCc::PlayerError'
Aborted
```

I tried to change the cfg file by adding more simulation interface:
```
driver
(
	name "stage"
	provides ["simulation:0"]
	provides ["6666:simulation:0"]
	provides ["6667:simulation:0"]
	provides ["6668:simulation:0"]
	plugin "libstageplugin"
	worldfile "AMiR.world"
)
```
But then I could not run the robot with default port 6665. Instead I was able to run robot with port 6668. 
SO, I thought I might be something related to the definition of  simulation proxy within the config file. Or I could be wrong.

Please, any help is appreciated. Thanks.

---

### Post by K_D on 2011-10-26
Hi abqorian!

I had the same problem and almost went crazy about it...

Try to seperate your .cfg file. I mean instead of this:

driver
(
	name "stage"
	provides ["simulation:0"]
	provides ["6666:simulation:0"]
	provides ["6667:simulation:0"]
	provides ["6668:simulation:0"]
	plugin "libstageplugin"
	worldfile "AMiR.world"
)

try with this:


driver
(
	name "stage"
	provides ["simulation:0"]
	provides ["6666:simulation:0"]
	plugin "libstageplugin"
	worldfile "AMiR.world"
)
driver
(
	name "stage"
	provides ["simulation:0"]
	provides ["6667:simulation:0"]
)
driver
(
	name "stage"
	provides ["simulation:0"]
	provides ["6668:simulation:0"]
)

Hope that will help you too!

KD

---

