---
title: "Windows 7 wiped my home directory ???"
date: 2009-03-20
forum: General Help
---

### Post by Tyconic on 2009-03-20
I've been hankering to try out windows 7 for a while after hearing really good things about it from friends, but only got to installing it today. Now I wish I hadn't :( 

I'm not sure how it happened, but my home directory, which is (was?) located on a logical partition inside extended partition /dev/sda3, and which was formatted as ext3, is now read as being "unallocated" by gparted. My Ubuntu install, located on primary partition /dev/sda2 seems to be fine and indeed I can mount it and navigate around inside. 

In case it matters 7 is currently located on /dev/sda4, which is a primary partion. Previously it was formatted as ext3 and had some junk files inside. I didn't format it as ntfs prior to installing and let the installer do so for me, which I realize now was probably the wrong decision :(

Please tell me there is some way to get my stuff back... 
oh and fschk windows

---

### Post by rbmorse on 2009-03-20
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Read the documentation on the Wiki.

---

### Post by davo11 on 2009-03-20
this kind of happened to me when i installed fedora
it would not let me access the other os so i had too wipe it completely
im not sure what to do here, but try to backup when installing a new os

---

### Post by Tyconic on 2009-03-21
@rbmorse

TestDisk worked perfectly :)

Cheers mate!

---

