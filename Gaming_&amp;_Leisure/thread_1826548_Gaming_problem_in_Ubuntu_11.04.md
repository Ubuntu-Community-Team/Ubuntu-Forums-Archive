---
title: "Gaming problem in Ubuntu 11.04"
date: 2011-08-16
forum: Gaming &amp; Leisure
---

### Post by RippleEffects on 2011-08-16
I have problems with Ubuntu when it comes to gaming. I download games daily and play them and I seem to have some problems with some games I download such as... Assault Cube, warsaw, nexuiz, alien arena, teeworlds, ect.. Every single time when I download these games the screen freezes and gets stuck and I can't move my mouse and I hear a repeat of the same noises coming out of my speakers. I know this is not normal computer behavior. How can i fix this problem? I really wanna play these games PLEASE MESSAGE!!!!

---

### Post by RippleEffects on 2011-08-16
Bump!

---

### Post by jerryjustly on 2011-08-16
Similar Problem:
I'm not sure if these are wine games you are talking about or not, but I started having a problem with wine games on Ubuntu 11.04.  I would try to start a wine game and it would freeze up, I would reboot, and go through the hole thing again and again and again.

My Solution:
I finally booted up and started a wine game and just went and watched tv to distract myself while waiting a ridiculously long time.  Finally I think it was about an hour later, I checked it and a box popped up that said, wine had been configured.  I haven't had anymore freeze ups with it since.  (In other words you might want to try waiting a ridiculously long time, for wine to configure itself for the first time.)

----------------------
[http://www.dotdeb.com](http://www.dotdeb.com) is a great place to find deb packages.

---

### Post by RippleEffects on 2011-08-16
These are not wine games though these are Linux, windows, windows 7, and vista games I am talking about. So any more suggestions??? can anyone give me some way to fix this problem AND AGAIN THESE GAMES CAN RUN WITHOUT WINE. thanks for suggestion though. I might use it in the future.

---

### Post by RippleEffects on 2011-08-16
bump....

---

### Post by RippleEffects on 2011-08-16
Come on cant anyone help???

---

### Post by RippleEffects on 2011-08-17
How can I solve this problem? every time I open a game the next minute or two it freezes my computer. worst of all I am not running wine games, I am running Linux games such as teeworlds, nexuiz, alien arena, ect... HOW CAN I FIX THIS PROBLEM!?!? 

P.s. I am running Ubuntu 11.04(natty).

---

### Post by akand074 on 2011-08-17
Perhaps try giving a bit more information. What is the specifications of your computer. Do you have your proprietary drivers installed? NVidia/ATI card? Do you have desktop effects running (are you in Unity? on gnome panels?). It'll be easier to help or find the issue with some of that knowledge. There's no way anyone can work out what's wrong with just "I open up a game and everything freezes".

---

### Post by RippleEffects on 2011-08-17
Okay lets see...

_[SIZE=4]Ubuntu[/SIZE]_

Ubuntu 11.04 (natty)
Kernel Linux 2.6.38-10-generic
GNOME 2.32.1

_[SIZE=4]Hardware[/SIZE]_

Memory: 512 MiB
Processor: Intel(R) Pentium(R) 4 CPU 2.80Ghz


The weird thing is when I went to System> Administration> System Monitor It did not show my graphics driver how do i find that out???

---

### Post by akand074 on 2011-08-17
Try running this command in a terminal (Accessories > Terminal)

```
lspci | grep VGA
```and paste the content here. Also were those games ever working in the past? When were they working if so? (i.e were they working in Ubuntu 11.04 before? or in prior versions of Ubuntu). If it's worked in Ubuntu 11.04 in the past, do you know anything you might have done since the last time it worked?

Your computer does seem rather weak. It could be the possibility that it just can't run those games, especially if you only have an integrated graphics card (probably possible with a decent dedicated card). So anyways posting that information would be helpful.

---

### Post by RippleEffects on 2011-08-17
It says 01:00.0 VGA compatible controller: nVidia Corporation NV18GL [Quadro NVS 280 SD] (rev a2)

---

### Post by akand074 on 2011-08-17
Okay so you do have a dedicated graphics card, though it's very old and very weak. Try opening up additional drivers (System > Administration > Additional Drivers) and see if it comes up with any results. NVidia website seems to have completely wiped it off it's site. If it doesn't come up with anything then all you have is the drivers already provided. 

You also haven't answered the question as to whether you've been able to play the games in the past on that computer? If you don't have any drivers available then chances are you just don't have the resources. I think Ubuntu might be a bit much for you computer. I'd recommend trying [Lubuntu]("http://lubuntu.net/") which is Ubuntu with LXDE interface (very light, uses less resources). If you want to use even less resources, [Puppy linux]("http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm") is super light and might help you play games so that more resources would be available for the game and not used by the OS. I'm not sure how well you can get them to run though.

Anyways let me know if you've ever been able to play the games and if you find any drivers available using the Additional Drivers application.

---

### Post by RippleEffects on 2011-08-17
I wasn't really able to play games before this is sorta new to me Ill try to see puppy Linux... By the way how can i install this in my Ubuntu???

---

### Post by akand074 on 2011-08-17
Puppy Linux is an entire OS (instead of Ubuntu). You should wait a few hours before bumping.

---

### Post by overdrank on 2011-08-17
Please do not create multiple threads on the same issue. Threads merged.
Also please do not bump so quickly, once a day ( 24 hr ) is polite. :)

---

### Post by Fir3chi3f on 2011-08-18
I was thinking that the symptoms actually sounded like an overheating problem. It was on my laptop that I had a similar issue, everytime I did anything taxing, like minecraft, it would crash and this happened under Ubuntu as well as windows. After learning my warranty was up, I open it up and found a nice thin dust barrier on the heatsink between the fan. While I assume that this is a desktop from the graphics card, it could be possible dust or a bad fan is the trouble. 

Good luck mate keep us posted!

---

