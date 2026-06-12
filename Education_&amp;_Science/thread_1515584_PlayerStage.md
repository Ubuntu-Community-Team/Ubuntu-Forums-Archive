---
title: "Player/Stage"
date: 2010-06-22
forum: Education &amp; Science
---

### Post by vamc on 2010-06-22
Hi,

Just installed player/stage from the Ubuntu Repositories (I am using 10.04). After installation, in order to test it, in the terminal, I navigated to /usr/share/stage/worlds folder and executed the command:
                   ***robot-player simple.cfg***

Then I got an output window as shown in the screenshot. But my problem is: I referred "How to use Player/Stage" by Jennifer Owen. In it is written that the robot in the output window of simple.cfg starts moving as soon as it is opened. In my case it isn't moving. I don't know the reason. Can anyone sort out? Am I missing any dependencies? I only installed the dependencies which were prompted by the Synaptic package manager when I tried to install the packages "robot-player" and "stage".


Thanks in advance.

---

### Post by haroldsoh on 2010-07-13
Hi there. If you're getting the window with no errors, I doubt it's a dependency issue. 

How does your simple.world look like? Is the ctrl "wander" parameter in the pioneer2dx block commented out by any chance?

---

### Post by vamc on 2010-07-15
Hi, Haroldsoh. Thanks for your help. I am a newbie to this of software and so I am unable to figure it out. But in the file simple.world, I could not find any "wander" parameter in the pioneer2dx block. The block goes like this: 

```
# create a robot
pioneer2dx
(
  name "robot1"
  color "red"
  pose [-6.5 -6.5 45]
  sick_laser( samples 361 laser_sample_skip 4 )
)
```

P.S Suggest me a good book to start working with this software.

---

### Post by yarox on 2010-07-20
Hi vamc, 

Can you check which version of Player/Stage are you using? The version from the Ubuntu repos are not the ones used by Jennifer Owen's current manual (Stage 3.2.X). 

However, there's also a [link]("http://www-users.cs.york.ac.uk/~jowen/player/playerstage-tutorial-manual-2.1.pdf") from Jennifer Owen to a previous edition which uses an older version of Player/Stage (Stage 2.1.1 and 3.1.0).

EDIT: You can find current Player/Stage packages (Player 3.0.1, Stage 3.2.2) for Ubuntu Lucid [here]("https://launchpad.net/~thjc/+archive/ppa").

---

### Post by alsch on 2010-08-05
Hi all,
perhaps somebody can help me. I have just installed player/stage. I   used the fallowing description:[http://www.control.aau.dk/~tb/wiki/index.php/Installing_Player_and_Stage_in_Ubuntu]("http://www.control.aau.dk/~tb/wiki/index.php/Installing_Player_and_Stage_in_Ubuntu")

It looks like everything is okay. 
When I try "stage simple.world" it works without problems
but if I try to start "player simple.cfg" some error raises:

error   : Failed to load plugin stageplugin.
error   : libtool reports error: file not found
error   : plugin search path: /usr/local/lib:/home/alschbpk/Studienarbeit/stage/worlds:.:/usr/local/lib/
error   : failed to load plugin: stageplugin
error   : failed to parse config file simple.cfg driver blocks


I google this problem but nothing really works...

[defaut installation!]

My .bashrc:

export LD_LIBRARY_PATH=/usr/local/lib
export STAGEPATH=/usr/local/lib
export PLAYERPATH=/usr/local/lib




Sorry for my bad english...

Regards,
alsch

---

### Post by yarox on 2010-08-11
There is a block inside 'simple.cfg' that says:

```

driver
(		
  name "stage"
  plugin "stageplugin"
  provides ["6665:simulation:0"]
  worldfile "simple.world"	

)

```

If you're using an older version of Player/Stage, the line **plugin "stageplugin"** needs to be **plugin "_lib_stageplugin"**.

---

### Post by yarox on 2010-08-12
Hi,

I'm using Player 3.0.1 and Stage 3.2.2. You can find these packages for Ubuntu Lucid [here]("https://launchpad.net/~thjc/+archive/ppa?field.series_filter=lucid").

By the way, in case you were already using an older version and want to try the latest one, there is a [document]("http://www-users.cs.york.ac.uk/~jowen/player/playerstage-manual-update.html") talking about how to update the player stage files (*.cfg, *.world) to the newer syntax.

---

