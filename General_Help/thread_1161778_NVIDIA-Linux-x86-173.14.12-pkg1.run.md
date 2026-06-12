---
title: "NVIDIA-Linux-x86-173.14.12-pkg1.run"
date: 2009-05-17
forum: General Help
---

### Post by metricspace on 2009-05-17
Hi, I followed the instruction provided on [http://ubuntuforums.org/showthread.php?t=514161&highlight=install+nvidia](http://ubuntuforums.org/showthread.php?t=514161&highlight=install+nvidia) to manually install my nvidia drivers, after downloading 
NVIDIA-Linux-x86-173.14.12-pkg1.run (My mohterboard is ASUS p5N73AM, it has an inbuilt NVIDIA 610i/7050 graphic) from nvidia's website. 
 
I followed the instruction from [http://ubuntuforums.org/showthread.php?t=514161&highlight=install+nvidia](http://ubuntuforums.org/showthread.php?t=514161&highlight=install+nvidia)
 
after issuing the command
sudo sh ~NVIDIA-Linux-x86-173.14.12-pkg1.run
 
I was asked to accept the licence agreement, I accepted, and carried on 
I got the following msg
No precompiled kernel intereface was found to matching you kernel would you like the installer to attemtp to download a kernel interface for your kernel form NVIDIA ftp site ..
I selected yes, press enter 
got the msg.
No matchng precompiled kernel interface was found on NVIDIA ftp site
then 
builing kernel moddule 1% .......100% It went upto 100% and thrown this msg
ERROR: unable to build the NVIDIA kernel module
ERROR: intaller failed... 
and then it came back to command prompt
 
I've ubuntu 8.04 installed
 
Any help is greatly appreciated, wants this Nvidia drivers to be installed, please assist
 
Thanks a bunch,
metric

---

### Post by kpkeerthi on 2009-05-17
Any specific reason why you opted for manual install?

The recommended method is to install the driver from System -> Admin -> Hardware Drivers. Ubuntu should list the drivers available for your chipset and you should be able to 'Activate' it.

---

### Post by thegreenblob on 2009-05-17
By the error it seems like you might be missing build-essential or your kernel headers (or both).

Did you run:

```
sudo apt-get install linux-headers-$(uname -r) \
       build-essential pkg-config xorg-dev

```

from the tutorial you linked to?

---

### Post by metricspace on 2009-05-17
Thanks for the quick response,
 
Initially I tried thru System -> Admin -> Hardware Drivers. however I got the error, unable to activate the driver, you have held outdated packages ... , I've repaired the broken packages even then i got the same error.
 
yes following the instrction, I did issued 
```
sudo apt-get install linux-headers-$(uname -r) \
       build-essential pkg-config xorg-dev
```
 
something happend and then i was left on the command prompt with this line
```
build-essential pkg-config xorg-dev
```
 
Regards
metric

---

### Post by kpkeerthi on 2009-05-17
> **metricspace said:**
> Thanks for the quick response,
 
Initially I tried thru System -> Admin -> Hardware Drivers. however I got the error, unable to activate the driver, you have held outdated packages ... , I've repaired the broken packages even then i got the same error.
Is your system up-to-date?

---

### Post by metricspace on 2009-05-17
when I run 
```
sudo apt-get install linux-headers-$(uname -r) \
       build-essential pkg-config xorg-dev
``` in terminal, I got the following line on my terminal 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.27-7-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  binutils-static
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Please assist, what needs to be done

also now my system-administration ->Hardware Drivers window shows 
No proprietary drivers are in use on this system

Regards,
metric

---

### Post by kpkeerthi on 2009-05-17
[https://help.ubuntu.com/community/NvidiaManual]("https://help.ubuntu.com/community/NvidiaManual")

---

### Post by metricspace on 2009-05-17
> **kpkeerthi said:**
> [https://help.ubuntu.com/community/NvidiaManua](https://help.ubuntu.com/community/NvidiaManua)


Thanks for the link, I followed what is given at
[http://stringofthoughts.wordpress.com/2009/04/03/installing-nvidia-drivers-in-ubuntu/](http://stringofthoughts.wordpress.com/2009/04/03/installing-nvidia-drivers-in-ubuntu/)

however opting yes to compile the kernel, I got the following error

ERROR: Unable to build ther NVIDIA Kernel module

before installing the drivers i even installed linux-source as given the link and the gcc compiler, still I got the above err.

any help for getting this NVIDIA drivers installed is really appreciated.

Thanks for all your responses,

Regards,
metric

---

### Post by oldos2er on 2009-05-17
Do you have source code repositories enabled? In Gnome, check System, Administration, Software Sources, tick the box next to Source Code.

---

### Post by metricspace on 2009-05-17
[SIZE=2]Hi
[/SIZE]
[SIZE=2]I tried NVIDIA-Linux-x86-180.51-pkg1.run and the drivers got installed in a jiffy. This comment am writing from my linux box, with NVIDIA drivers installed.[/SIZE]


[SIZE=2]This link helped me 
[/SIZE]
[SIZE=2]http://stringofthoughts.wordpress.com/2009/04/03/installing-nvidia-drivers-in-ubuntu/#comment-33
[/SIZE]
[SIZE=2]
[/SIZE]
[SIZE=2]
[/SIZE]
 [SIZE=2]
[/SIZE]
[SIZE=2]Thank you all of you for devoting your valuable time,
metric[/SIZE]

---

