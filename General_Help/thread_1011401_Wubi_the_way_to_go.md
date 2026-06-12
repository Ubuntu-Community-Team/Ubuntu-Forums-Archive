---
title: "Wubi the way to go?"
date: 2008-12-14
forum: General Help
---

### Post by terry@softreq.com on 2008-12-14
I have a laptop with Windows XP installed. 

I'm thinking of using Wubi to install Ubuntu, and then be able to dual boot in either XP or Ubuntu.

Is this the way to go?   Realiable?

Also, how much hard drive will I need available,  my machine has only 16gb available. 

Thanks, Terry

---

### Post by brandon88tube on 2008-12-14
It really depends on what you want, but I would say to try Ubuntu out, Wubi would be a good choice. Also when you go to install it gives you the option to choose how much space you want to use. You decide how much space you are willing to give Ubuntu, but remember you need some extra room if you plan on installing extra stuff.

---

### Post by terry@softreq.com on 2008-12-14
Thanks Brandon,
I heard I have to give up 5gb's as the minimum, is that correct?
Terry

---

### Post by brandon88tube on 2008-12-14
According to their requirements an install requires at least 4 GB of disk space. I would probably recommend a little more that 4GB as that is just the install for the base system.

---

### Post by abn91c on 2008-12-14
> **terry@softreq.com said:**
> I have a laptop with Windows XP installed. 

I'm thinking of using Wubi to install Ubuntu, and then be able to dual boot in either XP or Ubuntu.

Is this the way to go?   Realiable?

Also, how much hard drive will I need available,  my machine has only 16gb available. 

Thanks, Terry

I use wubi with my dell inspiron 1000, I gave wubi 10gigs, installed kubuntu without problems, same on my dimension 2400, just make sure you defrag windows first and avoid hard boots. Kubuntu is faster that xp on both PC's. Same functionality as standalone Ubuntu install.

---

### Post by magmon on 2008-12-14
Wubi is reportedly unstable, be careful! For a trial, I would recommend it, for long term use I would have to say the oposite

---

### Post by brandon88tube on 2008-12-15
> **magmon said:**
> Wubi is reportedly unstable, be careful! For a trial, I would recommend it, for long term use I would have to say the oposite

Unstable? How so? I'm curious because I have been using Wubi for a few months already.

---

### Post by Jammanuser on 2008-12-15
> **brandon88tube said:**
> Unstable? How so? I'm curious because I have been using Wubi for a few months already.

Unstable as in "crc error, system halted" error message that u get when trying to boot into Ubuntu...and which can't be fixed! :D

Hope u don't get it as well... :p

Cheers! :lolflag:

Jam Man

:guitar:

---

### Post by catfished on 2008-12-15
I've had Ubuntu 8.04 (Wubi installed) on my Acer laptop dual boot with XP SP3 for about 6 or 7 months now with no real problems. It just works. If only I could get Wine to work, I'd dump XP altogether.

---

### Post by Jammanuser on 2008-12-15
> **catfished said:**
> I've had Wubi installed Ubuntu 8.04 on my Acer laptop dual boot with XP SP3 for about 8 or 9 months with no real problems. It just works. If only I could get Wine to work, I'd dump XP altogether.

Well, it sounds like u were more lucky with Wubi than i was! :D because i got a crc error after about a **week** of using my Wubi install...and i **still** have not found a real fix for it! :lolflag:

Cheers! ):P

Jam Man

:guitar:

---

### Post by brandon88tube on 2008-12-15
> **catfished said:**
> I've had Ubuntu 8.04 (Wubi installed) on my Acer laptop dual boot with XP SP3 for about 6 or 7 months now with no real problems. It just works. If only I could get Wine to work, I'd dump XP altogether.

You could probably get help for Wine in other parts of the forums if you want it. As for me, I have never used Wine so I couldn't help.

---

### Post by abn91c on 2008-12-15
> **magmon said:**
> Wubi is reportedly unstable, be careful! For a trial, I would recommend it, for long term use I would have to say the oposite

I have used wubi since it came out with 7.04, it is not a trial and you get same functionality as any other method of ubuntu installation. Those "problems" and "errors" are with individuals hardware, not ubuntu/wubi. Remember this is an international forum, not all the hardware is the same as that you find in the USA because export issues, etc
So go ahead and use it. By the way I have a very old PC 400mhz(four hundred, not a typo) running ubuntu 8.10 and dual boot mandriva 2009 right now ansd it runs fine.

---

### Post by Jammanuser on 2008-12-15
> **abn91c said:**
> I have used wubi since it came out with 7.04, it is not a trial and you get same functionality as any other method of ubuntu installation. [COLOR="Red"]Those "problems" and "errors" are with individuals hardware, not ubuntu/wubi.[/COLOR] Remember this is an international forum, not all the hardware is the same as that you find in the USA because export issues, etc
So go ahead and use it. By the way I have a very old PC 400mhz(four hundred, not a typo) running ubuntu 8.10 and dual boot mandriva 2009 right now ansd it runs fine.

IS it? :D then how do u explain the fact that my hardware is fine, but i still got the "crc error" running Wubi? :lolflag:

Cheers! ):P

Jam Man

:guitar:

---

### Post by terry@softreq.com on 2008-12-15
I installed using Wubi and really didn't have a problem with it. 

So far it's run a-okay.

---

### Post by Jammanuser on 2008-12-15
> **terry@softreq.com said:**
> I installed using Wubi and really didn't have a problem with it. 

[COLOR="Red"]So far it's run a-okay.[/COLOR]

So far... :lolflag:

Jam Man

:guitar:

---

### Post by abn91c on 2008-12-15
> **terry@softreq.com said:**
> I installed using Wubi and really didn't have a problem with it. 

So far it's run a-okay.

Now that Ubuntu is more popular you can expect the invasion of the 13yr olds former AOL user/wannabe hackers. I never seen the crc error mentioned before until user jammauser flamed the forums with his "crc" error, If you google that error most posting point to an imminent hardware failure such as RAM or bad HDD sectors, not a software issues
Here is a definition from [http://www.linuxgazette.net](http://www.linuxgazette.net)

    It sounds like an ailing hard drive to me. Try a boot/rescue floppy (Tom's Root/Boot is nice for this -- [http://www.toms.net/rb](http://www.toms.net/rb)). 

    If you can't mount your filesystems, try running fdisk to view the partition table. The command 'fdisk -l' will list all available partitions on all drives (except for the Debian fdisk which will require a series of commands like 'fdisk -l /dev/hda ; fdisk -l /dev/hdb' etc depending on the number of drives you have --- they use a more powerful version of fdisk which nonetheless has this limitation). 

    It's possible that the CRC error is only affecting your track 0 (where your MBR, and the partition table are stored). 

    Anyway it is almost certainly a hardware problem. If you have a backup, I'd replace the drive (or at least reformat it with badblock checking enabled) and restore your system and data. If you don't have a backup, you might be able to recover some of your data and filesystems through some low-level disk editing heroics. 

    (If you've given up on recovering the filesystems and data, and you want to confirm that it really is hardware and not some Linux glitch, try using MS Windows to repartition and reformat that second drive. Not that MS Windows does that any better than Linux --- but you'll know by that it's not "just us").

---

### Post by Jammanuser on 2008-12-15
> **abn91c said:**
> [COLOR="Red"]Now that Ubuntu is more popular you can expect the invasion of the 13yr olds former AOL user/wannabe hackers. I never seen the crc error mentioned before until user jammauser flamed the forums with his "crc" error,[/COLOR] If you google that error most posting point to an imminent hardware failure such as RAM or bad HDD sectors, not a software issues
Here is a definition from [http://www.linuxgazette.net](http://www.linuxgazette.net)

    It sounds like an ailing hard drive to me. Try a boot/rescue floppy (Tom's Root/Boot is nice for this -- [http://www.toms.net/rb](http://www.toms.net/rb)). 

    If you can't mount your filesystems, try running fdisk to view the partition table. The command 'fdisk -l' will list all available partitions on all drives (except for the Debian fdisk which will require a series of commands like 'fdisk -l /dev/hda ; fdisk -l /dev/hdb' etc depending on the number of drives you have --- they use a more powerful version of fdisk which nonetheless has this limitation). 

    It's possible that the CRC error is only affecting your track 0 (where your MBR, and the partition table are stored). 

    Anyway it is almost certainly a hardware problem. If you have a backup, I'd replace the drive (or at least reformat it with badblock checking enabled) and restore your system and data. If you don't have a backup, you might be able to recover some of your data and filesystems through some low-level disk editing heroics. 

    (If you've given up on recovering the filesystems and data, and you want to confirm that it really is hardware and not some Linux glitch, try using MS Windows to repartition and reformat that second drive. Not that MS Windows does that any better than Linux --- but you'll know by that it's not "just us").

HUH? i think u **completely** misunderstood me! :D anyway, i don't have the time right now to correct ur **many** errors...i'll bbiab to correct them! :lolflag:

Cheers! ):P

Jam Man

:popcorn:

EDIT: ok...first of all i'm 24, not 13...and no wannabe hacker. secondly, yes, it is true that most crc errors r hardware related, however mine was NOT! :D Anyway, i've already recovered my data and programs (thanks to balaknair!:D) from the old Wubi install, by keeping the old root.disk, and then replacing the new after the reinstall...so i'm past the error now, as i do remember mentioning... I wasn't trying to blame u or anyone else on the Ubuntu forums for having the crc error...i'm sorry if u took it that way! As for Tom's Root/Boot floppy disk thing, i tried that back when I still had the crc error, but couldn't create because #1 I didn't have a floppy drive, and #2 because i found out the programs was for older versions of Windows (i.e. Windows 97) and would not work on Vista...so that wasn't an option for me! But anyway, like i said before, many times, i'm past the crc error now (and now have a **real** install of Ubuntu 8.10, not just Wubi), and so i'm no longer worried about it. However, the reason i've been mentioning it here as well as other places, is because i don't want other users to have this same problem with Wubi that i had...**believe** me, its a pain in the *** to deal with! Cheers! :D

---

