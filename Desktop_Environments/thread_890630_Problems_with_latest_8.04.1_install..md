---
title: "Problems with latest 8.04.1 install."
date: 2008-08-15
forum: Desktop Environments
---

### Post by kelean on 2008-08-15
I have been having some very odd things happening with a new install.  The specs are;

AMD 1800xp+  768 megs of ram and a 40 gig HD.

I have been getting random freeze ups, always something different running.  I cannot pin it down to any one program.

Opera, firefox, and pidgin will suddenly shutdown.  I have started with the cli and the only error I got from that is a segmentation fault.  Sometimes after shutdown the programs will not start.  When I start with the cli I get the segmentation fault and it will not start.

I checked the hard drive with disk analizer I had a big suprize.  It said I had 74 gigs of space free on the drive.  Thats pretty good out of a 40 gig drive.

Would it be a good idea to start over and do a fresh install?

---

### Post by phidia on 2008-08-15
What video card/driver is in your system and are you using visual effects like compiz?
If you are using any visual effects you could try turning them off and see if that helps. I'm not sure why you're getting this: > checked the hard drive with disk analizer I had a big suprize. It said I had 74 gigs of space free...out of a 40 gig drive It might be a bug you could report at [launchpad]("https://launchpad.net/ubuntu").

---

### Post by kelean on 2008-08-15
I am running an older nvidia AGP graphics card.  I cannot use any visual effects as it is not supported with that graphics card.  

I will check out the other issue and see if a bug report might have been put up there.

I just checked and there has been a bug report posted.

---

### Post by phidia on 2008-08-15
> **kelean said:**
> I am running an older nvidia AGP graphics card.  I cannot use any visual effects as it is not supported with that graphics card.  

I will check out the other issue and see if a bug report might have been put up there.

I just checked and there has been a bug report posted.

You can install the nvidia-legacy driver for older cards. Search that package name in synaptic. Also check out the [Ubuntu wiki]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") on video cards.

---

### Post by pietjanjaap on 2008-08-15
On a different forum somebody had also such a problem on a website, but other people went to the site and had no problems.
He was installing flash(and other things), but he removed it, but problem was still there.

He is starting over with installing, and following a website how to install codecs etc.
On 1 of these how to site's you can find wat you have to install after installation of ubuntu.

Search forums, ubuntu howto sites etc.


[http://computertip.googlepages.com/ubuntulinux](http://computertip.googlepages.com/ubuntulinux)
[http://onlyubuntu.blogspot.com/](http://onlyubuntu.blogspot.com/)
[http://www.ubuntu-unleashed.com/](http://www.ubuntu-unleashed.com/)
[http://www.ubuntu1501.com/](http://www.ubuntu1501.com/)
[http://www.tuxmachines.org/](http://www.tuxmachines.org/)
[http://polishlinux.org/howtos/truecrypt-howto/](http://polishlinux.org/howtos/truecrypt-howto/)
[http://www.ubuntugeek.com/](http://www.ubuntugeek.com/)
[http://ubuntu-tutorials.com/](http://ubuntu-tutorials.com/)
[http://www.ubuntux.org/](http://www.ubuntux.org/)
[http://www.debuntu.org/how-to-instal...lvm-filesystem](http://www.debuntu.org/how-to-instal...lvm-filesystem)




[http://www.linuxalt.com/](http://www.linuxalt.com/)
[http://www.openinhoud.nl/zoeken](http://www.openinhoud.nl/zoeken)
[http://www.osalt.com/](http://www.osalt.com/)
[http://linuxappfinder.com/alternatives?page=1](http://linuxappfinder.com/alternatives?page=1)

the best:
[http://damen.dommel.be/Ubuntu.html](http://damen.dommel.be/Ubuntu.html)

the gimp        - very good photoshop
gfslicer        - splitter joiner
Q7z+7z          - archiver
hellanzb        - downloaden nzb van usenet
kget            - download program
Inkscape Vector Graphics Editor
Klibido         - to look in usenet groups and nzb download
dvdfab in wine  - the only thing i can't find in linux.
quickpar in wine
k3b writing/burning dvd's
gmount iso       - to mount iso file
KNetLoad Network Monitor - you network activity in a grafic

---

### Post by kelean on 2008-08-15
I am using the nvidia-legacy driver.  The problem is the card I have is not able to do the effects.  The card I have is a quattro 4 plus.  Something like that,I am not on that machine at the moment so going from my memory.

pietjanjaap, It does not matter what site I go to.  The default start page, blank page, or one that has heavy flash.  There is no rhyme or reason for it.  I can start it with blank page and it will shutdown is 30 seconds.  Then I can go to youtube and play videos for an hour and not have a problem.  It is completely random.  Also it is the only program running.  I also have the same problem with opera but it happens far less often.

---

### Post by phidia on 2008-08-15
You could try installing the epiphany browser and see if that works better-it won't have all of ff's features though.

Another thread [here]("http://ubuntuforums.org/showthread.php?t=889811") addresses this too-but there doesn't seem to be any easy answers.

---

### Post by kelean on 2008-08-15
I am running the same version of ubuntu an a machine with a lot lower specs.  I do not have the problems with firefox shutting down.  I do not think it is a memory problem.  768 megs of ram on that machine more than enough.  I use to do all of those things with half the memory.  Granted it was slower, but it did shutdown without notice.  It would freeze up from time to time but I get that with firefox no matter what distro or machine I am using.

---

### Post by kelean on 2008-08-17
The latest problem with fierefox is that when I go to sites with flash on them.  I get a popup that says I need to install new plugins.  I click okay then it comes blank with a button at the bottom that says to continue.  I click of it and it says plugin not installed and then desaperes.  Go figure, now I just open it up and wait to see how lone before it dies.

---

### Post by ajgreeny on 2008-08-17
I think your Disk Analyser size problem may be due to the gvfs file system making the total appear to be twice what you really have.  If I remember correctly, system monitor also shows this unless you chose to not show the gvfs file system.  I'm messing about on a live CD system at the moment so can't check this myself, but I have read of the problem before and it is just a silly apparent anomaly in the file system detection.

---

### Post by kelean on 2008-08-17
File system monitor showes it correctly.  The disk anilizer is a but abd a bug report have been issued.

---

