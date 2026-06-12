---
title: "Google Earth, OpenGL, mga Matrox broken Urgent"
date: 2006-09-29
forum: Desktop Environments
---

### Post by leemckusic on 2006-09-29
Sorry but I am getting frantic. I need google earth running to add it to an invasive plant mapping software program. 

After Upgrading from 5.05 Breezy Badger to 6.01 LTS, Google Earth fails with 

"OpenGL mode not supported". 
This should be a video card not running Open GL right?

I have a Matrox G400 card using the "mga" video driver.

I am holding the xserver-org package at the "10." revision because the "10.4" still crashes the X window. I think I have this one installed:

/var/cache/apt/archives/xserver-xorg-core_1%3a1.0.2-0ubuntu10_i386.deb

Running sudo dpkg-reconfigure xserver-xorg and choosing the vesa driver results in no X window for me. Display stops just like the 10.4 xserver stops.

I can't find any error messages that suggest the mga driver is broken or not loading,

I don't know any test to figure out if OpenGL actually works for me.

So far, a whole raft of upgrade screwups have cleared up with simple fixes. But I am stumped on this one. Suggestion please?

---

### Post by jpkotta on 2006-10-01
I would imagine that you need to get a different driver.  Don't take my word for it, but I've only heard of certain ATI cards having open source drivers with 3D support.  Most X drivers are just 2D.  Again, I'm not sure about this at all.

The beauty of OpenGL is that you can always have a software fallback.  On Linux, this is Mesa; just search for "mesa" in Synaptic.  But software OpenGL is slow as molasses in January.

You can check for OpenGL with glxgears and glxinfo commands.

---

### Post by Jasper84 on 2006-10-16
I had a matrox G400 card too, i got hardware acceleration going by changing /etc/X11/xorg.conf. The problem was that it only works for 16bit, and the default setting is 24bit.
You can do this either by editing the file yourself or by using mgapdesk. ( sudo aptitude install mgapdesk, and then run with mgapdesk ) Make a backup of the mentioned .conf file and click the thing left to the "round-going arrows", you should find the option there. You can test wether it works by seeing if glxgears runs properly. ( glxgears -printfps for fps, another test is the Chromium game that will run smoothly with hw accel )

Basicly you have to change in xorg.conf Section "Screen"  DefaultDepth from 24 to 16. (but prolly better to use mgapdesk)
Here is an earlier post on the same topic/problem: [http://www.ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=1566291](http://www.ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=1566291)

---

