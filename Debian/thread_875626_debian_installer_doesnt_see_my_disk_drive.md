---
title: "debian installer doesnt see my disk drive"
date: 2008-07-31
forum: Debian
---

### Post by SteveNorman on 2008-07-31
While installing debian doesnt see my hard drive(s), and I therefore cannot partition it. I have 2 seagate barracuda drives, one with ubuntu and xp, the other blank and unformatted. They both come up in gparted, sda and sdb. It askes for drivers,and I have no idea what the driver name is. I couldnt find any driver names anywhere. I tried generic and a few others to no avail. Has anyone else encountered this? I had no problems at all putting ubuntu on sda. 

both are seagate barracuda sata, one 250 and the other 500 mb

---

### Post by basenvironment on 2008-07-31
which debian version are you trying?

---

### Post by SteveNorman on 2008-07-31
Latest,,4.0r3 etch, i386

---

### Post by basenvironment on 2008-07-31
actually r4 is the latest...

Are you getting a error message? If so, what is it?

You say they come up in gparted? What are you running gparted from?

You might want to try the etch-n-half ISO which has a updated kernel and so forth. I think etch-n-half is only a netinst image which will only install the base system from the CD and the rest would be downloaded. 

You might also want to try the weekly **testing** images 
[http://cdimage.debian.org/cdimage/weekly-builds/](http://cdimage.debian.org/cdimage/weekly-builds/)
or the beta2 build
[http://www.debian.org/devel/debian-installer/](http://www.debian.org/devel/debian-installer/)

---

### Post by SteveNorman on 2008-07-31
wasnt an error message,,just said no disk drive detected,,please pick a driver from the list. When I tried to continue it said nothing there to format. I used gparted from a live disk, and from ubuntu. Both drives show up accurately. It looks like debian wants a driver for the HD, and I have no idea which driver I need for these.

---

### Post by Bachstelze on 2008-08-02
Actually, it is not a driver for the HD that is needed, but a driver for the ATA chipset of your motherboard. Those drivers are generally included in the kernel, so it the reason the Debian installer cannot "see" your drives is most likely that the kernel it uses is too old, and does not include the driver you need.

So you have three options here:

1. Modify the installer so that it uses a more recent kernel (e.g. the same version Ubuntu uses, since it sees you drives properly). There are guides about this, but it's quite bothersome, and generally not worth the hassle.

2. Go with Debian testing or unstable, which might contain a more recent kernel. Unless you're running a production-critical server, you don't want to stick with stable anyway.

3. Forget Debian for now, stick with Ubuntu and wait for Lenny to be released.

---

### Post by polmir on 2008-08-03
Try installing from debootstrap.

[http://rimuhosting.com/knowledgebase/linux/misc/installing-debian-or-ubuntu-using-debootstrap]("http://rimuhosting.com/knowledgebase/linux/misc/installing-debian-or-ubuntu-using-debootstrap")
[http://www.cs278.org/blog/ubuntu-configuration/feisty-debootstrap-encrypted-install/]("http://www.cs278.org/blog/ubuntu-configuration/feisty-debootstrap-encrypted-install/")

---

