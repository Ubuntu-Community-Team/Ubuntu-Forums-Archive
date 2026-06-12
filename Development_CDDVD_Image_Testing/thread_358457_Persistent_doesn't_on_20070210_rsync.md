---
title: "Persistent doesn't on 20070210 rsync"
date: 2007-02-10
forum: Development CD/DVD Image Testing
---

### Post by jerrylamos on 2007-02-10
Test case type: persistent mode - failed
Date of testing: 10 Feb 2007
md5sum confirmed: Yes for current image today, 20070210
Bugs identified: Tried 3 times to get persistent mode to work, wouldn't.
Comments: 
Formatted casper-rw as per Ubuntu instructions then rebooted F6 persistent
selected control panel shared folders which needed smb package which it installed O.K.
network places to a laptop running Dapper dual boot
used pointer drag to copy files from Dapper desktop to Feisty desktop
rebooted F6 persistent - files were not there.

Big clue: casper-rw icon showed up on desktop.  When persistent is working, casper-rw icon does not show.

Proof: cranked up 20070207 did the same thing.  Files persisted with F6 persistent.  casper-rw icon does not show.
Note: had to use synaptic to get samba.  shared folder package install wouldn't.

Another 20070210 note: restart, after a while I notice nothing's happening.  I squint at the bottom of screen and in very very tiny dark blue on black letters it says remove CD and press enter.  Can't do it.  Drawer is not open and won't open by pushing button.  20050207 works as expected.

---

### Post by pochu on 2007-02-11
Have you reported those bugs in Launchpad?

---

### Post by jerrylamos on 2007-02-11
O.K., reported bug 84591 on persistent mode failure and 84592 on no CD eject on shutdown for 20070210 and 20070211 builds.  20070207 does not have these problems on my systems.

---

### Post by jerrylamos on 2007-02-12
Checking status of bugs I've reported in launchpad on today's Feb 12 daily image.

Persistent mode still isn't.

Shutdown or restart message says "please remove CD and close drawer, press enter" however Feisty didn't open the drawer and manual pushbutton doesn't work so I can't remove.

Network Manager says "No network connection" where I obviously have have one to enter this reply to thread.

Cheers....

---

### Post by jerrylamos on 2007-02-13
Checking daily build 20070213 for bugs in this thread and have been reported on launchpad.
Still there.
Persistent mode isn't.  An oddity: two casper-rw icon's on screen, both with same UUID while there's really only one device.
Network manager says "No network connection" as I make this entry.
Shutdown doesn't eject and doesn't power off after pressing ENTER.  (Anyone with impaired vision will never be able to read that tiny black on blue print).
All these items worked on 20070207.
Cheers, Jerry Amos

---

### Post by jerrylamos on 2007-02-14
20070214 build still has same bugs reported in launchpad: persistent isn't, shutdown doesn't eject or power off, network manager "no connection" when there is, dhclient errors,  Most of these worked on 20070207.

Control panel has grown some more: it's now 3 screens tall.  Is there any way to set a list mode like Applications or Places?  As it is, there's only 9 lines of info on a 1024x768 screen, which can easily display three times that many.  For example I just counted 29 lines in Bookmarks which are perfectly readable and don't even start at the top of the screen.

Cheers, Jerry

---

### Post by jerrylamos on 2007-02-22
As of 20070222 persistent mode is still broken.  Anyone know which package or script sets up persistent?  

Example, /etc/init.d/casper does shutdown which fails to eject the CD.  Problem was the eject target was /live_media should be /cdrom.  If I make that change in casper shutdown ejects CD like it should.

Is there some sort of script used on boot up that detects the "persistent" option and sets it up?  Thanks, jerry

---

