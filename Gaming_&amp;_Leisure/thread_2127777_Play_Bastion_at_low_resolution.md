---
title: "Play Bastion at low resolution"
date: 2013-03-21
forum: Gaming &amp; Leisure
---

### Post by supergreatawesome on 2013-03-21
Hey guys, 
I recently bought Bastion on Steam for Linux and it runs terribly on my laptop at 1280x800(16:10) resolution but is much more playable at 800x600(4:3) resolution. I do this by changing my screen resolution for the whole system and then running the game. This is kind of annoying because I have to switch back after I'm done. Is there any way where I can make the resolution change automatically when I play the game? Like in Windows you have "Run in 640x480" in properties and stuff. Just wondering.. 
Any and all help is appreciated :)

---

### Post by Perfect Storm on 2013-03-21
From Bastion READMe.txt file;

> The game stores it's configuration and other save game files in the ~/.SupergiantGames/Bastion
folder located in your home folder. **These files are not-editable outside of the game**, but you
back them up.  **Resolution settings are stored in the profiles.**

---

### Post by supergreatawesome on 2013-03-21
I can't find the folder you're telling me about :(
Another thing is that I'm looking not to change the resolution of the game, but the resolution of my computer when I start the game, and have it return to normal when I exit it.

---

### Post by Perfect Storm on 2013-03-21
Then you may want to look at this: [http://www.vxbus.com/software/linux/148-how-to-change-monitor-resolution-in-ubuntu-1204.html](http://www.vxbus.com/software/linux/148-how-to-change-monitor-resolution-in-ubuntu-1204.html)
and then build a script afterwards.

A script contains a number of commands you want to execute, example of a script I use to tweak & run ET: Quake Wars
```
#!/bin/bash
OLD_CONSOLE_KEYMAP=`xmodmap -pke|grep "51"|cut -d "=" -f 2`
xmodmap -e "keycode 51 = quoteleft asciitilde"

sh -c "cd /games/ETQW/ && pasuspender -- ./etqw-rthread +set s_alsa_pcm plughw:0" $@

xmodmap -e "keycode 51 = ${OLD_CONSOLE_KEYMAP}"
```

---

### Post by supergreatawesome on 2013-03-21
Riiight. Okay, thanks for your help. I read through the link but I was looking for something a bit simpler.. guess it's not possible without making a script. I would, if I knew how xD 
Haha thanks anyways :)

---

### Post by Perfect Storm on 2013-03-21
If you give a go, create a file called B_launch.sh, open it with a text editor.
When you start to make a script, you'll start with **#!/bin/bash**

Next in line you want to tell the system to change resolution: **xrandr --output VGA1 --mode <X>x<Y>_<Z>.00**
Perhaps insert a pause as well before launching the game: **sleep 5**
Now to launch the game: **sh -c "cd <destination> && ./<binary file>" $@**
And then last set the resolution back: **xrandr --output VGA1 --mode <X>x<Y>_<Z>.00**

---

### Post by supergreatawesome on 2013-03-21
I tried it. It says something like "cannot find mode 800x600" and same for the reverting resolution. And also "&&" unexpected. *confused*

---

### Post by snafu006 on 2013-03-21
Can you tell me more about your computer First

---

### Post by lisati on 2013-03-21
Thread closed for staff review.

---

### Post by lisati on 2013-03-21
Thread reopened.

> **supergreatawesome said:**
>  And also "&&" unexpected. *confused*
Did you adapt the line**sh -c "cd <destination> && ./<binary file>" $@** to your game's location and file name?

---

### Post by The Big Head One on 2013-03-22
I'm having also a problem with the resolution of Bastion as well (but it's kind of different, so if you think I should create another thread, please let me know):

The game runs a little slow on my native resolution (1920x1080), so I thought about playing it on a new x server using the following command on the "Command" box of the Bastion.desktop shortcut:

```
 xinit /usr/bin/ck-launch-session /usr/local/games/Bastion/Bastion.bin.x86_64 %U $* -- :3 & nvidia-settings –load-config-only
```

The game opened in a new x server, and run faster, but i wasn't fullscreen, but only in a small square (about 1/6th of the screen) in the center of the screen. As the linux version of Bastion doesn't allow to change  resolution, specially because the config files are binary >.>, I couldn't try to see if it was a problem with the resolution :(

Do you have any solution to this problem? I'd post a screenshot to better portray the issue, but I couldn't paste my screenshot from the new x server on my default x server :/

---

