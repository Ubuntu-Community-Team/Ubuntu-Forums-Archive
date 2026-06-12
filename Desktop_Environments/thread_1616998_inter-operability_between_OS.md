---
title: "inter-operability between OS"
date: 2010-11-08
forum: Desktop Environments
---

### Post by AM_SOS on 2010-11-08
hi ,
can someone please explain how different OS interact with each other, or if this is possible at all.
e.g. assume i am running only ubuntu on a comp. now i have saved various files such as openoffice, basic text documents, movies etc.
so if can i open them straightaway in mac or windows OS ?
i mean the filing system are all different, right ?
e.g. ext4, ntfs, and whatever mac uses.

also if i have lots of data saved on a mac, can i simply transfer this on to an ubuntu or windows OS ?

thanks!

---

### Post by cipherboy_loc on 2010-11-08
If you get a NAS (like the Dlink 323 [http://www.dlink.com/products/?pid=509](http://www.dlink.com/products/?pid=509)), you can put all your documents on a ftp or SMB share, and share between your computers. You cannot boot your computers (easily that is) from it, but you can if you really want to.


Cipherboy

---

### Post by Cheesehead on 2010-11-08
You are talking about two different types of compatibility.

First, FILESYSTEMS. Linux uses ext3 ot ext4 or a variety of others. Windows uses NTFS. Mac uses HFS+. Some systems can read different filesystems. Ubuntu, for example, has packages to read NTFS and HFS+ disks. Most systems also work with vFAT, a much older (Windows pre-NTFS) filesystem that can be recognized by just about everyone.

Most small USB stick drives are vFAT and work equally well on Linux, Windows, and Mac. So you can save a file (foo.doc) from one, and the others will recognize it.  CDs/DVDs also use filesystems that are universally recognized. In the past, advice has been to steer clear of large NTFS-formatted external USB drives if you're moving data to/from Linux systems.


Next, FILES. Microsoft Word doesn't run on Linux. But there are many applications that open and save .doc files. An OpenOffice .odt should look identical if saved and reopened on another platform. Movies play great in Linux.

You really should simply download a LiveCD ([http://www.ubuntu.com/download]("http://www.ubuntu.com/download")) and simply try some of these things. It's free and easier than describing them.

---

