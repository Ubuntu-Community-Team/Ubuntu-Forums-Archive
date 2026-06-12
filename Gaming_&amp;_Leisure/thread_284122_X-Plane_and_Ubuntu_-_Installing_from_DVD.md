---
title: "X-Plane and Ubuntu - Installing from DVD"
date: 2006-10-25
forum: Gaming &amp; Leisure
---

### Post by wehttam67 on 2006-10-25
Hello all,

I'm new to linux and I've been having a good look around to find out what I need to do to get X-Plane up and running but at the moment I'm having trouble getting past step one.

I've got the DVD installer from [here.]("http://dev.x-plane.com/installer/1.14/") I've modified its permissions so it's exceutable. 
With the X-Plane DVD in one of my drives with a device name of */dev/hda* and which Ubuntu seems to have mounted as */media/cdrom0* I run the installer and get the following error message...> DVD scan: The installer cannont extract a file

Error:We were unable to open a zip file. It may be missing or damaged

Compressed File:Not Yet Scanned/directory.txt.zip

Destination Path:/tmp/

(main.cpp line 210)

So I "googled" it and came up with this suggestion detailed here...
[http://forums.x-plane.org/lofiversion/index.php?t22062.html](http://forums.x-plane.org/lofiversion/index.php?t22062.html)

this is what I end up with trying that suggestion...
> *****@*****-desktop:~$ sudo mount -t udf /dev/hda /media/cdrom0
mount: block device /dev/hda is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


What is this telling me?

Can someone who has perhaps gone through the process of getting X-Plane up and running give me a hand. I think Open GL should be working after following "Method 1" here -
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

Cheers,
Matt

---

