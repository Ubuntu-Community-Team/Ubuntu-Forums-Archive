---
title: "Applications intermittently consume 100% cpu"
date: 2007-04-29
forum: Desktop Environments
---

### Post by shardservant on 2007-04-29
I have a Dell Inspiron 1000 configured with Ubuntu 7.04. The Inspiron has a 2.2 Celeron and 512M of memory.

Under normal circumstances, the PC runs just fine.

Intermittently Firefox and processes such as Gnome Desklets consume 100% of the CPU and essentially freeze up the system.

Has anyone run into this?

If so, any help you can provide to resolve the problem would be greatly appreciated.

Thanks,
Andy

---

### Post by ksudbury on 2007-05-01
Are you running the latest version? if not do an update and see if the problem still exists. 

I have experienced Firefox consuming 100% load but not firefox2 and irrc that was on XP.

If all else fails check the system with memtest86 for an hour and see if that brings up any errors. 


Thanks

---

### Post by mlblac02 on 2007-05-23
I just setup Kubuntu on a Dell Inspiron 1000 and had a similar problem.  At first I thought it was a problem with Ubuntu's kernel or base system as I didn't have that problem in Gentoo.  But compiling my own kernel and stripping down to only the kde-core files didn't help at all.

I'm pretty it has to do with the Xorg server's auto-detection.  I noticed that X kept crashing everytime I tried to run glxgears or glxinfo so I opened up the config and noticed that it was running with GLX and DRI enabled.  After turning both of those off, I noticed that all of my programs loaded much more quickly and that I didn't get any slowdowns in Firefox or Openoffice.  

The SiS card in the 1000's can't really do 3D well at all.  You'll need to open up xorg.conf in a text editor and comment out the GLX and DRI module lines.

---

### Post by sakthi on 2007-05-25
I also have Dell inspiron 1000. Was running FC6 few weeks back. Now with Ubuntu 7.04.

Main problem I have is when I run firefox it starts ok but whern I use it for few minutes xorg and firefox takes up too much CPU close to 90-95% and my mouse pointer just crawles and I can not do anyhting in my desktop for sometime. If I minimize firefox after sometime it comes back to normal state. What might be the problem?

Please help me

---

