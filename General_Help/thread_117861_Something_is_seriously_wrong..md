---
title: "Something is seriously wrong."
date: 2006-01-15
forum: General Help
---

### Post by Epimetheus on 2006-01-15
Ok, i recently began using ubuntu again after being away from it for a while, got back, noticed that a new version is out. So i installed breezy, thought it was going fine until i booted my computer the next day and the internet interface f*ed up, could reach outside 127.0.0.1. rebooted into windows, worked fine, back to ubuntu, not so fine. Rebooted my router, booted in ubuntu... it worked! Installed a few necessary stuff, nvidia graphics drivers, blender, ogre3d. And while trying to compile ogre i noticed i missed a library, which i couldn't find via apt-get (not so leet haxorish on that one) so i tried starting synaptic and got this error: "Failed to run /usr/sbin/synaptic as user root: Child terminated with 1 status", so i tried to reboot ubuntu and try again (yes i have used alot of windows). It didnt work, but i got up a "Could not initiate HAL" error when i got into gdm. I know HAL is important so that kind of scared me... and here i am writing this post hoping that someone can help me. :confused: I really want this to work, I want to be able to use ubuntu full time, but seriously this aint working as it should :???:

---

### Post by Mr_Grieves on 2006-01-15
First off.. why are you running as root? A regular user and sudo is more than enough.. running as root when you are not very experienced may be very dangerous, as you very easily can cause alot of problems.

Secondly, have you tried [http://www.google.com](http://www.google.com) [http://wiki.ubuntu.com](http://wiki.ubuntu.com) [http://www.ubuntuguide.org](http://www.ubuntuguide.org) and searching here in the forum?

When searching on google on your messages
> 
"Failed to run /usr/sbin/synaptic as user root: Child terminated with 1 status"


I found this among many other tips
> 
I also recently had this problem. After I debootstraped a new ubuntu installation onto an evms volume.

This problem was easily fixed by running:
visudo
and adding
{username} ALL=(ALL) ALL


> 
Can't Run Synaptic and Other Tools
mojorising
11-28-2004, 02:36 AM
When I try to run Synaptic and other tools like the login screen setup program -- basically anything requiring root access -- I get an error like, "Failed to run /usr/sbin/synaptic as user root: Child terminated with 1 status.

I have set up the root account and use this instead of sudo, which is where I think the problem stems from but I am not sure what do do about it.

Does anyone know how to fix this issue? I would greatly appreciate it!

12-01-2004, 05:29 AM
If you are trying to run Synaptic from the menu Computer->System Configuration, you must still enter your password (not root's) when you are prompted. It doesn't matter that you have set up the root account. This menu runs Synaptic with gksudo, which is the graphical version of sudo.
mojorising

12-01-2004, 07:24 AM
I do enter my password. Still does not work. If I did not, surely it would produce a different error.

I have made some progress on the issue.

Running synaptic or gdmsetup from a console produced this error: "(synaptic:5077): Gtk-WARNING **: cannot open display:"

So I googled part of that message and figured this out from picemealing advice from others on similar problems..

If I type xhost + at the command line and then su - (enter pw),
Type export DISPLAY=:0.0 as root
I can then run synaptic and gdmsetup from the console temporarily until I close that console. 


---

### Post by Epimetheus on 2006-01-16
starting synaptic as root wasnt something i choose, it just did that :S And i must have missed those when googling, sorry.

---

