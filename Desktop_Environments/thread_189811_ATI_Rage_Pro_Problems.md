---
title: "ATI Rage Pro Problems"
date: 2006-06-05
forum: Desktop Environments
---

### Post by StueyB on 2006-06-05
Hi Everyone,

I have got a new dell machine with an ATI Rage 128 Pro. 

So far I have got the system installed fine. Then I installed the  686 kernel to update it.

So now i thought, its the turn of the ati card.

I followed the basic outlines for installing the restricted modules.

However trying to run it, i get the kubuntu loading screen but it doesnt move. using ctrl alt f1 the error that seems to kill it is XIO Fatal error 104.

I can get back into KDE by using dpkg-reconfigure xerserver-xorg.

I don't quite know what to do now really.  Its pointless having an accelerated card that acts like a standard svga card.

Cheers

Stu

---

### Post by Donald on 2006-06-05
What driver are you using? I think the restricted ati "fglrx" driver supports only radeon 8500
and higher cards. So for the rage 128 you should use the open-source driver "ati".

---

### Post by StueyB on 2006-06-05
Thanks for that. It could explain a few things. The ATI driver is installed at present, so im assuming its as optimised as much as its gonna get. Oh well

---

### Post by HeavyAl on 2006-06-05
Having just had issues myself with an ATI card, a couple things to do to check the status of your card:

in a term:

glxinfo | grep direct

will let you know if you are using direct rendering

glxinfo | grep render

will show you what renderer you are using (if it says Mesa Indirect you have an issue)

---

### Post by Hezekiah on 2006-06-05
Also, if you have any of the fglrx packages installed then they may be interfering with the xorg ati driver working properly.

That said, the Rage Pro 128 is not a very speedy card by modern standards, so that combined with imperfect driver support may be a large limiting factor.

---

### Post by woopud on 2006-06-14
[QUOTE=HeavyAl]Having just had issues myself with an ATI card, a couple things to do to check the status of your card:

in a term:

glxinfo | grep direct

will let you know if you are using direct rendering

glxinfo | grep render

will show you what renderer you are using (if it says Mesa Indirect you have an issue)[/QUOTE]

bert@ubuntu:~$ glxinfo | grep direct
direct rendering: Yes
bert@ubuntu:~$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI Rage 128 Pro 20041026 AGP 1x
bert@ubuntu:~$

This is my output, is this the best I can do with my video card ?

Bert

---

### Post by weijie90 on 2006-06-14
hi,
i have the same problem. 
the card works find in windoze xp.
please help us. thanks!

---

### Post by Hezekiah on 2006-06-17
Since glxinfo is saying that direct rendering is enabled, I think this is probably as good as you are going to get for now.  I do not know if there are currently any efforts to improve the performance of these cards.

---

### Post by az on 2006-06-17
That is quite an older card.  How much video ram does it have?  Also, DRI is on by default with the GPLed xorg drivers - flglx won't work.

You can probaly improve the performance of DRI by dissabling higher resolutions and color depths.  The ram is allocated to 2D graphics and what is left over goed to 3D.  By lowering the resolution and color, you give yourself more ram for DRI.

Since Ubuntu uses the maximum color depth and resolution for 2d, you may be losing out.  Try booting into recovery mode and
dpkg-reconfigure xserver-xorg

and picking 1024x768 at 16 bit for your screen.


then run

init 2
and see if 3D is better.

---

### Post by patrick295767 on 2006-06-23
[QUOTE=azz]That is quite an older card.  How much video ram does it have?  Also, DRI is on by default with the GPLed xorg drivers - flglx won't work.

You can probaly improve the performance of DRI by dissabling higher resolutions and color depths.  The ram is allocated to 2D graphics and what is left over goed to 3D.  By lowering the resolution and color, you give yourself more ram for DRI.

Since Ubuntu uses the maximum color depth and resolution for 2d, you may be losing out.  Try booting into recovery mode and
dpkg-reconfigure xserver-xorg

and picking 1024x768 at 16 bit for your screen.


then run

init 2
and see if 3D is better.[/QUOTE]
  
Thanks for help !
  
I tried this but unfortunately that cannot help glxgears
I got some improvments via : 
[http://ubuntuforums.org/showthread.php?p=1174814#post1174814](http://ubuntuforums.org/showthread.php?p=1174814#post1174814)
  
	Option "UseInternalAGPGART" "yes"
        Option "VideoOverlay" "off"
        Option "OpenGLOverlay" "off"
  
What is very weird, is that under windows XP, the gaming is really great !
my rage 128 works very well and fast. 
On contrary to windobe, that's very pitty that ubuntu is not able to handle with such ati cards :-( (it's a bit processor which was brand new long time ago) :-(
  
Greetz

---

### Post by patrick295767 on 2006-06-23
[QUOTE=woopud]bert@ubuntu:~$ glxinfo | grep direct
direct rendering: Yes
bert@ubuntu:~$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI Rage 128 Pro 20041026 AGP 1x
bert@ubuntu:~$

This is my output, is this the best I can do with my video card ?

Bert[/QUOTE]
  
Please coudl you post ur /etc/X11/xorg.conf ?  and /etc/modules ?
  
thanks

---

