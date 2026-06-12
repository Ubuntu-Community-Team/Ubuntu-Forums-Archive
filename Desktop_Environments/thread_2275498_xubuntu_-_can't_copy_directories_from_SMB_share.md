---
title: "xubuntu - can't copy directories from SMB share??"
date: 2015-04-26
forum: Desktop Environments
---

### Post by wood_e on 2015-04-26
Hi there - I can't seem to copy directories from my Mac to my xubuntu PC over SMB. I'm running 14.04 - just installed it last night on a new PC build.

I can copy individual files just fine, but when it comes to directories I get a dialogue box saying "Is a directory, do you want to replace it?" And my options are Retry, Yes to All, Yes, and Cancel.

None of those options seems to do anything except place a file of zero bytes in my location with the name of the folder.

It's very strange, and quite annoying since I'm going to use this as my primary machine.

Anyone have any ideas??

---

### Post by Morbius1 on 2015-04-26
That be a bug:
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/458003](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/458003)
[https://bugzilla.samba.org/show_bug.cgi?id=10587](https://bugzilla.samba.org/show_bug.cgi?id=10587)

It was fixed in 14.10 but that doesn't do you or I any good.

A workaround:

Create a zip (  Compress ) in OSX so that it adds a XXX.zip of the directory and copy that.

Or you can mount the OSX SMB share manually and then it works as it appears to be a gvfs error in Linux.

---

### Post by wood_e on 2015-04-26
haha I thought I was going crazy! Glad it's not just me :)

Thanks Morbius!

EDIT: I'm having good success the other way around - copying to my xubuntu box via SMB from the mac.

---

