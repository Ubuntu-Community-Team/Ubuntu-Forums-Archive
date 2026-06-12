---
title: "No desktop!"
date: 2006-07-07
forum: Desktop Environments
---

### Post by rmdeal on 2006-07-07
I had a Breezy Ubuntu on a partition on my PC which worked fine but I have only slow expensive connection to the internet so I used another computer on a different system to download some iso files which I converted to CDROMs.
Everything went pretty smoothly until I used "debian-edu 20r0-i386.iso" as a resource for upgrades, once I finally got it properly listed in the
sources.list file.  Then I made a serious mistake:
I started using apt-get instead of aptitude to install everything that looked interesting.  When next I booted into this system, I could not get a Ubuntu screen.  I was told that my [HOME]/.dmrc file had the wrong protection code so wouldn't work and that I should set it to 644.  Well it already was 644 so I made it 777, not knowing what it's problem was.  No joy.  It was clear that KDE was trying to become the window manager but complained about other protection codes which I upgraded to no avail.  I then decided that the KDE additions to my former Gnome desktop were the problem and began removing *kde* packages.  
Now I have NO response after the notice on the need to upgrade the .dmrc file, just a black screen with a working mouse, requiring manual computer off to restart.  

I have some gnome desktop deb package files I'd like to install but I can't get aptitude to recognize these legit. xxx.deb files as packages.
This is a very basic question I realize but I really am new to the Debian
apt packaging system and need some help.

Looking forward to your wisdom,   Ralph,  retired P.Chem. professor living
in Weimar, Germany

---

### Post by mcduck on 2006-07-07
You seem to have quite a problem there.. Using ackages from outside of Ubuntu repositories is easy way to break your system.. 

Sadly I can't help you to fix your system, but at leats I can help you with those .deb files: Even when apt-get/aptitude use those same files, they are built to insall packages from internet repositories, not from your own machine. To install .deb packages you need to use the 'sudo dpkg -i package.deb' command. (if you have any packages to install, you can insatll them all at the same time like this: 'sudo dpkg -i package1.deb package2.deb)

---

### Post by tzulberti on 2006-07-08
Another form of installing all the packages is: "sudo dpkg - i *.deb"

I am sorry, but i do not know what is happening in your home. Did you trie to create another user and login with it? (adduser command...)

---

### Post by rmdeal on 2006-07-09
Thanks for the responses.  I have indeed explored with dpkg as a way of directly opening a .deb package without stating an archive name.  Unfortunately that did not help.  I also have read more on the Gnome Desktop Manager system and various apt* commands.  Using apt-setup I was able to load packages from any cdrom which allowed me to reinstall most of gnome packages, starting with gnome-session, etc.  All of the installations, using aptitude, not apt-get, went fine, working as root in the safe mode.  However,  after restarting the system, I still get the protection code error message for .dmrc followed by a dead screen with a movable mouse, requiring manual shutdown.
I believe my problem dwells in the basic window start up programs/scripts such as xinit, Xsessions.  But where and how to fix it?

Looking forward to more replies.

      Ralph

---

### Post by ShiningHolden on 2006-07-09
Couldnt you just boot into recovery mode and edit your resportories back to default and update back to the ubuntu packages and remove all the bad packages form there?

Tell me if this would help, I will make a guide how to do it all.

---

### Post by rmdeal on 2006-07-09
Hmmm - interesting suggestion but I don't know how to "edit back to repositories".  I certainly wish I could turn the clock back to when I began using apt-get to place so many of the packages I had installed from a Debian disk, including several kde packages.  I believe the kde installs caused the problem but am not sure.

My problem is awkward in that I have a dual boot system with Suse 9.3 as the other kernel.  The Suse 9.3 has only ISDN linkage to the internet (can't get DSL in my building in Weimar, Germany because the building was wired with fiberglass) and the ISDN corporation (T-com) only offers expensive maximum time internet packages.  That means that I have to use another, faster, cheaper internet connection in a different building to download images onto CD's which I bring to my computer.  My Ubuntu system has NO internet connection (yet - ISDN is awkward to set up I've found), so I cannot download packages directly from the internet.

My current mantra:  LINUX is FUN, remember

  Thanks,  Ralph

---

### Post by rmdeal on 2006-07-09
I did not properly respond to the suggestion: "Couldnt you just boot into recovery mode and edit your resportories back to default and update back to the ubuntu packages and remove all the bad packages form there?"
I really don't understand how to "edit our repositories back to default".
Updating is what I've been doing, using aptitude, using 'aptitude update' regularly after installing a new package.  I don't know what the bad packages are, unfortunately.

One more response:  tzulberti had suggested that I try adding a new user and booting with that user.  I did try that and got the same no-response screen with mouse logo but requiring turning off the computer to restart.

---

