---
title: "Dell PowerEdge 2900 Ubuntu Desktop 8.04 installation failure"
date: 2009-04-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by niaf on 2009-04-22
Hello,
I'm trying to install Ubuntu 8.04.2 LTS Desktop on a Dell PowerEdge 2900.
I boot the server on the live CD, choose the language then select the option to install Ubuntu.
The Ubuntu splash screen is displayed with the progress bar and suddenly I get the following error messages:

ata_id[xxxx]: main: HDIO_GET_IDENTITY failed for '/dev/.tmp-8-0'
ata_id[xxxx]: main: HDIO_GET_IDENTITY failed for '/dev/.tmp-16-0'
ata_id[xxxx]: main: HDIO_GET_IDENTITY failed for '/dev/.tmp-32-0'

and the installation process is stopped.
Here is my Dell PowerEdge 2900 hardware configuration:
PE 2900 III Quad Core Xeon E5430 (2.66GHz, 2x6MB, 1333MHz FSB)
RAM: 16GB (4x4GB Dual Rank DIMMs) 667MHz FBD
Hard disks: 1x160GB Serial ATAu 7.2k 3.5" HD Hot Plug
            2x1TB Serial ATAu 7.2k 3.5" HD Hot Plug
SAS 6i/R Internal Controller Card RAID
16X DVD-ROM Drive SATA

I have seen on the following URL that the Dell PowerEdge 2900 is compatible with Ubuntu 8.04 LTS:
[http://webapps.ubuntu.com/certification/list/?category=Server]("http://webapps.ubuntu.com/certification/list/?category=Server")

Can someone help me?

---

### Post by stilling on 2009-04-22
but what type of ubuntu 8.04 you downloaded is it 64 bits or i386 that means 32 bits ...
and that can be your problem
hope it helps

---

### Post by tomvietdungvn on 2009-04-22
> **stilling said:**
> but what type of ubuntu 8.04 you downloaded is it 64 bits or i386 that means 32 bits ...
and that can be your problem
hope it helps

I also have Dell power edge 7500.I do not know,it can run Ubuntu Server 8.4 LTS?please help me too

---

### Post by stilling on 2009-04-23
> **tomvietdungvn said:**
> I also have Dell power edge 7500.I do not know,it can run Ubuntu Server 8.4 LTS?please help me too

your hardware configuration is ?
don`t feel defended thank you.

---

### Post by Technoviking on 2009-04-23
On my Dell PowerEdge 2950, I have to update the firmware raid controller card to Ubuntu Hardy or new on the box.

T-V

---

