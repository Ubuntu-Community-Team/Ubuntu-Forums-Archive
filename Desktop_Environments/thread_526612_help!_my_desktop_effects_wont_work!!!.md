---
title: "help! my desktop effects wont work!!!"
date: 2007-08-15
forum: Desktop Environments
---

### Post by treyping on 2007-08-15
Ok well i went to system/prefrences/desktopeffects and lciked on engable. but a white screen pooped up for a moment and then it just went back to "do you want to enable desktop effects?"
will someone tell me whats going on here????:popcorn::guitar::confused:

---

### Post by tdrusk on 2007-08-15
click enable when it asks you.

---

### Post by elbowgeek on 2007-08-20
It sounds like exactly what I'm experiencing.  When i get the box with the Enable Effects button, I get a blank screen for a while and have to press escape to get back.  I am using the restricted drivers as the system prompted me.

Anyone with any ideas?

---

### Post by daniel of sarnia on 2007-08-20
what video card do you have, if it's an ati and you are using there restricted driver then it will not work with AIXGL.

---

### Post by elbowgeek on 2007-08-20
Thanks for responding so quickly.  I'm using an nvidia card with the restricted drivers.

Cheers

---

### Post by daniel of sarnia on 2007-08-20
Is your system patched up to date, I've had problems with fresh installs not installing that drivers properly. Try updating your system, then uninstall then reinstall that driver. Then reboot and see if that works. If not that, I'm not sure I not have NV cards on my personal system so I'm not to sure what it would be other than what I just said.

---

### Post by gogogadget on 2007-09-08
I am (or was) running ubuntu 7.07 Feisty Fawn
I am using my old 6.10 Efty for this post

I am getting a similar problem. When I start up I get a white screen
What is most perplexing is that I can still restart. I have marked on mt screen where the logout button is and the restart icon and altough I cant see anlything I can still reboot by going through the motions. So it appears that there is a full working system but a screen full of white is covering it.

So my question is how to restore the screen to normal. The only way for me to do this is to start in terminal mode. So I will need instructions to use Linux terminal.

:(

---

### Post by elbowgeek on 2007-09-08
Well, all I can say is that every time I've tried to set up either Compiz or Beryl with either an ATI or nVidia video card I've never got it to work properly, despite all the how-tos and searches on forums like this.  And I've done some pretty esoteric things to make it happen.  

Ironically, I installed Ubuntu 7.04 on a laptop with an Intel graphics chip set and it worked without having to do anything special.  So why is it so difficult with the two major video manufacturers?

Cheers

---

### Post by gogogadget on 2007-09-10
I had the same problem but my solution was quite simple. I hope this helps you.

Log in to recovery mode and when it is finished you will be at the command prompt and logged in as root.

change directory 

cd /etc/X11

create a backup of the file we are going to alter
cp xorg.conf xorg.conf.backup

use you favorite editor and edit xorg.conf
gedit xorg.conf

looking through the file you might see Load	"glx"
simply comment this line out be putting a hash (#) in 1st column of the line so it reads
#	Load	"glx"

reboot

and all should be ok

---

### Post by elbowgeek on 2007-09-10
Cool, I'll give that a go.

Cheers

---

### Post by elbowgeek on 2007-09-10
No go.  Now when I press the button to enable desktop effects it says Desktop Effects could not be enabled.  *Sigh*.  

This is rediculous; I'm using the restricted drivers and all seems well otherwise.  I'm totally confused as to whether glx is necessary or not, or why some people get their systems working and others not.  Is there some magic I'm missing?  Did I fail to sacriifice a large enough farm animal to the correct gods?  

Dang...

---

### Post by elbowgeek on 2007-09-10
Ok, from what I can tell, the default drivers for the Nvidia are actually for the 9xxx series of cards.  I don't think my card is at that level, so is this what may be causing the problem?  However all other aspects do seem to be working fine; maybe it's just the 3D rendering that gets affected on different models of cards.  

Is there a way of obtaining Nvidia drivers which *will* work on my card (I think it's a 6XXX series)?

Anybody with some insight on this issue?

Many thanks...

---

