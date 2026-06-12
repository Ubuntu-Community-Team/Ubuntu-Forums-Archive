---
title: "OH NO!! Just re-installed 9.04 and I've lost all my data!! PLEASE HELP"
date: 2009-05-17
forum: General Help
---

### Post by blue carrot on 2009-05-17
hi guys,
I was having some serious problems surrounding restricted nvidia graphics drivers as has been discussed in these forums by many people.

in the process of trying one of the fixes my computer would no longer start up properly, it would just go to a blank screen. after trying what i could and what i'd read in the forums, i decided to do a reinstall from the disk of 9.04. i thought that it would be the same as when i upgraded from 8.10 to 9.04 in that it would just keep all my music, photos etc. ready to use.

but now that i've installed, i can't see ANY of my stuff!! and the hard drive says that it has more space avaliable than it should if my stuff was still there.

when installing i (stupidly) chose 'use whole drive' rather than installing the 2 versions of 9.04 side by side. this was a dumb move i guess but there you go.

is there ANY way that i can recover my data? i'm doing a lot of work for university etc. at the moment that was on there an not backed up...assignment due in 3 days...crap!!

PLEASE HELP ME

---

### Post by aysiu on 2009-05-17
Well, the most important thing to do is to reboot with a live CD right away. Don't add any more files. Don't delete any files. Don't modify anything.

You can use *photorec* off the live CD to try to restore your deleted files:
[http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/](http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/)

The instructions are for Windows, but the only difference is that you choose the Linux filesystem option (Ext3 instead of NTFS).

---

### Post by HermanAB on 2009-05-17
Howdy,

My sincere condolences with your loss.  

The next time you install, do create a separate /home partition.  If /home is a partition, then you can re-install and simply choose NOT to format that partition.

The older and wiser Linux installers such as Mandriva and Suse do that by default, but Ubuntu is one of the young and reckless ones that must be handled with care.

---

