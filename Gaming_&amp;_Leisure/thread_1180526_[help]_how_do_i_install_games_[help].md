---
title: "[help] how do i install games? [help]"
date: 2009-06-06
forum: Gaming &amp; Leisure
---

### Post by Kaaku on 2009-06-06
[CENTER][SIZE=1]**_[IMG]http://www.cs2d.com/img/os_linux.gif[/IMG]_**[/SIZE][SIZE=1]**_[IMG]http://www.cs2d.com/img/os_linux.gif[/IMG]_**[/SIZE]
[/CENTER]

Ok so I know how to get games off of "synaptic" But! when it comes to downloading [SIZE=1]**_"Counter-Strike 2D for [IMG]http://www.cs2d.com/img/os_linux.gif[/IMG] Linux"  _**I cant do it! OK heres exactly what i do..

(I have never used Linux) Also I am running on Ubuntu the newest version!

1. I go to the game I want to download.. as in this example it is "[/SIZE][SIZE=1]**_Counter-Strike 2D for [IMG]http://www.cs2d.com/img/os_linux.gif[/IMG] Linux"  _**So now.. I go to download select the LINUX download then it downloads no problem...

2. I select the file I downloaded.. I click on it and there are 2 files... (a Read ME File) and "CounterStrike2D" witch is the game! When I double click on it a box pops up like this..
[IMG]http://i41.tinypic.com/11ta04g.png[/IMG]

So i dont know if i need to get something from [/SIZE]"synaptic" or what to be able to read these files..

REMEMBER: I have never used Linux!
Please help![SIZE=1][B][U][IMG]http://www.cs2d.com/img/os_linux.gif[/IMG]


[/U][/B][/SIZE][CENTER][SIZE=1]**_[IMG]http://www.cs2d.com/img/os_linux.gif[/IMG]_**[/SIZE][SIZE=1]**_[IMG]http://www.cs2d.com/img/os_linux.gif[/IMG]_**[/SIZE][/CENTER]

---

### Post by Grishka on 2009-06-06
change it to executable in file preferences menu.

---

### Post by Kaaku on 2009-06-06
> **Grishka said:**
> change it to executable in file preferences menu.
Please explain.. Like I said  I dont know anything with linux... I have Never been on one...

Please Tell me step by step... Im very confused..

---

### Post by Kaaku on 2009-06-07
Bump!


Please help!!

---

### Post by regor210 on 2009-06-07
I have never played &#65279;Counter-Strike. But heres an easy way it can be installed. Go to PlayOnLinux and install  PlayOnLinux. this is a Wine installer. 

[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

After PlayOnLinux is installed you will find it under games in Ubuntu.

start it and goto >Install>Games>Steam
then install Steam:&#65279;Counter-Strike

Hope this gets you going.

---

### Post by Bölvaður on 2009-06-07
> **regor210 said:**
> I have never played &#65279;Counter-Strike...[loads of dribble]

counterstrike **2D** is for linux.

taken from the readme file> 

- Please extract/unzip the zip file before playing 
- Run CounterStrike2D or Launcher to start the game 
- Visit [www.CS2D.com/faq.php](www.CS2D.com/faq.php) if you have any problems

So you right click the archive file (.zip) and select extract
Then find a file called CounterStrike2D and double click it (if it doesnt work right click and find Permissions and mark it to be allowed to be executed).

---

### Post by regor210 on 2009-06-07
Thanks for the Info  &#65279;Bölvaður. I tried &#65279;counterstrike 2D for linux.

But could not get it to start.


regor210-desktop:~$ cd ~/Desktop/cs/cs2d_0114_linux
rerog210-desktop:~/Desktop/cs/cs2d_0114_linux$ ./CounterStrike2D
Error: Failed to load image
gfx/player/t1.bmp
Please re-install CS2D

I don't think CS2D likes my AMD 64 x2.  But the Windows version worked using Wine.

---

### Post by LinuxFox on 2009-06-07
> **Kaaku said:**
> Please explain.. Like I said  I dont know anything with linux... I have Never been on one...

Please Tell me step by step... Im very confused..I never tried Counter-Strike 2D on Linux myself, but I'll be glad to help you change it to an executable step by step.

1. Right-click the file you're opening for a menu.
2. Choose "Properties".
3. Click the "Permissions" tab.
4. Click the check box that says "Allow executing file as program"
5. Click close and try opening it.

Edit: I tried downloading the game myself and changing to executable helps, but it crashes on me.  When I tried running it from the Terminal, I got the same message as regor210.

---

