---
title: "Installing Xubuntu 9.10 on a Dell C400"
date: 2010-01-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by RedShifted on 2010-01-03
*** UPDATED 4 Jan 2010 ...

Please bear with me as I am a really green Linux, let alone Ubuntu user.  I have a Dell Latitude C400 with a 20 GB hard disk, 750MB of memory and the 1GHz Pentium III Mobile processor.  I really like the machine because of its size and weight and I would like to use it as a development platform.  I have 'toyed' with other Linux variants and find Ubuntu the most comfortable to use, hence I want to install Ubuntu on it.  Everything I read on the Ubuntu website and in the various forums points to doing an installation of Xubuntu 9.10 using the alternate version.

The screen during installation seems to be flawed in that the text installer is activated.  A blue-grey screen presents itself and it seems to flicker.  The installation finishes and reboots.  A white mouse appears clearly on the screen but then when the login page is presented, the page flickers very quickly and is washed out.  It gives the impression the image cannot be synchronised.  

I have tried 8.10, 9.04 in different flavours of Ubuntu and Xubuntu, live CD and alternate version, automatically partitioned and manualy partitioned.  None seem to work for me.  

Has anyone tried installing Xubuntu 9.10?  
Is there an older version that works better? 
Is it possible that the hard disk is too small?
Should I have an active internet connection during installation? (I am asking this because some of the installations 'complain' about not being able to find a DHCP server.)

From all the posts I have read, I can only conclude that a Dell C400 is not a very good machine to install Ubuntu on.  Is this a reality I should face?  Hope someone can point me in the right direction.

UPDATE:  This morning, I tried re-installing with a connection to a router connected to the Internet and I realised I omitted a detail.  During the text installation, the screen is blue and had black/dark grey tildes, '~', across it, on what seemed to be every line.  This is despite when it starts with a good white text on black screen.  It would seem the video chipset is not being detected properly.  I have not been able to figure out how to specify the chipset during installation.  Maybe someone could make a suggestion on how to do this.

Thank-you for your help!

---

### Post by bobcollard on 2010-01-07
> **RedShifted said:**
> *** UPDATED 4 Jan 2010 ...

Please bear with me as I am a really green Linux, let alone Ubuntu user.  I have a Dell Latitude C400 with a 20 GB hard disk, 750MB of memory and the 1GHz Pentium III Mobile processor.  I really like the machine because of its size and weight and I would like to use it as a development platform.  I have 'toyed' with other Linux variants and find Ubuntu the most comfortable to use, hence I want to install Ubuntu on it.  Everything I read on the Ubuntu website and in the various forums points to doing an installation of Xubuntu 9.10 using the alternate version.

The screen during installation seems to be flawed in that the text installer is activated.  A blue-grey screen presents itself and it seems to flicker.  The installation finishes and reboots.  A white mouse appears clearly on the screen but then when the login page is presented, the page flickers very quickly and is washed out.  It gives the impression the image cannot be synchronised.  

I have tried 8.10, 9.04 in different flavours of Ubuntu and Xubuntu, live CD and alternate version, automatically partitioned and manualy partitioned.  None seem to work for me.  

Has anyone tried installing Xubuntu 9.10?  
Is there an older version that works better? 
Is it possible that the hard disk is too small?
Should I have an active internet connection during installation? (I am asking this because some of the installations 'complain' about not being able to find a DHCP server.)

From all the posts I have read, I can only conclude that a Dell C400 is not a very good machine to install Ubuntu on.  Is this a reality I should face?  Hope someone can point me in the right direction.

UPDATE:  This morning, I tried re-installing with a connection to a router connected to the Internet and I realised I omitted a detail.  During the text installation, the screen is blue and had black/dark grey tildes, '~', across it, on what seemed to be every line.  This is despite when it starts with a good white text on black screen.  It would seem the video chipset is not being detected properly.  I have not been able to figure out how to specify the chipset during installation.  Maybe someone could make a suggestion on how to do this.

Thank-you for your help!
I'm running Xubuntu 9.10 right now on my dell 1545 laptop.  It is fast and very easy to work with.  If you can install Ubuntu 9.10 you can also have the XFCE-desktop added to that.  Then you will have a choice at login.  It is the easiest way to go, use Synaptic Package Manager to install it.  I've never had much luck with "Alternate CD installers."

---

### Post by RedShifted on 2010-01-07
> **bobcollard said:**
> I'm running Xubuntu 9.10 right now on my dell 1545 laptop.  It is fast and very easy to work with.  If you can install Ubuntu 9.10 you can also have the XFCE-desktop added to that.  Then you will have a choice at login.  It is the easiest way to go, use Synaptic Package Manager to install it.  I've never had much luck with "Alternate CD installers."

Thank-you the reply.  

I have  successfully installed Xubuntu 9.10 for the 'alternate CD' and it works quite well.  What I note is that the installation on the C400 is complete and working, but the screen seems to be rotated about 3/4 inches to the right putting what was an the very right of the screen moved to the very left of the screen.  This suggests that during installation the video chip set was not recognised or recognised properly.  I will have to do more reading to understand how this can be changed manually.  Meanwhile I can use my D400 to do the work.

As I am still too green a Linux user to know what Synaptic Package Manager is, but I am sure I can find online documentation for it.

---

### Post by bobcollard on 2010-01-07
> **RedShifted said:**
> Thank-you the reply.  

I have  successfully installed Xubuntu 9.10 for the 'alternate CD' and it works quite well.  What I note is that the installation on the C400 is complete and working, but the screen seems to be rotated about 3/4 inches to the right putting what was an the very right of the screen moved to the very left of the screen.  This suggests that during installation the video chip set was not recognised or recognised properly.  I will have to do more reading to understand how this can be changed manually.  Meanwhile I can use my D400 to do the work.

As I am still too green a Linux user to know what Synaptic Package Manager is, but I am sure I can find online documentation for it.
Explore a little.  The button named Applications on the far left of your panel will lead you to System.  From System move to Synaptic Package Manager.  Click on that, it may ask for your password, if so type that in.  Open the window out and scroll down, you can see all of the packages for the different programs possible to use on your computer.  If you already know what you are looking for, begin typing the description in the search window and before you are finished, most of the time, it will come up on the screen.  If you are not sure what something does, click on it to highlight it and there is a description below the window.

---

### Post by RedShifted on 2010-01-25
> **bobcollard said:**
> Explore a little.  The button named Applications on the far left of your panel will lead you to System.  From System move to Synaptic Package Manager.  Click on that, it may ask for your password, if so type that in.  Open the window out and scroll down, you can see all of the packages for the different programs possible to use on your computer.  If you already know what you are looking for, begin typing the description in the search window and before you are finished, most of the time, it will come up on the screen.  If you are not sure what something does, click on it to highlight it and there is a description below the window.

Hello Bob ... thank-you for your last post.  I have now installed Xubuntu 9.10 about 3 times and it keeps installing the same way as I described in a previous post.   The issue seems to be it is not detecting the video chipset correctly.  Unfortunately I have not been able to figure out how to modify the drivers.  Everything I have read seems to say that the chipset gets detected automatically and the right drivers are selected.  If you could point me in the right direction it would be appreciated. ...cheers!

---

### Post by bobcollard on 2010-01-25
> **RedShifted said:**
> Hello Bob ... thank-you for your last post.  I have now installed Xubuntu 9.10 about 3 times and it keeps installing the same way as I described in a previous post.   The issue seems to be it is not detecting the video chipset correctly.  Unfortunately I have not been able to figure out how to modify the drivers.  Everything I have read seems to say that the chipset gets detected automatically and the right drivers are selected.  If you could point me in the right direction it would be appreciated. ...cheers!
I would recommend another distro with Xfce already set up.  Go to the following link and check it out.  The current Linux Mint 7 (Gloria) is based on Xubuntu with many drivers already built in.  [http://www.linuxmint.com/download_ce.php](http://www.linuxmint.com/download_ce.php)  scroll down to XFCE Community Edition and download it, burn to a disk and install it like you would Xubuntu.

---

### Post by leebaldwin on 2010-01-30
> **bobcollard said:**
> I would recommend another distro with Xfce already set up.  Go to the following link and check it out.  The current Linux Mint 7 (Gloria) is based on Xubuntu with many drivers already built in.  [http://www.linuxmint.com/download_ce.php](http://www.linuxmint.com/download_ce.php)  scroll down to XFCE Community Edition and download it, burn to a disk and install it like you would Xubuntu.
If thats the case,then install XUbuntu. It is native with XFCE installed on it. I am running a Dell Latitude C610 with Ubuntu 9.10 on it and I love it. I have hard drives that I switch in and out. One with Linux, the other Windows. I only do this due to my business.

---

### Post by corcomp84 on 2010-01-31
try disabling the visual effects.  after you install Ubuntu it will automatically activate the visual effects if its compatible, which can cause problems with your screen. Its worth a try.

---

### Post by 0nelove on 2010-02-09
8.10 runs fine on my c400.  If you google around, you'll find that this video chipset (i830M) has some quirks that caused corruption.  I had to dig around for a long while back when I installed this thing to fix the problem.  These 3 links discuss the issues involved:

[http://ubuntuforums.org/showthread.php?t=969939](http://ubuntuforums.org/showthread.php?t=969939)
[http://ubuntuforums.org/showthread.php?t=890843](http://ubuntuforums.org/showthread.php?t=890843)
[http://www.cse.unsw.edu.au/~chak/linux/c400.html](http://www.cse.unsw.edu.au/~chak/linux/c400.html)

I seem to recall that editing xorg.conf to use a different "AccelMethod" was the ticket.  Will try to remember to post my xorg.conf here...

OP, are you still looking for a solution?

---

### Post by 0nelove on 2010-05-13
> **0nelove said:**
> 
OP, are you still looking for a solution?

Guess not.

Just wanted to add to this thread that Xorg (as configured by my method) seems to have some sort of memory leak (maybe that's the wrong term).  After a few hours of use, xorg starts hogging all the cpu cycles (top shows xorg pinned at 100%).  So, if you use my solution, it's not as "perfect" as I may have thought.  Hoping 830M is supported on a newer linux somewhere.

...off to search.

---

### Post by Kixtosh on 2010-09-27
Well, I had a subscription to this thread and it just got bumped. I've had quite a bit of extra experience with Ubuntu and its variants since I first added my subscription, but here's what I have to add:

On a DELL CPi R400GT, with just 256MB maximum RAM allowed, a Pentium II 400 MHz CPU, and a 12GB hard drive: Ubuntu 9.10 Karmic Koala was indeed stable, but a bit slow (almost two minutes to boot up). I also had to work out some tricky sound problems with Karmic, but then I did find the following excellent solutions instead (with no sound problems to fix):

- Xubuntu with the LXDE package (much better than regular Xubuntu).
- Peppermint.
- Puppy 431 and Puppy LuPu 501.
- Lubuntu 10.04.

Xubuntu was noticeably faster than regular Ubuntu, but the LXDE desktop was an even bigger improvement. I added it from the Ubuntu Software Center, and then logged off (not shut down) to log back on after chosing the LXDE desktop instead of XFCE. I would probably use Lubuntu except that it is still a beta version, and Xubuntu with LXDE is just about as lightweight in everyday use from what I can see. Overall, boot time was reduced to about 60 seconds or less. Shut down takes less than ten seconds. Lubuntu, Peppermint and Xubuntu (with LXDE added) were all faster to start up than Puppy, even if I installed Puppy to the hard drive.

Also, Chromium was noticeably faster than Firefox on such an old machine

However, on a much newer Toshiba (but still not very new), with a maximum allowed of almost 1.3GB of RAM, and a 1.2GHz ULV Pentium Mobile CPU, there was no real advantage to using LXDE at all (including Xubuntu with the added desktop environment, Lubuntu or Peppermint). On this machine, I much prefer regular Ubuntu 10.04 Lucid Lynx. It has a much more sophisticated layout in my opinion with better user functionality.

The thread starter has 750MB of RAM, which should certainly mean that he/she should have been able to find something that worked correctly. Other than the sound problems I mentioned with Ubuntu 9.04 on that old Dell, I've had a lot of success with the other distributions I've tried on it.

---

