---
title: "Azureus auto-updater = broken stuff"
date: 2006-02-11
forum: Desktop Environments
---

### Post by Dustin Wyatt on 2006-02-11
I went ahead and let Azureus auto-updater update to the latest version (2.4.0.0).  Bad idea.

It went through the download ok, but when it tried to restart Azureus it never came started again, so I did it manually by clicking the Gnome menu entry for Azureus.  

This brought up version 2.3.0.4 with NO torrents listed and completely unconfigured.  I checked out .Azureus in my home folder and all my config info and torrents were gone.

My actual files in progress and completed were still there of course, but I was seeding like 30 files and I don't remember which files there I was seeding since they were mixed in a directory with a bunch of files I was no longer seeding...

---

### Post by Dustin Wyatt on 2006-02-11
quick update to save anyone else who has problems...

Turns out that my old settings were not deleted.  They were in .azureus, while the new (supposed to be new even though it was 2.3.0.6 instead of 2.4.0.0) was pointing to .Azureus.

I ended up just completely removing azureus via [http://ubuntuforums.org/showthread.php?t=90797](http://ubuntuforums.org/showthread.php?t=90797) and reinstalling via [http://easylinux.info/wiki/Ubuntu#How_to_install_P2P_BitTorrent_Client_.28Azureus.29](http://easylinux.info/wiki/Ubuntu#How_to_install_P2P_BitTorrent_Client_.28Azureus.29) while replacing 2.4.0.0 for 2.3.0.6.

All is now well.

---

### Post by denisesballs on 2006-02-11
Well I think you have to be root to do updates. I tried doing the auto-update while running as root, and everything went fins EXCEPT it keeps saying I need to update the swt library. It just keeps rebooting saying it needs to update it, but doesn't install it. Oh well.

---

### Post by jeremy on 2006-02-12
[QUOTE=denisesballs]Well I think you have to be root to do updates. I tried doing the auto-update while running as root, and everything went fins EXCEPT it keeps saying I need to update the swt library. It just keeps rebooting saying it needs to update it, but doesn't install it. Oh well.[/QUOTE]
I updated it from a console, 'sudo azureus', and all is fine, except that I have the same problem with the swt library.

---

### Post by jeremy on 2006-02-12
I just want to add that if I cancel the updater, azureus runs fine.

---

### Post by shizow on 2006-02-14
i have also the same problem with the swt update, azureus always wants to update swt, it downloads it, restart and wants again to update, (using sudo azureus doesnt help either)

---

### Post by mpozzi on 2006-02-15
Same problem with the update... anyone managed to solve ?

---

### Post by newuser111 on 2006-02-15
[http://www.ubuntuforums.org/showthread.php?t=129152](http://www.ubuntuforums.org/showthread.php?t=129152)

---

### Post by shizow on 2006-02-15
[QUOTE=newuser111][http://www.ubuntuforums.org/showthread.php?t=129152](http://www.ubuntuforums.org/showthread.php?t=129152)[/QUOTE]

is there not another way than installing azureus in /opt like described in the thread mentioned

---

### Post by newuser111 on 2006-02-15
wget klik.atekon.de/client/install -O -|sh

[http://azureus.klik.atekon.de/](http://azureus.klik.atekon.de/)

edit: the auto update doesnt work in the klik version,  it is version 2.3.0.0, but klik only creates one compressed file, and just delete it to uninstall

the way in the link i posted is the only way i could get it to update properly and torrents also dont get stuck at zero or slow speeds like they did with the repo version (for me at least)

---

