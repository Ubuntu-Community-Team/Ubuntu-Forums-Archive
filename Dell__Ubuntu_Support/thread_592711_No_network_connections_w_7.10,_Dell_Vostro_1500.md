---
title: "No network connections w/ 7.10, Dell Vostro 1500"
date: 2007-10-26
forum: Dell  Ubuntu Support
---

### Post by tylerhardy on 2007-10-26
Hi all. I am the biggest greeny to ubuntu. I just downloaded and installed ubuntu 7.10 on my dell vostro 1500 and I am having difficulties with many issues.

My notebook is T7500, 160GB HDD, 2GB RAM, Dell 1500 wireless N-draft, and the sigmatel (or Intel HD audio, I don't know).

I installed it pretty much by stumbling until it worked (on the account I couldn't get any good and thorough install guides with dual booting with vista) and so I hope nothing has happend in the installation that would create these errors.

Issue 1.) most importantly I cannot connect to the internet via wireless nor Ethernet. Neither are listed in network settings and Dell of course doesn't have ubuntu drivers for this model.

Issue 2.) no sound, this seems to be a major issue with all vostros but due to the lack of internet I cannot update ubuntu and I've tried to follow some guides but they are not clear on their steps and keying in the terminal.

Issue 3.) I couldn't decide how I wanted the partitions on my hard drive and I hope that I had set them right:
vista - 100GB
Shared (fat32) - 5GB
Swap - 2GB
Ubuntu - 49GB

is this ok, I've had difficulties setting up the partitions in the g parted utility. but I don't have any problems with reinstalling the OS if it comes to it.

Sorry for the lengthy post, but I am too frusterated with this (I feel like I was dropped in china naked with no guide nor translator). Please help

---

### Post by dmgthe2nd on 2007-10-29
Hi there, I'm kinda of linux noob so I can only help with one thing since I experienced it also.

For Sound... follow these instructions..
Type it into your terminal:  Applications..Accessories..Terminal
>  the solution

sudo apt-get install module-assistant (useless cause you already have it if it's not the first time you do the trick)
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

from this thread..
[http://ubuntuforums.org/showthread.php?t=569082&highlight=vostro+1500+sound&page=3]("http://ubuntuforums.org/showthread.php?t=569082&highlight=vostro+1500+sound&page=3")

It might be hard to make it work without internet but hopefully you resolved that issue.

There are still bugs with this sound fix but the basics are as follows.
If you boot with headphones plugged in, your speakers won't work but the headphone jack will play sound.. and if you boot with nothing at all, they will both work at the same time :).. kinda shitty if you use the shitty laptop speakers.  And also, when you sleep or hibernate your system, the sound stops working till you reboot.

Good luck on that internet issue.

---

