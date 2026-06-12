---
title: "Having some trouble with my periphals"
date: 2009-01-29
forum: General Help
---

### Post by EI51 on 2009-01-29
Hi There,
I've been messing around with Ubuntu for a couple weeks now and overall I'm very impressed with the distro.  
Little background: I have an eight year old Dell Inspririon 8100 laptop that I'm trying to keep running longer by using Ubuntu.  After some research I decided the best way to go about this was to use a Wubi and play around with Ubuntu 8.10 without worry about partitioning and things like that. All has gone well with the wubi install.  Already the old Dell runs better. However, I've been searching for a week to get my Canon Pixma ip1800 printer to work and it just won't print.  I downloaded and installed the packages from this site: [http://home.btconnect.com/jerryf/](http://home.btconnect.com/jerryf/) and I got there by folowing this thread: [http://ubuntuforums.org/showthread.php?t=445874](http://ubuntuforums.org/showthread.php?t=445874) which was the best I could find.
Also, and this one is just really getting me.  I went to sync my PalmOne Zire 31 and I found this bug report to help me do that, [http://bugs.launchpad.net/ubuntu/+souce/gnome-pilot/+bug/9983](http://bugs.launchpad.net/ubuntu/+souce/gnome-pilot/+bug/9983). The instruction were very straight forward, add these product ids etc to the .xml file.  I go to said file and the numbers and commands have already been added.  But guess what? The Zire 31 won't sync with the Palm OS. So does anybody have any ideas? Is it because I'm running it throuh the Wubi? I thought one of the advantages of the Wubi was to check to see if everything works before you commit to dedicated install?

All in all I'm still very pleased with Ubuntu and I hope this experiment of mine works so well that I can duel boot on my new computer (will have to keep Vista for AutoCAD and warrenty) and running solely on my old computer.  But I do need plenty of help.  Thanks.

---

### Post by icheyne on 2009-01-30
Wubi installs should operate like any other.

The printer should work fine. This page tells you where to find a suitable driver - [http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP1800](http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP1800)

Did you try this page to fix your Zire? [https://help.ubuntu.com/community/PalmZire31HowTo](https://help.ubuntu.com/community/PalmZire31HowTo)

---

### Post by EI51 on 2009-02-04
Thanks icheyne, I've since been able to get my printer working.  However, I'm still unable to get the Zire 31 synced. The post you gave me was helpful but since the product id and vender id are already logged in the xml file and my gpilot is not running, I don't know where to go from there. I haven't tried this through Evolution yet. I was using the palm OS feature.  I haven't set up Evolution but that may be what I do next. Thanks again.

---

### Post by EI51 on 2009-02-10
Well I'm having a strange time syncing this Palm Zire 31. I have the product and vendor IDs listed in the .xml file (in fact, they were already there!). I haven't been able to sync using gpilot or through Evolution. The link to the tutorial above says to go to Tools>Pilot Settings.  I do not have a tools menu drop down in Evolution. I have "syncronizing options" but thats just gpilot through evolution. Very strange. Don't know where to go from here.

---

