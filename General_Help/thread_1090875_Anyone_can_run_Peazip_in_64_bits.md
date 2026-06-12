---
title: "Anyone can run Peazip in 64 bits?"
date: 2009-03-08
forum: General Help
---

### Post by UranUtan on 2009-03-08
Hi,

I was using Peazip [http://peazip.sourceforge.net/](http://peazip.sourceforge.net/) happily under Ubuntu x32. Now I run Ubuntu 8.10 64bits and it no longer start. Error = Could not launch menu item, Failed to execute child process, "peazip" (No such file or directory)

Anyone had successfully run Peazip in 64bits? If not, can you suggest an Archive Manager which can handle 7Zip and RAR format (and must run in 64 bits)

Thanks in advance

---

### Post by howefield on 2009-03-08
> **UranUtan said:**
> Hi,

I was using Peazip [http://peazip.sourceforge.net/](http://peazip.sourceforge.net/) happily under Ubuntu x32. Now I run Ubuntu 8.10 64bits and it no longer start. Error = Could not launch menu item, Failed to execute child process, "peazip" (No such file or directory)

Anyone had successfully run Peazip in 64bits? If not, can you suggest an Archive Manager which can handle 7Zip and RAR format (and must run in 64 bits)

Thanks in advance

Add 7zip and rar ability to file roller is the easy way.

Search for them in Synaptic Package Manager (rar / unrar / p7zip) if you don't have them, you might need to add the Medibuntu repository.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)


Or install peazip as per their webpage instructions for 64 bit.

* DEB package can be installed on 64 bit Linux using dpkg -i --force-architecture

---

### Post by UranUtan on 2009-03-08
> **howefield said:**
> 
* DEB package can be installed on 64 bit Linux using dpkg -i --force-architecture

NOT WORKING, which is the reason of this thread.

---

### Post by howefield on 2009-03-08
> **UranUtan said:**
> NOT WORKING, which is the reason of this thread.

Yeah I know, mind reading is not my strong suit.

---

### Post by bone2006 on 2009-03-22
Is it really that time consuming for the developers to come up with a 64bit release?  I did notice that the software is GNU at least at wikipedia


Anyway, this worked for me
sudo dpkg -i --force-architecture peazip_2.5.1.LINUX.GTK2-2_i386.deb

Wish they were in the repos and wish they had a 64bit release

---

### Post by UranUtan on 2009-04-05
> **bone2006 said:**
> 
Anyway, this worked for me
sudo dpkg -i --force-architecture peazip_2.5.1.LINUX.GTK2-2_i386.deb
Confirmed, just installed new version 2.51. Working now. I was using 2.50, may be there was an error in setting up the link to the executable in 64bits.

---

