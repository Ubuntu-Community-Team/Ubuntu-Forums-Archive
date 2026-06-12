---
title: "show mounted cd/dvd's on gnome dekstop but hide mounted windows partitions"
date: 2005-12-04
forum: Desktop Environments
---

### Post by serenity on 2005-12-04
hey all, just recently started dual booting with Windows XP and Ubuntu 5.10, and thanks to all the guides and responses to other people on this forum i've been able to figure out pretty much everything i had questions about, but i haven't been able to find a fix for this......

following this guide ([http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-windows-partitions](http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-windows-partitions)) i set my 4 windows partitions (3 ntfs, 1 fat32) to auto-mount each time i boot into linux, unfortunately by default this made each mounted partition show up on the desktop which was cluttering things up more than i wanted so i went to Applications -> System Tools -> Configuration Editor -> apps -> nautilus -> desktop and unchecked "volumes_visible"

Unfortunately, with this option, when i put in a cd or dvd into one of my 2 drives they don't show up on the desktop anymore like i'd like ( /dev/hdd mounts to /media/cdrom0 & /dev/hdc mounts to /media/cdrom1 )

is there some file or something i can edit to not show my mounted Windows partitions on the desktop but still show the mounted cd/dvd's on the desktop ??

thanks for any replies

---

### Post by linbetwin on 2005-12-04
If you don't want to see your mounted Windows partitions on the desktop don't mount them in /media. Create a new directory (folder) like, say, /xp and in /xp create four subdirectories for your Windows partitions (ex. c, d, e, f).

I'm sorry but I can't advise you on the CD/DVD-ROM problem.

---

### Post by serenity on 2005-12-04
if i do that will the four mounted partitions still show up under "Places" on the Gnome Panel?? and on the sidebar in the filebrowser (is that still nautilus?)??

i'd still like to be able to keep that functionality

---

### Post by serenity on 2005-12-04
tried mounting my windows partitions in another folder (/xp) like recommended and it they don't show up in the Places menu or the nautilus sidebar anymore, which isn't what i'm looking for

---

### Post by Gray. on 2005-12-05
In nautilus (the file browser):
Browse to whichever folder you wish to add the places menu (in your case /xp)
The go Bookmarks > Add bookmark
Voila!

---

### Post by Canuckelhead on 2005-12-05
the easiest way to do this ... imho is to not remount anything... go to applications/system tools/config editor/apps/nautilus/desktop... and uncheck volumes visible....  
this will remove them from the desktop...

then creat a launcher for your dvd etc using right click anywhere on the desktop....
make the type link and under the url add the path to the specified device!

---

### Post by serenity on 2005-12-05
[QUOTE=Gray.]In nautilus (the file browser):
Browse to whichever folder you wish to add the places menu (in your case /xp)
The go Bookmarks > Add bookmark
Voila![/QUOTE]
thanks, just what i was looking for

---

### Post by Bagster on 2007-02-21
Hi. Another idea is to remove the keyword user from the list. is fstab. This will stop the partition from showing on the desktop

---

