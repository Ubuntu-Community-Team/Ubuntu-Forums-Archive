---
title: "Amarok permissions?"
date: 2006-03-03
forum: Desktop Environments
---

### Post by nalmeth on 2006-03-03
Ever since I installed (the last time) Amarok has been having some problems with my music.
In "Collection" all all artists are listed, but the folders don't contain *any* files. Drag and drop anything into playlist window, it says "tried to add nothing to playlist".
So I use Files instead.. No biggie..
But when I try to change artist info, I'm told I don't have permission to.. I think the two problems are related...

BTW I use gnome primarily, but in KDE it is the same thing. Does gnome play into this somehow?

Thanks!

---

### Post by aysiu on 2006-03-03
It's not a Gnome thing, definitely. I've used AmaroK in Gnome.

It sounds as if it's a file permissions thing that has nothing to do with AmaroK.

Does your music folder live on a FAT32 partition? Does it live on an NTFS partition? Is there any way you can just look at the permissions by right-clicking the files?

---

### Post by nalmeth on 2006-03-03
I have no fat32 or ntfs, only good ol' ext3.
I checked permissions for my music, and each folder is missing write permission for group and others. I corrected a few of them, but they all seem to be missing this.. Do I have to reboot for this changes to take effect? If not, then something else is wrong, because I'm still getting this message when trying to change track info:

> Sorry, the tag for file:///home/nalmeth/Media/Music/Albums/*Pantera/vulgar display of power/05 Track 5.wma could not be changed.

UPDATE: Running gksudo amarok, I can use amarok features fully, but don't want to run amarok as root all the time..

Is there a way to change all files within a folder (namely my music folder) to have full read/write permissions?

chmod xvf 777 something or other ~/Media/Music? will this change all permissions within the folder as well?

ADDITION: While I'm on the subject of amarok, do I have to have KDE configured with my keyboard function buttons for amarok to be able to use them? I want the play/stop/forward/rewind to work with amarok in gnome like with rhythmbox, but amarok won't respond to them..

---

### Post by nalmeth on 2006-03-04
Still no luck with my collection in amarok...

I apt-get --purge removed amarok to delete configuration files, but when brought it back, I still couldn't use the COLLECTION or edit track data.
I installed the 1.4 beta version of amarok, and it doesn't work with my user in KDE or gnome. It crashes when trying to copy:
file:///home/nalmeth/.kde/share/apps/amarok/collection.db
to
file:///home/nalmeth/.kde/share/apps/amarok/collection-backup.db
I've created new users, and they have no trouble running amarok in KDE, and no problem seeing my tracks in COLLECTION. 

SO

Amarok must be having some problem attaining permissions with my main user account.
I've checked permissions for my account, and I am indeed permitted to do everything.

How do I check what level of rights amarok is operating with? It's such a small thing, but it's driving me crazy now. And with the new version, I can't even use it semi-functionally like before. It crashes when copying my collection. 

Whats the deal?
happened to anyone else?

---

