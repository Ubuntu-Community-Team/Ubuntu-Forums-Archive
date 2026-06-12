---
title: "Ubuntu installation took all my space."
date: 2011-08-06
forum: Desktop Environments
---

### Post by astoit1323 on 2011-08-06
Hi there,
My Ubuntu 11.04 installation took all 40GB of my hard drive space on my laptop, can GParted make a partition for extra space and make the installation smaller??

---

### Post by omelette on 2011-08-06
Yes, Gparted will have no problem doing that.  Where it fails (miserably imo) is if you try doing something complicated - eg 2 partitions, shrink number 1, (first on disk) and grow number 2, it will spend ages copying then tell you it failed! This has happened to me on two occasions before wising up...

---

### Post by astoit1323 on 2011-08-06
Thanks very much, ill try that. Also, somehow my computer cant access the internet for some reason. Is there a fix to this??

---

### Post by astoit1323 on 2011-08-06
Also, GParted isn't already installed. Do i have to get it from the software center?

---

### Post by oboedad55 on 2011-08-06
Yes, GParted is in the software center or use synaptic. In order to help with the network stuff we need info about your network hardware.

---

### Post by astoit1323 on 2011-08-06
Ok I fixed the network issue, the updates just didn't finish correctly. But I am running synaptic now.

---

### Post by astoit1323 on 2011-08-06
OK is it GParted, or Gnome Partition Editor?

---

### Post by Hakunka-Matata on 2011-08-06
They are the same program, in synaptic search for GParted

---

### Post by astoit1323 on 2011-08-06
OK it is installing, and my laptop is running extremely slow right now.

---

### Post by astoit1323 on 2011-08-06
Alright, I'm in GParted. Here's the stats.

Partition:  Size:         Used:      Unused:    Flags:
 /dev/sda1  36.82GiB      3.32 GiB   33.50GiB   boot  
 /dev/sda2  444.00MiB
 ^/dev/sda5 444.00MiB

---

### Post by Hakunka-Matata on 2011-08-06
It appears you have one disk, of about 40GB. 

```
sudo fdisk -lu
```will show the drive information in another form.


Post those results so we can be sure of what possibilities you have available.

---

### Post by wildmanne39 on 2011-08-06
Hi, also you need to use the livecd to shrink partitions.

Here is a link you should read before you change partition size, it is a dangerous process always a good idea to back up your important files first.
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://ubuntuguide.org/wiki/Manipulating_Partitions](http://ubuntuguide.org/wiki/Manipulating_Partitions)

---

### Post by astoit1323 on 2011-08-13
Hey there guys, sorry about the very long delay. Unfortunately the computer is running a slow as a snail and i am trying to get it to run faster. Should I install Lubuntu as an alternative, due to the computer's low RAM space??

---

### Post by astoit1323 on 2011-08-13
Ok i am on my Ubuntu laptop and here is the results:


alex@alexlaptop:~$ sudo fdisk -lu
[sudo] password for alex: 

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002559c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    77228031    38612992   83  Linux
/dev/sda2        77230078    78139391      454657    5  Extended
/dev/sda5        77230080    78139391      454656   82  Linux swap / Solaris

---

### Post by oboedad55 on 2011-08-13
> **astoit1323 said:**
> Hey there guys, sorry about the very long delay. Unfortunately the computer is running a slow as a snail and i am trying to get it to run faster. Should I install Lubuntu as an alternative, due to the computer's low RAM space??

Please post your computer's specs. Yes, you can certainly run Lubuntu or Xubuntu which are lighter on resources than Gnome. Also Puppy Linux is a nice alternative.

---

### Post by astoit1323 on 2011-08-13
Heres the specs:

Specs:
HP Compaq nx9030
OS: Windows XP Professional, Ubuntu 11.04
Intel Pentium M Processor 1500MHz
599MHz 
RAM: 256MB

Sorry if thats not enough, i cant really find out more about it.

---

### Post by oboedad55 on 2011-08-13
> **astoit1323 said:**
> Heres the specs:

Specs:
HP Compaq nx9030
OS: Windows XP Professional, Ubuntu 11.04
Intel Pentium M Processor 1500MHz
599MHz 
RAM: 256MB

Sorry if thats not enough, i cant really find out more about it.

I wonder how well XP runs on that hardware. I would try the Ubuntu variants mentioned above as well as Puppy. I have much more recent hardware than that and 11.04 does not exactly scream. I went back to 10.04 LTS for that reason. I don't like Unity and my hardware apparently isn't sufficient for it to run well. I would give Puppy a try. It runs from the CD and only uses a small file that can be saved on your hard drive without affecting anything else. But you can run it without saving anything, will give you an idea about its performance.

---

### Post by astoit1323 on 2011-08-13
Well when i first tried to use Unity on the laptop, it could not handle it, so i have been using Ubuntu Classic instead, but it still runs extremely slow. I installed Lubuntu, and that runs like lightning! now I'm thinking about uninstalling Ubuntu and keeping Lubuntu.

---

### Post by oboedad55 on 2011-08-13
> **astoit1323 said:**
> Well when i first tried to use Unity on the laptop, it could not handle it, so i have been using Ubuntu Classic instead, but it still runs extremely slow. I installed Lubuntu, and that runs like lightning! now I'm thinking about uninstalling Ubuntu and keeping Lubuntu.

Great, sounds like a plan.

---

### Post by astoit1323 on 2011-08-13
> **oboedad55 said:**
> Great, sounds like a plan.

So, how do i do that?, is it just as simple as using ```
sudo apt-get remove ubuntu-desktop
```

---

### Post by oboedad55 on 2011-08-13
> **astoit1323 said:**
> So, how do i do that?, is it just as simple as using ```
sudo apt-get remove ubuntu-desktop
```

I believe that should get it done. I'm guessing you installed lxde after the regular 11.04 install? Failing that, you can download the Lubuntu iso and install it from that. You may wish to try xfce as well, I found no difference in in speed between the two.

---

### Post by astoit1323 on 2011-08-13
> **oboedad55 said:**
> I believe that should get it done. I'm guessing you installed lxde after the regular 11.04 install? Failing that, you can download the Lubuntu iso and install it from that. You may wish to try xfce as well, I found no difference in in speed between the two.

i installed lubuntu using:```
sudo apt-get install lubuntu-desktop
```

now it seems to be installed. so i am going to try and uninstall ubuntu, here we go.

---

### Post by astoit1323 on 2011-08-13
Ok after using the code, nothing happened.

---

