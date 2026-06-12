---
title: "how to add awn applets?"
date: 2007-10-20
forum: Desktop Effects &amp; Customization
---

### Post by mattgarm on 2007-10-20
Hi,

How do you add regular applets, like trash or show desktop? I don't know where the awn applet packages are placed.

Thanks

---

### Post by PPAAUULL on 2007-10-20
rith click the panel and hit add to panel and then select what you want to add.

---

### Post by mattgarm on 2007-10-20
No, I mean once you've done that you need to specify where they are. I don't know, I thought maybe /usr/lib/awn/applets or ~/.config/awn/applets but there's nothing there.

Thanks

---

### Post by PPAAUULL on 2007-10-20
OHHHH sorry I thought you ment the regular gnome panel.

---

### Post by PPAAUULL on 2007-10-20
I figured it out. Don't hit the "+" button hit the arrow that points this way "<--"

---

### Post by mattgarm on 2007-10-20
LOL, how stupid of me! :) Thanks!

---

### Post by medicineman24 on 2007-10-21
:lolflag: That took me like 5 minutes to figure out myself!!!!!

---

### Post by iamforgiven on 2008-03-19
Go to: [http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive](http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive)

Add the packages that end in bzr from  either Synaptic or apt-get once you add the sources in the link to your repositories.

---

### Post by fxguenea on 2008-04-27
I had the following problem... when i installed awn and started to configure it, i miss-closed the firefox applet and now dont know how to get it back... it doesn't show in the applet list of the awn manager configuration wizard... 

thanks

---

### Post by ktulu1115 on 2008-04-28
FYI, there are issues with the applets package.  According to applets install directions, they say to add a repository to get avant-window-navigator-trunk:

[http://wiki.awn-project.org/Awn_Extras:Installation](http://wiki.awn-project.org/Awn_Extras:Installation)

However, trying to install avant-window-navigator-trunk results in the following:

~$ sudo apt-get install avant-window-navigator-trunk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  avant-window-navigator-data-trunk libawn0-trunk
Recommended packages:
  awn-manager-trunk
The following packages will be REMOVED:
  avant-window-navigator awn-manager libawn0
The following NEW packages will be installed:
  avant-window-navigator-data-trunk avant-window-navigator-trunk libawn0-trunk

Apparently this is a known issue: [https://launchpad.net/~awn-testing/+archive](https://launchpad.net/~awn-testing/+archive)

So basically it looks like you can't install any awn-applets at the moment.  Anyone else figures this out please post a solution. :)

---

### Post by ktulu1115 on 2008-04-28
*SOLVED*

Figured out a solution.  Use a new repository and install -bzr versions of packages: [http://ubuntuforums.org/showthread.php?t=762363](http://ubuntuforums.org/showthread.php?t=762363)

This allows you to install latest version of awn/avant which is much nicer.  Also awn-applets is easily installed from this repo.

---

### Post by SomeGuyDude on 2008-04-29
The packages that came with Hardy are screwed up. Uninstall AWN entirely, follow the directions from reacocard's tutorial.

---

