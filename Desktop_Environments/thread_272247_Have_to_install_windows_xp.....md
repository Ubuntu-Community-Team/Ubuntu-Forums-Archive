---
title: "Have to install windows xp...."
date: 2006-10-05
forum: Desktop Environments
---

### Post by Jerrac on 2006-10-05
Ok, for school I need to install windows xp pro on my computer. So I partition 20 gigs off as fat32, boot the disc, and it will not detect my partions correctly. Basically, if my free space is fat32 or ntfs, it says there is a huge 131072 partiton. Pressing c like it says to partition the free space does not do anything. If I just delete the partion and leave it free, it will detect my three linux partions. It's like windows can't detect that my hard drive is bigger that that... 

Any suggestions? Other than not installing it... :D

---

### Post by pay on 2006-10-06
Install vmware server or kqemu and then install it into that.

---

### Post by guysmiley25 on 2006-10-06
Installing Windows after linux can be a paint but I have done it before. I'm going of memory here so yeah.

I think I used pqmagic alot. How ever you do have to buy it.

I think what I did is booted to a pqmajic disc created my partition and formated it. and then seleted hide for the other partitions.

I think that should work, at least for installing XP. Now the problem is resoring GRUB so you can boot to XP and linux.

I use XOSL Extended Operating System Loader. I have it set up to boot Windows 98 and XP and xubuntu.

It quite cool with a really cool interface and easy to setup. However when installing it if you chose to do so install it to a partition. first before you try and install windows XP. Just use pqmagic or somting like it to make a partition as small as you can.

Install it then set it up to boot you linux OS first.

Then install windows XP. should be all good but now XOSL wont boot. but thats ok you can run the setup again to restore it. do that.

now add another boot entry for XP and should be all good.

By the way to set it up to book your linux OS tell it to boot the oringal boot record.

That should work. Any questions just Ask

---

### Post by x64Jimbo on 2006-10-06
> **pay said:**
> Install vmware server or kqemu and then install it into that.
Gonna have to agree here. VMWare is nearly native in its speed, and it even supports USB passthrough.

---

### Post by Jerrac on 2006-10-06
> **guysmiley25 said:**
> Installing Windows after linux can be a paint but I have done it before. I'm going of memory here so yeah.

I think I used pqmagic alot. How ever you do have to buy it.

I think what I did is booted to a pqmajic disc created my partition and formated it. and then seleted hide for the other partitions.

I think that should work, at least for installing XP. Now the problem is resoring GRUB so you can boot to XP and linux.

I use XOSL Extended Operating System Loader. I have it set up to boot Windows 98 and XP and xubuntu.

It quite cool with a really cool interface and easy to setup. However when installing it if you chose to do so install it to a partition. first before you try and install windows XP. Just use pqmagic or somting like it to make a partition as small as you can.

Install it then set it up to boot you linux OS first.

Then install windows XP. should be all good but now XOSL wont boot. but thats ok you can run the setup again to restore it. do that.

now add another boot entry for XP and should be all good.

By the way to set it up to book your linux OS tell it to boot the oringal boot record.

That should work. Any questions just Ask
What do you mean "hide" the other partitions? Would partition magic have asimilar feature?

As for vmware and kemu, vmware is way to expensive, and I want to have the full capabilites of my hardware availible. I figure that if I have to have windows on my computer I will take advantage of it for some gaming that cedega won't do.

---

### Post by indytim on 2006-10-06
I did this a couple of weeks ago.  My process was:

Using GParted Live:

1.  Booted into GParted.
2.  Took my windows partition and had GParted reformat it to NTFS.
3.  Re-Booted with the Windows install disc.
4.  Directed windows to install only on the partition referenced in #2.
5.  Waited hours-upon-hours as I re-built Windows (have 1 app that I absolutely need and it won't run in Wine).

Hope this helps.

IndyTim

---

### Post by arolopez on 2006-12-08
I did the same, but the problem is still given me no peace. I mean after i create the ntfs partition with the BOOT flag or without the BOOT flag, when i reboot whit the windows install disc. This one can't find any disc on my system. What can i do? Other strange thing is that my bios not detect my hard disk, but when i boot from my ubuntu partition it work all right...

please, help me!
sk!

---

### Post by igknighted on 2006-12-08
> **Jerrac said:**
> What do you mean "hide" the other partitions? Would partition magic have asimilar feature?

As for vmware and kemu, vmware is way to expensive, and I want to have the full capabilites of my hardware availible. I figure that if I have to have windows on my computer I will take advantage of it for some gaming that cedega won't do.

I know this is old, but VMWare is free... so I'm not sure what you mean here.  Also you could try Xen, I like it better.

---

### Post by coachsd on 2007-10-01
> **igknighted said:**
> I know this is old, but VMWare is free... so I'm not sure what you mean here.  Also you could try Xen, I like it better.

VMWare has a free trial, but it's not free... unless I'm missing something... can you tell me how to get a free version? Download on website says $189

Thanks

---

### Post by maybeway36 on 2007-10-01
[http://www.virtualbox.org]("http://www.virtualbox.org")

---

### Post by ninja1990 on 2007-10-01
This will take a bit of work, but it can be done.  Most important thing is to save your data.  Grab VMWare Server.  It's free.  VMWare's other products, with the exception of VMWare Player are not free.  I don't even know what happend to VMWare Player.

---

### Post by idkwot on 2007-10-01
what did ever happen to vmware player?

---

### Post by zaphod777 on 2007-10-02
it is there just hidding. I recomend virtual box it works great just be advised of one thg you need to add the following permissions after you install:

in the example greg is the username:

sudo groupadd vboxusers 
sudo usermod -G vboxusers -a greg 
Now we must change the permissions of /dev/vboxdrv so that it can be accessed by the vboxusers group: 

sudo chmod 660 /dev/vboxdrv 
sudo chgrp vboxusers /dev/vboxdrv 
In order to prevent the permissions from being reset every re-boot, we must edit /etc/udev/rules.d/40-permissions.rules to add a line to the end of that file; so: 

sudo gedit /etc/udev/rules.d/40-permissions.rules 
then in the opened file: 
[...] 
KERNEL==”vboxdrv”, GROUP=”vboxusers”, MODE=”0660” 
and save the file and exit. 
Now you have to re-boot the computer for all this crap to take effect."

---

### Post by tech9 on 2007-10-02
> **maybeway36 said:**
> [http://www.virtualbox.org]("http://www.virtualbox.org")

seconded .... virtual box works flawlessly

---

