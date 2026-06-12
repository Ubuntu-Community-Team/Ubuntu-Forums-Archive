---
title: "Problem with Video Performance"
date: 2007-03-26
forum: Desktop Environments
---

### Post by AlexKarm on 2007-03-26
Hello,

I have been playing around with Ubuntu for the better part of this month, and although I have tuned out most of the issues, there is still one or two items remaining that are causing me grief. (See [http://www.ubuntuforums.org/showthread.php?t=393329](http://www.ubuntuforums.org/showthread.php?t=393329))

Anyway, today's issue is with the performance of, well, screensavers. Sounds odd, but bare in mind that it's a reflection of the 3D acceleration.

Basically, when I launch a screensaver that uses anything 3D (such as AntSpotlight, or GLBlur) I get about 2 frames per second, at best (dropping down to some fraction at times). This video card (despite what I know people are going to say about it's age) is capable of running SupremeCommander at 20 FPS, and World of Warcraft at 40 FPS stable, so a screensaver doesn't seem like that much to ask :P

Here's the relevant information:
Card:   Radeon 9600
Driver: ATI Binary X.Org driver [fglrx] (grumble grumble, I would prefer OSS if it supported OpenGL or Hardware Acceleration) 
Vanilla Ubuntu (GNOME)
Modified xorg.conf to use Big-Desktop

If you need to know anything else, ask away.

---

### Post by UserAlphaP on 2007-03-26
I'm having a similar problem with a 9800... Anyone out there have any idea's? It would be greatly appreciated...

---

### Post by AlexKarm on 2007-03-27
I just ran glxgears, and the results were interesting. It ran for about a full second or two perfectly. Then, after that, it started slowing down and the FPS droped to somewhere between 2 and .5...

Appearently this is a rather popular problem. Anyone able to help point us in the right direction?

---

### Post by nat95 on 2007-03-29
It's likely because you don't have your respective Video card's drivers up to date on Ubuntu.

I had the same thing happening to me, with the gears playing wonderful for a second, then going to crap after about 2 or 3 seconds.  I updated my nvidia drivers, and viola!  Problem solved.  Now, every time I start up ubuntu, before I log in; an Nvidia Logo comes up.  After that, I haven't had any more issues. 

Look up how to install drivers for your card.

---

### Post by ambien on 2007-04-02
I have had the same problems with my screen saver. I just got my driver issues resolved, so if the driver is the issue, good luck on getting it solved anytime soon because if that was the problem mine would be working.

---

