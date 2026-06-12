---
title: "Gnome hanging on start up"
date: 2006-01-06
forum: Desktop Environments
---

### Post by Omnios on 2006-01-06
Im havinng serios problems with Gnome on log in. I have both KDE and  gnome but prefear to use gnome. Also I  seem to have two Ubuntu kernals in Grub. Also since the  last kernal upgrade my boot up is now Kubunttu lol.

 Anyways when I tryed  to log into gnome it hangs on the ssplash screen and the components dont load. Funny thing is if I keep ctrl-alt-backspace it works sometimes with errors. I had it going but gnome pannel was frozen. I already corrected it once by reinstalling GDM but that did not help fix it this time. Aalso I tryed to uninstall gdm and reinstall it from command line as I thoguht it may have soemthing to do with kdm. Anyways  there was a fail to initionalize k9 sommething  or something like that. Gdm works but it wont leg me og into Gnome.

 Aanyone haave similar problems? AAny help greatly apreciated.

---

### Post by Omnios on 2006-01-06
Just found out I can not log into faailsafe either

---

### Post by zappa86 on 2006-01-06
Have you tried just going into a regular terminal shutting down your xdm (I know to stop GDM its /etc/init.d/gdm stop) and just trying a regular startx and see if that freezes.

---

### Post by Omnios on 2006-01-07
I uninstalled the owld kernel and know it is saying fail saafe Ggnome is not installed I think it may have something to do with the last kernal upgrade

---

### Post by Omnios on 2006-01-08
My computer was buissy doing Fold@home charity work so I put this off for a bit but now im reaady to try to repair the problem. First off my computer is doing funny things things keep breaking in KDE and need constant attention. The latest was my firestarted not aautoloading on KDE log in even though I installed the firestarted kde start up script thing. 

 My current though is to try to reinstall gnome but I can not seem to find the gnome desktop package and also in KDE my apt-get does not seem to have the reinstall option. 

 ANy ideas on how to kill this problem?

---

### Post by Omnios on 2006-01-08
Looks like my gnome got trashed. I was playing around with samba to test and and learn a bit about networking with my P2 which is running PC-BSD (it has a ps-2 mouse connected to a com port with a serial adapter which is a pain with Linux). Anyways my home directory was left on share by accident and best guess is someonee trashed my gnome files.  Anyways I was running a large folding@home project and thankfully got that done running KDE. Guess my best start is to reinstall gnome. Is there a Ubuntu desktop download? Or what is the best way of trying to correct this?

---

### Post by Dr. Nick on 2006-01-08
try [B]sudo apt-get install ubuntu-desktop
[/B]That should reinstall install any missing packages, not sure if it will reinstall all of gnome or not.

Do you have other users for your system that you could try to login as? It may just be your personal gnome config files are trashed

---

### Post by Omnios on 2006-01-08
Looks like Gnome is trashed even safe mode Gnome does not work. Tryed to install Ubuntu-desktop and it said I  had latest version and also tryed reinstalling which did nothing. Think im going to try to uninstall GNome dektop and try installing it again.

---

### Post by Dr. Nick on 2006-01-08
Unintsalling the ubuntu-desktop package will not remove gnome unfortunately.  You may have to pick a gnome app and remove it, like gnome-panel. Never done this before. My idea would be to remoe the .gnome folder from our home directory and it will delete any perosnal settings in gnome which may help depending on the problem

---

### Post by Omnios on 2006-01-08
Funny thing cleared out all the filesharing and found a samba allow rule in firestarter that I removed. I rebooted and managed to boot into gnome this time. Anyways when I tryed to boot into gnome safemode it gave me an error that gnome safstart was not installed in GDM. Worse come to worse If I can get failsafe to work I can deleate the gnome set up files and rebuil my desktop.

---

### Post by Dr. Nick on 2006-01-08
Glad you sorta got it. I had trouble with gnome hanging up when it couldnt connect to an access point, It worked a few times but most of the time it stopped at the spash screen. I imagine thier is something that just hangs up and stops it from loading. the failsafe option may be fixed with a gdm reinstall, if not I dont know how to di it, Dapper is only 4 months away so maybe upgrading to it will fix it all :)

---

