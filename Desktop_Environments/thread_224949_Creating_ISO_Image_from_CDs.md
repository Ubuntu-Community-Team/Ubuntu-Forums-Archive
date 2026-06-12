---
title: "Creating ISO Image from CDs"
date: 2006-07-28
forum: Desktop Environments
---

### Post by Keshyden on 2006-07-28
I have a need to create an ISO image file of my Windows XP CD for use in VMWare Server. I am having problems getting it to read from my drive. So I'd like to create an ISO and boot from that. Problem is I can't seem to find software that makes this simple. I don't want to run any scripts because it seems that these will not be bootable anyway.

Any help would be great!

Thanks. ;)

---

### Post by chavo on 2006-07-28
Just use dd ->

dd if=/dev/cdrom of=/path/to/WinXPcd.iso

Substitute the path to where you want the iso kept.

---

### Post by true_friend on 2007-01-12
i tried it but it says no such file or directory.
my cdrom in mounted at cdrom0

---

