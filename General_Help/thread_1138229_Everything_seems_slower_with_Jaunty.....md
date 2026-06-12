---
title: "Everything seems slower with Jaunty...."
date: 2009-04-26
forum: General Help
---

### Post by toejamfootball on 2009-04-26
Has anyone else noticed this? It seems for me everything in general is much slower with Jaunty then it was in Interpid or Hardy Heron.

For eg. just right clicking on the Desktop, the menu takes a little while to pop up, and navigating through the Application, Places, Start menus is much slower to respond.

Open Office Write took much longer to load also, and for the first 10 minutes or so of typing it wasn't responding in time, my text would take a little while to catch up with me.

Thanks to anyone who has any ideas at all!

James/

---

### Post by stoneage on 2009-04-26
I found when updating to Gutsy from Feisty instead of doing a clean install things ran slower, but not to that extent.

What are your system specs and how old is your HDD?

---

### Post by philinux on 2009-04-26
[http://www.goitexpert.com/entry.cfm?entry=ubuntuguide](http://www.goitexpert.com/entry.cfm?entry=ubuntuguide)

Faster Gnome/UBUNTU Menus


Click "Places", "Home Folder". Now, we need to create a file called .gtkrc-2.0. To do this we right-click on any white space and move our mouse over "Create Document" and click "Empty File". We now rename this file to .gtkrc-2.0.



We will now double-click the ".gtkrc-2.0" file you just created and add the following line to it;

gtk-menu-popup-delay=0

Click Save and close the window.  You will have to log back in to see the results.

If you feel your Ubuntu menus open too fast now and would like to make them slower, the suggested optimal speed is:

gtk-menu-popup-delay=100

However, for you to be able to edit ".gtkrc-2.0" again we need to tell Ubuntu to show hidden files.

Go back to your "Home Folder"

Click "View" and a menu expands. In this menu you will find something called "Show Hidden Files", click it.

You will now be seeing a whole bunch of files you have never seen before. Find the file called ".gtkrc-2.0", open it and delete gtk-menu-popup-delay = 0, replace it with gtk-menu-popup-delay = 100.

If for whatever reason you do not like this tweak, it is safe to delete the file called ".gtkrc-2.0" and all will be back to normal.

---

### Post by blueyelabs on 2009-04-26
I've found everything to be much slower, especially login times and compiz effects e.g. opening firefox was horrendously delayed and choppy.
This hasn't got anything to do with the computer, since in Intrepid everything was really fast and the computer is brand new.

---

### Post by toejamfootball on 2009-04-26
> **stoneage said:**
> I found when updating to Gutsy from Feisty instead of doing a clean install things ran slower, but not to that extent.

What are your system specs and how old is your HDD?

Pentium 4 2.4Ghz 2Gb RAM. I'm guessing the HDD is about 8 years old. Intrepid was lightning fast.

> **philinux said:**
> [http://www.goitexpert.com/entry.cfm?entry=ubuntuguide](http://www.goitexpert.com/entry.cfm?entry=ubuntuguide)

Faster Gnome/UBUNTU Menus



Thanks, I will give this a go tomorrow after Uni.

> **blueyelabs said:**
> I've found everything to be much slower. Especially login times and compiz effects e.g. when opening firefox the delay is horrendous.
This hasn't got anything to do with computer, since in Intrepid everything was really fast and the computer is brand new.

My PC is pretty old, but Intrepid ran very smooth and fast. Jaunty is choppy as.

---

### Post by stoneage on 2009-04-26
You could try running memtest from the Live CD to test the RAM.
Try using badblocks to check the HDD. ```
man badblocks
``` for usage info.

Did you update or do a clean install?

---

### Post by toejamfootball on 2009-04-26
> **stoneage said:**
> You could try running memtest from the Live CD to test the RAM.
Try using badblocks to check the HDD. ```
man badblocks
``` for usage info.

Did you update or do a clean install?
RAM is fine, tested only a couple days ago. I did an upgrade not a clean install.

Will check HDD after UNI later.

---

### Post by toejamfootball on 2009-04-28
Just about everything is back to normal now, thanks guys.

Only one thing left, it is really starting to bug me. When I close an open window (from full) and it drops down to the panel. The Desktop takes a while to appear. The background image is there, but there is a strange black Frame where the window used to be, and anything that is on the Desktop takes a few seconds to show up.

For smaller open windows, the black frame trails behind the window as it drops down. I have all effects turned off.

I can also not do *anything* until the Desktop icons etc come back, I cannot open other windows, check Pidgin etc. If anyone has any ideas how to stop this, it would be greatly appreciated. Thanks.

---

### Post by joshaman on 2009-04-28
Removed

---

### Post by Briga on 2009-04-28
Well I did a clean install and 9.04 looks way faster. And I mean way faster. Of course this is only to say that there must be something to fix. 

If you have /home on a separate partition I would seriously consider a new install.

---

### Post by toejamfootball on 2009-04-28
> **Briga said:**
> Well I did a clean install and 9.04 looks way faster. And I mean way faster. Of course this is only to say that there must be something to fix. 

If you have /home on a separate partition I would seriously consider a new install.
I have been thinking about doing a fresh install. This does mean I have to download the .iso now though after waiting like 2 hours to upgrade to Jaunty. Bit of a PITA.

---

### Post by stoneage on 2009-04-28
> **joshaman said:**
> Everything is slower!  It's a pain in my ***.

Why the hell would there be a problem with his HDD or Memory if Intrepid ran fine?  Durr!!

Well the next time you have a problem, ask yourself was it running fine yesterday.....

A slow system is one of the first signs that hardware is failing....

Once you have ruled out hardware the problem MUST be something else.

---

### Post by toejamfootball on 2009-04-29
> **stoneage said:**
> Well the next time you have a problem, ask yourself was it running fine yesterday.....

A slow system is one of the first signs that hardware is failing....

Once you have ruled out hardware the problem MUST be something else.
The whole PC is around 8 years old....

---

### Post by scheuri on 2009-04-29
> **toejamfootball said:**
> The whole PC is around 8 years old....
Taken into account that businesses usually change their hardware (desktop) at lesat evry 4 years (maybe even earlier) your 8 year computer is rather old.

A harddisk usually can fail every second after about 3-4 years (depending on its usage).
On a 8 year old computer hardware failures seem not to be far away.

---

### Post by sumpm1 on 2009-04-29
I can vouch that I have use Jaunty on a couple of systems from a fresh install and it runs damn fast, faster than Intrepid and Hardy for me.

---

### Post by toejamfootball on 2009-04-29
> **scheuri said:**
> Taken into account that businesses usually change their hardware (desktop) at lesat evry 4 years (maybe even earlier) your 8 year computer is rather old.

A harddisk usually can fail every second after about 3-4 years (depending on its usage).
On a 8 year old computer hardware failures seem not to be far away.

Everything is backed up 2-3 times.... on new HDDs. I will run this PC to it's grave.

> **sumpm1 said:**
> I can vouch that I have use Jaunty on a couple of systems from a fresh install and it runs damn fast, faster than Intrepid and Hardy for me.

I am going to install fresh today I think.... thanks.

---

### Post by jamesobooth on 2009-04-29
You know, I ran across the same thing.  I updated from 8.10 and noticed the system was much slower.  My cursor was not smooth.  Internet browsing/downloading was MUCH slower.  My system was acting like it was VERY busy when it wasn't.  CPU wasn't being pinned.  Memory wasn't maxed out.  HDD wasn't busy.

I tried testing HDD, RAM.  I tried wifi and wired.  I tried different networks on different hardware.

I tried wiping the HDD and re-installing a couple times with different partition schemes to no avail.

I just went back to 8.10 today.  I'll wait til the kinks get worked out.

---

### Post by Bibek on 2009-04-30
For me, Jaunty is much much faster than hardy.

---

### Post by 4Orbs on 2009-04-30
Far out, philinux. Making the menu respond quicker improved the "feel" dramatically. Thanks for passing along the tip.

---

### Post by Eneerge on 2009-04-30
You can also use  gtk-menu-popdown-delay=100 or some integer value.  I found it prevents the menus from delaying when I change top level menus quickly after just loading another menu.  EG: If you use the main menu instead of the default custom menu, you open System->Administration and then you immediately go to ->Preferences after scrolling a little, sometimes you will experience a second delay waiting for the menu to "popdown" before it brings up the one you selected.  It seems that if you set both values to 100, your active delay will actually be 200 when scrolling quickly.  200 is quicker than the default, which makes it snappier.

---

### Post by 4Orbs on 2009-04-30
...and that made the menu action quick AND smooth. Thanks for the added tip, eneerge.

---

### Post by muhannadfa on 2009-04-30
i've da same issues and do't tell me my hardware is failing cause i use XP dual-boot
---------------------
don't bother ur hardware
it jaunty bugs man
move back to 8.10 if it makes u happy
------------------------
H-H , your hardware is failing !!!??? u make me laugh dude :D

---

### Post by 4Orbs on 2009-04-30
> move back to 8.10 if it makes u happy

I considered moving back to 8.10 a few weeks ago, but now that I've got Jaunty sorted out, not gonna change. Ext4 caused me some problems so I went back to ext3. I'll start using ext4 again probably in a couple of months because it rocks.

---

### Post by toejamfootball on 2009-05-01
I did a fresh install from CD. All the menus etc are fine now. Just this weird thing with the black frame beign left behind when I minimise windows..... :(

---

### Post by blueyelabs on 2009-05-04
I don't know if I can be bothered with a fresh install. I've always found Ubuntu a little volatile and sensitive so I don't want to change anything since it all works at the moment.
The hassle of fresh installing is a little too much anyway. I've done it all too often in the past. Never again.

---

### Post by Mirge on 2009-05-04
> **philinux said:**
> [http://www.goitexpert.com/entry.cfm?entry=ubuntuguide](http://www.goitexpert.com/entry.cfm?entry=ubuntuguide)

Faster Gnome/UBUNTU Menus


Click "Places", "Home Folder". Now, we need to create a file called .gtkrc-2.0. To do this we right-click on any white space and move our mouse over "Create Document" and click "Empty File". We now rename this file to .gtkrc-2.0.



We will now double-click the ".gtkrc-2.0" file you just created and add the following line to it;

gtk-menu-popup-delay=0

Click Save and close the window.  You will have to log back in to see the results.

If you feel your Ubuntu menus open too fast now and would like to make them slower, the suggested optimal speed is:

gtk-menu-popup-delay=100

However, for you to be able to edit ".gtkrc-2.0" again we need to tell Ubuntu to show hidden files.

Go back to your "Home Folder"

Click "View" and a menu expands. In this menu you will find something called "Show Hidden Files", click it.

You will now be seeing a whole bunch of files you have never seen before. Find the file called ".gtkrc-2.0", open it and delete gtk-menu-popup-delay = 0, replace it with gtk-menu-popup-delay = 100.

If for whatever reason you do not like this tweak, it is safe to delete the file called ".gtkrc-2.0" and all will be back to normal.

> **Eneerge said:**
> You can also use  gtk-menu-popdown-delay=100 or some integer value.  I found it prevents the menus from delaying when I change top level menus quickly after just loading another menu.  EG: If you use the main menu instead of the default custom menu, you open System->Administration and then you immediately go to ->Preferences after scrolling a little, sometimes you will experience a second delay waiting for the menu to "popdown" before it brings up the one you selected.  It seems that if you set both values to 100, your active delay will actually be 200 when scrolling quickly.  200 is quicker than the default, which makes it snappier.

+1 for these tips! Just implemented it here too, and it's NICE...

---

### Post by Pluvius on 2009-05-13
Hey guys!this is my first post, even though i've been reading around for some time now.

I was on intrepid 8.10 and everything was fine, but then after i upgraded to 9.04 things went wrong, everything is slow and takes ages to load (firefox,menus...) can anyone help please?

---

