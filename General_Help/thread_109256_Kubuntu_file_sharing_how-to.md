---
title: "Kubuntu file sharing how-to"
date: 2005-12-28
forum: General Help
---

### Post by php4us on 2005-12-28
This is where I love Xandros better -- easy file sharing.

We're about 40% of all PCs migrated to Kubuntu when we found out that we are unable to make a folder shared to another Kubuntu desktop. Of course, i may be missing it only.  So, can you please walk me thru the process of sharing directories with one Kubuntu desktop to another? The graphical way is appreciated.

Thanks.

---

### Post by stimpack on 2005-12-28
Looked into SSH? ([http://www.ubuntuforums.org/showthread.php?t=30709](http://www.ubuntuforums.org/showthread.php?t=30709)) very powerfull and secure. KDE kioslaves mean you can use sftp:// in any program for transfering files.

Cant help if your going the SAMBA route, never used it.

---

### Post by GoldBuggie on 2005-12-28
kcontrol->Internet & Network->File Sharing
There you can add folders and change some options etc. Either thrue nfs or samba.

I do remember that on hoary(which is the computer I have at home but I can't check that now since I'm far away from it) you could right-click on a folder and go to the share-tab and manage everything from there. Don't know if it was the smb4k that did it or not. Anyway...use kcontrol otherwise.

---

### Post by php4us on 2005-12-28
[QUOTE=GoldBuggie]kcontrol->Internet & Network->File Sharing
There you can add folders and change some options etc. Either thrue nfs or samba.

I do remember that on hoary(which is the computer I have at home but I can't check that now since I'm far away from it) you could right-click on a folder and go to the share-tab and manage everything from there. Don't know if it was the smb4k that did it or not. Anyway...use kcontrol otherwise.[/QUOTE]

I'm using Breezy so I'm not sure if that makes a difference. I'm aware of that feature. Unfortunately, even if I login as Admin, the fields are simply grayed out. Is this a bug or something?

---

### Post by Eazy© on 2005-12-28
Maybe you need to install "kdenetwork-filesharing" if you dont have it.

---

