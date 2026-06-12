---
title: "How to clone my ubuntu installation?"
date: 2009-03-18
forum: General Help
---

### Post by tarekeldeeb on 2009-03-18
Hello all,

I have a lab with: 1 server-pc, 10 user-pc

The server provides: dhcp, gateway,file sharing, svn ..[running fedora]

I want to switch the other 10 from windows to ubuntu, I started with 1 PC, installed ubuntu and all tools, packages and settings. Now I want to clone this PC to the other 9.

I found a [HowTo]("http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html") use the remastersys tool to clone/backup a system into a live bootable ISO.

The problem is that the installation is >10GB, and I cannot burn it to any media(CD/DVD).

Can you suggest a solution?

I thought about using the server-pc as an ftp to provide network boot .. can the remastersys iso be used with a PXE (network boot) ?

Any clue about that last point? a HowTo ?

Thanks in advance,

Tarek

---

### Post by JECHO on 2009-03-18
> **tarekeldeeb said:**
> Hello all,

I have a lab with: 1 server-pc, 10 user-pc

The server provides: dhcp, gateway,file sharing, svn ..[running fedora]

I want to switch the other 10 from windows to ubuntu, I started with 1 PC, installed ubuntu and all tools, packages and settings. Now I want to clone this PC to the other 9.

I found a [HowTo]("http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html") use the remastersys tool to clone/backup a system into a live bootable ISO.

The problem is that the installation is >10GB, and I cannot burn it to any media(CD/DVD).




Can you suggest a solution?

I thought about using the server-pc as an ftp to provide network boot .. can the remastersys iso be used with a PXE (network boot) ?

Any clue about that last point? a HowTo ?

Thanks in advance,

Tarek



That tutorial you found on ubuntugeek is excellent, its the same one I used...

If youre using Ubuntu 8.10 it has a great GUI based "Create USB Start-Up disk" tool built into it... System > Administration > Create USB Startup Disk...

create an iso with remastersys and go get yourself a 10gig thumb drive and use that software to make it bootable with your custom ubuntu image.

install ubuntu on your machines with that thumb drive and youre set :D

---

### Post by tarekeldeeb on 2009-03-18
> **JECHO said:**
> That tutorial you found on ubuntugeek is excellent, its the same one I used...

If youre using Ubuntu 8.10 it has a great GUI based "Create USB Start-Up disk" tool built into it... System > Administration > Create USB Startup Disk...

create an iso with remastersys and go get yourself a 10gig thumb drive and use that software to make it bootable with your custom ubuntu image.

install ubuntu on your machines with that thumb drive and youre set :D

Great idea .. !!
Fool me, I missed this.

But I found a more interesting HowTO:
[Setting Up A PXE Install Server For Multiple Linux Distributions]("http://www.howtoforge.com/ubuntu_pxe_install_server")

.. this even gives many ISOs as options to boot from :D
but the job does not seem simple :(

Salam

---

### Post by JECHO on 2009-03-18
> **tarekeldeeb said:**
> Great idea .. !!
Fool me, I missed this.

But I found a more interesting HowTO:
[Setting Up A PXE Install Server For Multiple Linux Distributions]("http://www.howtoforge.com/ubuntu_pxe_install_server")

.. this even gives many ISOs as options to boot from :D
but the job does not seem simple :(

Salam

yeah that howto looks pretty good!

its up to you, the PXE does seem a little complicated for what you need it for.

---

### Post by ugm6hr on 2009-03-18
I haven't thought this through completely, but it occured to me that if your workstations are identical, you could use partimage to backup the installation on to the server, and then share that directory with partimage, and then restore it on the other 9.

[http://www.partimage.org/Partimage-manual_Network-support](http://www.partimage.org/Partimage-manual_Network-support)

This would also mean that you could easily restore the setup in the future (on the same machines).

---

### Post by nelskurian on 2009-03-18
Thanks for the whole information...before that i think their is only one option..thats
dd if=/dev/sda of=dev/sdb like that.It simply copies the whole data..but its time condsuming..But the hard disk must be identical

---

### Post by DeMus on 2009-03-18
> **nelskurian said:**
> Thanks for the whole information...before that i think their is only one option..thats
dd if=/dev/sda of=dev/sdb like that.It simply copies the whole data..but its time condsuming..But the hard disk must be identical

I'm just wondering about the hardware in all the PC's. Does it have to be the same in all computers, regarding the drivers. Or will Ubuntu install the right drivers the first time it is booting?

---

### Post by nelskurian on 2009-03-18
> **DeMus said:**
> I'm just wondering about the hardware in all the PC's. Does it have to be the same in all computers, regarding the drivers. Or will Ubuntu install the right drivers the first time it is booting?

dd if=/dev/sda bs=1024k dd of=/dev/sdb
Actually we clone the disk through this.But for that all the system hardwares must be identical.

just try the below link for the other enough options
[http://ubuntuforums.org/showthread.php?t=127995]("http://ubuntuforums.org/showthread.php?t=127995")

---

### Post by lisati on 2009-03-18
No-one mentioned [remastersys]("http://www.geekconnection.org/remastersys/remastersystool.html")?

---

### Post by ugm6hr on 2009-03-18
> **nelskurian said:**
> dd if=/dev/sda bs=1024k dd of=/dev/sdb
Actually we clone the disk through this.But for that all the system hardwares must be identical.

You could probably reconfigure each system with dpkg-reconfigure xserver-xorg from Recovery Terminal.

---

### Post by tarekeldeeb on 2009-03-19
> **lisati said:**
> No-one mentioned [remastersys]("http://www.geekconnection.org/remastersys/remastersystool.html")?

I did, in the first post;)
The problem is with the huge iso (>10GB)


As for cloning partitions:
- In my case, the HW is the same.
- But generally speaking, the live remastersys is the optimal solution.
- You clone users, their settings, passwords .. which is not preferable.

---

