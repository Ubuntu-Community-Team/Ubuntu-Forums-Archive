---
title: "Won't automount filesystems on SATA disk"
date: 2010-04-26
forum: Desktop Environments
---

### Post by pksings on 2010-04-26
Help please!


I have a newly built system that is booting from an SSD disk that will not automount /home, it stops every time complaining that it is not available and requires a drop to the shell to mount the filesystem and then will come the rest of the way up. /home is on /dev/sdb2. Once I have dropped to the shell mount -a works just fine however.

What can I change to make it wait until the disk that /home is on is available? It appears to just be booting so fast that it just isn't ready yet. I am thinking an 'if exist' loop somewhere should do it, I just don't know where to put it.

Thank you very much in advance.

PK

I gave up and upgraded to 10.04, works like a champ.

---

### Post by Fedia on 2010-04-27
I'm having the same issue.....

I've installed a new SATA hard drive and it does not automount. I've found the Disk Mounter applet very useful for mounting it quickly, but it still asks for the password to mount it every time.

---

