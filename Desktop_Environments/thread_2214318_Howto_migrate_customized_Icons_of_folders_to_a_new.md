---
title: "Howto migrate customized Icons of folders to a new system"
date: 2014-03-31
forum: Desktop Environments
---

### Post by RainerEL on 2014-03-31
Hi together,   I are on the way to migrate from 32-bit tu 64-bit Ubuntu. I have 3 partitions 1: new 64-bit Ubuntu 2: old32-bit Ubuntu 3: my data.   Under the 32-bit system I had have a lot of folders and files where I have been changed the icons using preferences to my gust. Now under the 64-bit system I see only the standard icons not my preferred user icons. I googled a lot but find no hint.    Where are the user icons of modified files and folder are stored? Then I can try to find a way to copy the preferrences to the 64-bit system. Or exist a procedure to do so?    Thanks in advance Rainer .

---

### Post by trag on 2014-03-31
Download ' Aptik ' an use it to put your stuff on a usb, than transfer off the usb onto the Distro of your choice

---

### Post by RainerEL on 2014-03-31
Thanks,

I take a look at APTIK, but it only supports PPA and APP. 

I'm looking for my icon changes, mainly at the "Data" partition.

Any hinst for that?

---

### Post by trag on 2014-03-31
Try this,go to help.ubuntu.com/community/Partitioning/Home/Moving. Basically your putting your stuff into a home folder and putting it on a seperate partition and then migrating it all to the desired OS.

---

### Post by RainerEL on 2014-04-01
This doesn't help.

Thes problem is not my HOME. The Problem is my DATA. To understand what I mean:

Use a ext disk with some Folders and files on a 32-bit system with name A. Go in Nautilus to the ext disk. Klick right mouse on a folder, select Proterties, klick on the folder icon and now select a private user icon. Now you see this folder always with your private user icon (not more the standard folder icon). Now go to an other system und take a look at the ext disk. You see now the standard folder icon, not the wanted private user icon.

This is my problem. I have over 100 folder and files modified with user icons and now under the new 64-bit system I see only the standard folders. The question is: where are this properties are stored?

---

### Post by RainerEL on 2014-04-02
Hello

I found the problem by my self. [SIZE=4]**Problem solved**[/SIZE] for me

Here are how it works:

All icon references are stored in ~/.local/share/gvfs-metadata . I copied home and UIDD-[uidd of my disk] and those user Icons appear after an re-login

Hope this help other how have the same migration problem.:D

---

