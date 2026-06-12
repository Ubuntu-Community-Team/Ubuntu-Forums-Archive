---
title: "Note to Self: Compiz is broken"
date: 2010-03-01
forum: Desktop Environments
---

### Post by RasterBurn on 2010-03-01
hello all, i need a bit of help with compiz, having some major troubles with it... i will boot my computer normally and compiz loads as it is supposed to do, the problem i am having is that when i go to the apperance preferences and to the visual effects i can select to use the Extra effects setting but as soon as any window closes (aka keep settings window) the effects revert back to None, also if for some odd reason i manage to get the visual effects to stick they revert back to none the next time i reboot, does anyone have a fix for this issue? I am running UBUNTU 9.10 x86_64 using the ATI graphics drivers downloaded directly from ati.amd.com and my video cards are "ATI Sapphire HD 3870" only using 1 of the 2 at the moment.

---

### Post by elosier on 2010-03-01
I have a similar, possibly identical issue : 

When I log on, visual effects do not work.  If I go to System -> Preference -> appearance -> Visual effects it will usually be at none (even thought it was at extra).

I don't have to reboot for this to happen, simply log off and on.

I installed the compizconfig-setting-manager and changed a few settings just to see if that would make the settings persist to no avail.

I'm using ati's drivers off of ati/amd website catalyst 10.2 with a ATI Radeon HD4770 (the suggested drivers really slowed everything down to a crawl, so I went and got that one).

Perhaps unrelated info (but since I don't know, I'll enter them anyway) :

I seem to have erased my only working copy of /etc/gdm/Init/Default while trying to add the numlockx lines at the end.  File saved without errors but when I logged off the display went black for a few minutes.  I had to reboot, after reboot the file had 0 bytes.  Of course I did not back it up (somebody punch me).  I reinstalled GDM using synaptic to no avail.

Also the  System -> Preference -> appearance -> Theme pictures are weirdly screwed up (check attachment).  I have not seen this problem anywhere else.

Other appearances settings seems to persist (ex. : background image).

Thank for any and all help on this issue.

---

### Post by elosier on 2010-03-02
I found this thread : [http://ubuntuforums.org/showthread.php?t=1410531](http://ubuntuforums.org/showthread.php?t=1410531) which may explain the problem we're having.  Although I'm not sure if the issues explained are really similar to what I'm seeing.

---

### Post by RasterBurn on 2010-03-02
that one seems to be that little bit different in terms of hardware, as for their compiz problems, could be close or just related to the same problems we are having.

---

### Post by profslughorn on 2010-03-02
install simple-ccsm from synaptic. it adds a "custom" option to the "visual effects" settings. once you choose "custom" whatever you do with compiz should stay put.

---

### Post by RasterBurn on 2010-03-03
ok so i installed simple-ccsm and then set my desired effects and rebooted the computer, the problem still persists, now i have a new problem where my desktop doesnt work properly untill i log out and log back in... :(

---

### Post by RasterBurn on 2010-03-06
hey all, back with some updated info, a couple days ago i got the latest update for kernel-image-2.6.31.20 anyways had to do some reconfiguring with xorg and my ati driver to get it to work properly and from what i have done so far compiz seems to be working properly with the new kernel... my testing went as far as logging out and back in as well as rebooting once

---

### Post by elosier on 2010-03-06
None of that seemed to have worked for me.  I need to do some testing.  I also need to find where the crash info is going.

I upgraded to the new kernel and install the simple-ccsm.  Now, when I log on, the first program I open seem to make compiz crash after a few seconds (I go back to 2 desktop and I loose all the compiz effects).  When I go to System->preferences->Visual effect they are set to none and if I reset it to personalized it never crashes again until next time I log on.

Really weird.

---

### Post by RasterBurn on 2010-03-07
apparently i have spoke a bit too soon, my compiz is still half broken, it loads the effects when i select them though it forgets them when i boot up the next time :( unfortunately i have to turn on the effects each time i boot up, i have tried simple-css but it seems to disable my right click (on the desktop) and desktop icons :(

---

### Post by RasterBurn on 2010-03-18
I may still be speaking too soon once again, but last night i made a list of problems that i have to solve, i will know for sure if its the list is fixed or not, but it seems to be an issue related to the ATI driver downloaded from ati.amd.com i was searching how to setup crossfire on Linux and what i found was to install envyng-core and run "sudo envyng -t" to have it install the appropriate drivers for my video card after that, all i had to do is comment out line 34 on xorg.conf so that i can use the CCC and reboot the computer, this morning i woke up and booted the computer and it seems that the 5 issues i had listed regarding effects and gnome have been solved i will know for sure if everything is fixed by the time the next kernel comes out @elosier try following the steps i have done and see if that fixes things for you as well :)

---

### Post by 5735guy on 2010-03-20
Ubuntu purge compiz-fusion
[http://ubuntuforums.org/showthread.php?t=546429](http://ubuntuforums.org/showthread.php?t=546429)

Enabling Compiz Fusion On An Ubuntu 9.10 Desktop (NVIDIA Cards)
[http://www.howtoforge.com/enabling-compiz-fusion-on-an-ubuntu-9.10-desktop-nvidia-geforce-fx-5200](http://www.howtoforge.com/enabling-compiz-fusion-on-an-ubuntu-9.10-desktop-nvidia-geforce-fx-5200)

ATI Cards

RadeonDriver
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

RadeonXpress
[https://help.ubuntu.com/community/RadeonXpress](https://help.ubuntu.com/community/RadeonXpress)

---

### Post by elosier on 2010-04-10
Upgrading to the proprietary drivers version 10.3 is what solved it for me.

---

