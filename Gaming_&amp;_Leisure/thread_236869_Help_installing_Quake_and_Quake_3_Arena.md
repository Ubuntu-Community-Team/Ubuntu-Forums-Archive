---
title: "Help installing Quake and Quake 3 Arena"
date: 2006-08-15
forum: Gaming &amp; Leisure
---

### Post by darcstarr on 2006-08-15
I've heard that the quake games will run on Ubuntu so I wanted to try it out, the only problem is I'm a noob to Ubuntu and therefore can't figure out the step by step process to getting the job done. If anyone out there could help me it would be much appreciated.

---

### Post by HAARP on 2006-08-15
Which "Quakes"? 1 and 3?

---

### Post by Gergux on 2006-08-15
If q3 this is what got me through it about 2 years ago. Alot has changed though.. Should be better documented now.. GL&HF :)

[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Quake3&back=HOWTO+INDEX+Linux+Games](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Quake3&back=HOWTO+INDEX+Linux+Games)

---

### Post by Anduu on 2006-08-16
A good place to start...

[http://www.liflg.org/?catid=6](http://www.liflg.org/?catid=6)

---

### Post by darcstarr on 2006-08-16
It is the Quake 1 and Quake 3 games for those who need to know. Thanks.

---

### Post by crane on 2006-08-17
I am not familiar with installing Q1. Q3 is really easy provided you have the CD. and you have your 3d drivers set up.

> 
First make a directory /quake3 I made mine in /usr/local/games/quake3
command:

    * sudo mkdir /usr/local/games/quake3

the make a directory called baseq3 under the quake3 directory
command

    * sudo mkdir /usr/local/games/quake3/baseq3


then put the quake3 "windows version" in cd rom anf copy a file called pak0.pk3 to the newly made baseq3 directory.

command

    * sudo cp /media/cdrom0/Qauke3/baseq3/pak0.pk3 /usr/local/games/quake3/baseq3/pak0.pk3


Now you can go to Cranework.com <--- my site, and get the .run file. (but I think you already have it right?)
if not use this command

    * wget [http://www.cranework.com/Downloads/l....32b-3.x86.run](http://www.cranework.com/Downloads/l....32b-3.x86.run)

or right click and "save as"

OK now
run that file (lets say the file is in my home directory)
command

    * sudo sh linuxq3apoint-1.32b-3.x86.run


after the install has completed just exit. (it's not a good Idea to run as root.)
now just type quake3 in your console and the game should run fine.
__________________
Crane

This can from [this threaad]("http://www.ubuntuforums.org/showthread.php?t=24015&highlight=crane+quake")

---

### Post by Josh_b on 2006-08-18
Crane: I was able to install q3 in less than 10 mins thanks to your how to, but I have a little problem.

There's no sound. When I fire up q3, in the console under the sound init part it says

> Could not open /dev/dsp

Do you know how I could fix this?

---

### Post by Lord Illidan on 2006-08-18
Try either "killall esd" or else "killall artsd"

---

### Post by Josh_b on 2006-08-21
They didn't work.
for the artsd it said no process killed.

---

### Post by slyvren on 2006-10-09
edit ~/.q3a/baseq3/q3config.cfg
find 'seta snddevice "/dev/dsp"' change the /dev/dsp to /dev/dsp1, /dev/dsp0, /dev/dsp2 or try adsp for all those instead of dsp... one of em should work.

GL HF!

---

### Post by wingman91 on 2006-10-12
i couldnt download the file that crane gives a link to. do i have to download it on a linux machine or something?

---

### Post by dmn_clown on 2006-10-13
Try this link [http://icculus.org/quake3/]("http://icculus.org/quake3/"), its loads better than vanilla q3a.  It includes the recent security update and an SDL backend and support for flares (albeit they are done poorly).

It's also the backbone for many new GPLed fps games.

---

### Post by getphuture on 2010-10-17
The original version still works well. I writed a post about that:[http://ubuntuforums.org/showthread.php?p=9986973](http://ubuntuforums.org/showthread.php?p=9986973). About the sound you have to switch to the sdl-oss solution. Works well !

---

