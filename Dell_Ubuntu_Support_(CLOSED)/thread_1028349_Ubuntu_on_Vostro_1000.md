---
title: "Ubuntu on Vostro 1000"
date: 2009-01-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Hefnawy on 2009-01-02
Alright, I'm a LITTLE new at this, so please take it easy on me :)
Right now, I have a Dell Vostro 1000 with an AMD Athlon X2 processor, and I've just started using ubuntu (well, pretty much anything besides mac and windows). I've got a few questions:

1. Drivers! What about the drivers for VGA, Storage, WiFi, Sound, etc. ? You still have to install them, don't you?

2. How do you partition your hard disk?

3. Where IS that process list?


I have a few more, but those will do for now. :) Thanks

---

### Post by __Ryan__ on 2009-01-02
First of all welcome!

1. Drivers for most everything should be working automatically, hardware support is very robust these days.

2. You can let the installer chosse the partition setup for you. Usually a swap partition the size of your RAM footprint,  as well as a root partition.

3. Not sure what you mean by process list. Is this what you mean?

```
System -> Administration -> System Monitor
```

Good luck

---

### Post by BenAshton24 on 2009-01-02
Ubuntu comes with most of the drivers installed already... sound and graphics will probably work out of the box.. but wifi is a bit more "meh" if u know what i mean :P however i have found ubuntu to be pretty amazing with wifi support so you should have no trouble with that. If you get wifi using the live cd then you will be able to get wifi once you have installed it. Partitioning is fairly simple but the ubuntu installer can do it all for you anyway.. just select use entire disk (providing you don't have anything that you want to keep on the drive) and i'm not sure what you mean by process list but i figure you mean running processes?? if so just press Alt-F2 and type "gnome-system-monitor" (without the quotes)

Hope this helps XD

---

### Post by Hefnawy on 2009-01-02
Ryan:

Thanks a lot for the help. Yes, hehe I've spent over 5 hours trying to find the processes tab in the system monitor launcher you mentioned. Thanks :)

Ben:

As for wireless, it's currently working perfectly fine, which is why I was getting rather confused. With windows, I had to install every single driver for the laptop (including wifi), so...I just thought I would have to do the same with ubuntu. 

However, the sound sometimes doesn't work for some reason. I have to restart to make it work...any suggestions why that's happening?

---

### Post by epitaph on 2009-01-02
Greetings. I have Ubuntu 8.04 LTS 64-bit on my Dell Vostro 1000.

It appears you already have the wireless working, which means you're probably already using b43-fwcutter. I would also consider using the fglrx driver for accelerated 3D on the integrated ATi 1150 Xpress.

With respect to sound: I don't get this often, but sometimes the sound simply stops working (maybe once a week or so?). When this happens I restart ALSA:

```
sudo /etc/init.d/alsa-utils restart
```

Sound then returns.

Are your Fn keys working properly? Are you using 8.10 or 8.04? Glad to hear things are going decently well. Took me a few weeks to get issues ironed out on my laptop, but that was awhile back.

---

### Post by Hefnawy on 2009-01-02
Well, I installed Ubuntu 8.04 LTS, but then NOW it says in the system information that it was upgraded to 8.10 (intrepid).
The sound's working FAIRLY well for now, I guess. 

hehe..i know i'm going to sound VERY stupid (apologies), but...where exactly do you post those commands and codes (like the one you included)? I'm very confused. Also, where can i get the fglrx driver?

---

### Post by epitaph on 2009-01-02
No, you don't sound stupid. Everyone has to start learning something at some point, no one just knows it.

Good to know that the upgrade path to 8.10 from 8.04.1 on the Vostro 1000 will probably work for me without too many issues.

The command I posted is typed or pasted into a terminal. The terminal can be found by going to Application > Accessories > Terminal. The command will prompt you for your password.

The fglrx driver is typically enabled in the System > Administration > Hardware Drivers manager. In this menu on my Vostro 1000 I see the ATi driver (fglrx) and the Broadcom one for wireless (b43-fwcutter).

Try using the fglrxinfo command in a terminal (Once again, go to Applications > Accessories > Terminal):

```
fglrxinfo
```

If the drivers are working properly and you have hardware 3D acceleration working you should be able to do things like use a composited desktop (System > Preferences > Appearance then go to the "Visual Effects" tab and select either "normal" or "extra") and run OpenGL applications such as glxgears.

```
glxgears
```

I've gotten nearly everything to work properly on my Vostro 1000, so if you run into any issues let me know. There's a decent chance I may have run into it and found a workaround.

**EDIT**

It just occurred to me that not all of the Vostro 1000's may be identical. I'm not sure, but I think some may not have ATi IGP's in them. To determine what kind of VGA controller you have issue the following in a terminal:

```
lspci | grep VGA
```

---

### Post by Hefnawy on 2009-01-02
Perfect. both drivers are working properly (i just had to activate the ATI driver). Right now, the visual effects are set on extra and are working perfectly well.
Thanks a lot, I really appreciate it.
One more thing! (sorry for the disturbance :$ )
The thing is...I used to have Windows XP Pro installed. Usually, you'd have your system files stored on the C drive, and everything else on another partition.
When I installed ubuntu, it either couldn't read the other partition, or it just formatted it anyway and combined both into one large partition. I need to know what happened, and if i could retrieve (if the D partition was in fact formatted) those lost contents. 
Is that even possible?

---

### Post by epitaph on 2009-01-02
Copy and paste the output of the following command:

```
sudo fdisk -l
```

This will give a lot of information on the setup you have for your hard drive(s) and partitions.

Unfortunately, if you told Ubuntu to "Use entire disk" when you installed it, it's unlikely that much of the data is recoverable. To most easily create a dual-boot of Windows and Ubuntu Windows is usually installed first on part of the drive (or if it is already installed, shrinking its partition to have free space on the hard disk). Then Ubuntu is installed to the unused space on the hard disk.

If you selected the option for Ubuntu to "Use free space" then your NTFS partition *should* still exist and is usually easily accessible by going to the Places menu and selecting it from the list of accessible partitions under the folder bookmarks.

If you post the output of that command we can see what partitions are still on the drive. If it was formatted, there is not much hope, but that's beyond the scope of my experience.

---

### Post by Hefnawy on 2009-01-02
Perfect. both drivers are working properly (i just had to activate the ATI driver). Right now, the visual effects are set on extra and are working perfectly well.
Thanks a lot, I really appreciate it.
One more thing! (sorry for the disturbance :$ )
The thing is...I used to have Windows XP Pro installed. Usually, you'd have your system files stored on the C drive, and everything else on another partition.
When I installed ubuntu, it either couldn't read the other partition, or it just formatted it anyway and combined both into one large partition. I need to know what happened, and if i could retrieve (if the D partition was in fact formatted) those lost contents. 
Is that even possible?

---

### Post by epitaph on 2009-01-02
Is there a reason you've pasted the same text as in your previous post? A mistake, I presume.

---

### Post by Hefnawy on 2009-01-03
Sorry about that extra post, my bad.

Alright, so, here's what came up when i used the sudo fdisk command:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19128   153645628+  83  Linux
/dev/sda2           19129       19457     2642692+   5  Extended
/dev/sda5           19129       19457     2642661   82  Linux swap / Solaris



...? *confusion*

---

### Post by albinootje on 2009-01-03
> **Hefnawy said:**
> 
/dev/sda1   *           1       19128   153645628+  83  Linux
/dev/sda2           19129       19457     2642692+   5  Extended
/dev/sda5           19129       19457     2642661   82  Linux swap / Solaris

Linux has your whole disk in use, so you've made a mistake during the installation and wiped the MS-Windows partition.

You have backups ?

---

### Post by Hefnawy on 2009-01-03
Ouch!

No, I don't...but I've heard from someone (He could and probably is lying, but i thought i'd make sure) that you can still retieve formatted data, somehow...

---

### Post by albinootje on 2009-01-03
> **Hefnawy said:**
> Ouch!

No, I don't...but I've heard from someone (He could and probably is lying, but i thought i'd make sure) that you can still retieve formatted data, somehow...

Sorry to tell you, but I cannot give you much hope here.
Making regular backups is very important.
Hard disks (and also backup disks) can die unexpectedly etc.etc.

Have a look here :
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by epitaph on 2009-01-03
Yeah, I'm sorry to say but it appears that you cleared the whole drive out when you installed Ubuntu. Since your file system was changed from NTFS to ext3 it probably did more than a quick format. The chances of getting data back aren't good. There are probably people who know much more about this and may be able to provide some further insight.

---

### Post by Hefnawy on 2009-01-03
TestDisk worked!!!!
I've retrieved over 50 GB of the formatted data on the NTFS partition.

Thanks a lot, Albinootje...:)

---

### Post by albinootje on 2009-01-04
> **Hefnawy said:**
> TestDisk worked!!!!
I've retrieved over 50 GB of the formatted data on the NTFS partition.


Good. Well done! :)

---

