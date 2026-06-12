---
title: "Dell Inspiron 1525 dual boot w/Vista and Ubuntu"
date: 2009-01-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Dr. McKay on 2009-01-07
I'm looking into buying a Dell Inspiron 1525 with 2.4Ghz Core2Duo, 4Gb RAM, 320gb hard drive and a Intel GMAx3100 graphics adaptor. It comes with Vista Home Premium but I would like to make it a dual-boot system with Vista and Ubuntu. However, from what I've seen on my mom's Dell Studio she bought two months ago, there are two partitions on a factory installed Dell, the main Vista install and a small partition with what I believe to be recovery tools. Is it difficult to resize the existing partitions to create an extra one for Ubuntu, without messing everything up ?  I was thinking of giving 200Gb to Vista and the recovery tools combined, which leaves roughly 120Gb for Ubuntu (which I believe is plenty). 
Also, has anyone bought any of the latest Inspiron models ?  I would have gone for a 17" Studio because I would actually prefer a 17" screen, but as Studio's come with ATI cards, I figure it won't be ideal for Ubuntu. And 17" Inspiron's are a thing of the past (well, in Belgium anyway, where I live). So, anyone ?

---

### Post by tsger on 2009-01-07
It is easy to resize partitions using a live cd such as [Parted Magic]("http://distrowatch.com/table.php?distribution=partedmagic")

---

### Post by LeoSolaris on 2009-01-07
I have the slightly older model Dell 1520 that is just now a year old, and it came with the recovery partition. I opted to remove the recovery partition, because if I ever actually used it for a Windows reinstall/recovery, it would (I believe, and I may be wrong) eliminate my Linux partitions. With that said, I don't see why you wouldn't be able to just shrink the Vista partition, and completely ignore the recovery partition.

The ATI card, while not ideal, may be better than the integrated card, but that is a discussion for another day. (Mine was one of the last Inspirons to be offered with an Nvidia card, which they stopped offering a couple of weeks after I ordered it.)

Here's a wiki dealing with the ATI driver: [http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)

P.S. Ubuntu's Live CD has Gparted already installed (It doesn't install with the rest of the system though) It's in System->Administration->Partition Editor   It's very stable, but as with any tool that messes with your partitions, there is always a chance it could do damage.

---

### Post by Dr. McKay on 2009-01-07
> **LeoSolaris said:**
> I have the slightly older model Dell 1520 that is just now a year old, and it came with the recovery partition. I opted to remove the recovery partition, because if I ever actually used it for a Windows reinstall/recovery, it would (I believe, and I may be wrong) eliminate my Linux partitions. With that said, I don't see why you wouldn't be able to just shrink the Vista partition, and completely ignore the recovery partition.

The ATI card, while not ideal, may be better than the integrated card, but that is a discussion for another day. (Mine was one of the last Inspirons to be offered with an Nvidia card, which they stopped offering a couple of weeks after I ordered it.)

Here's a wiki dealing with the ATI driver: [http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)

P.S. Ubuntu's Live CD has Gparted already installed (It doesn't install with the rest of the system though) It's in System->Administration->Partition Editor   It's very stable, but as with any tool that messes with your partitions, there is always a chance it could do damage.

I'm not too bothered about the graphics card. As long as it can handle all graphical bells & whistles of Vista Aero en Linux compiz fusion (for both of which the GMAx3100 will be more than sufficient I believe), I'll be happy. I'm not interested in heavy 3D-stuff or games (I'm more into console gaming).
As for the recovery partition, I guess it wouldn't hurt to get rid of it. I always keep backups of my important files, so I should be okay. I've been an Apple user for 9 years (currently on iMac G5 and iBook G4 with OS X Tiger) but I don't like the direction Apple is taking. They've become too obsessed with design, pretty user interfaces and with limiting consumer's choices, hardware and software wise. Except for their pro-apps, their software (iLife, iWork, etc.) has become a little TOO user friendly. Not to mention their exorbitant prices...

---

### Post by krnekhelesh on 2009-01-08
I bought Dell Inspiron 1525 about 3 months ago. With the factory settings there were 3 partition, 1 for vista , 1 for dell mediadirect and 1 for some recovery setting same as yours.

I tried install Ubuntu 8.04, everything went on well but when it came to resizing the vista partition ubuntu screwed it up and I lost my vista os and everything. So I had to reinstall Vista and in its installation process I partitioned it into 2 drivers, one for vista and the other for ubuntu.

Then I installed media direct and then installed ubuntu. I wanted to keep vista as a backup as I'm also a linux newbie. So I'm currently using ubuntu for the past 2 months and everything is going on smoothly.....ubuntu detects all your multimedia keys, your wireless card everything is automatic.....

---

### Post by krnekhelesh on 2009-01-08
There is always some risk involved when resizing your partition or splitting into 2 partitions. It is best that you first backup all the data and then proceed to install ubuntu..

---

