---
title: "Unsuccessful ubuntu 12 upgrade, MBR issues, Dell 1650 laptop"
date: 2012-09-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by slalom72 on 2012-09-14
Question for the grub dual boot gurus etc,

So I tried to upgrade to 12, however the install didn't work. So here's the deal...

Ubuntu 12/11/whatever it ended up as, didn't load, so I re installed 11.10 that I had on a disk, however with the junk from the 12 and the unpacked junk for the 11.10 the install failed to complete properly because the partition was full of crap.

Que attemped load into windows to back up a few things first (yeah I know i installed an OS without doing a backup) but the MBR is all messed up and I get the Grub recovery screen. 

I cant use windows boot to straighten out MBR because the ubuntu disk isn't coming out of the disk drive (its a slot loader not tray mounted)

Im using the ubuntu disk stuck in the drive to access the lappy and the net, idealy I'd like to reformat the umbuntu partition re install 11.10, and straighten out grub, last resort is of corse a full re-formatt but ive finally got windows running nice and id like to avoid that.

Any Ideas gurus???

Cheers.

---

### Post by opensshd on 2012-09-14
If you press the disk eject button (top right, line w/ arrow pointing up) it won't kick your cd out at boot?

The 11 cd you have in there now, will it boot a liveOS (try, not install), or is it an alternate?

Can you tell me anymore about the circumstances in which it failed to install? Any ideas why?

---

### Post by slalom72 on 2012-09-14
some reason the eject button isnt working while ever im not in an OS, and the only OS i can get to work is running the trial version off the disk, so i can get in to do stuff only im not sure what needs to be done. its how i posted my initiatal query.

As to why it failed, the only reason i could think of is there wasnt enough room to fully unpack the install as it was going, which is strange because it had quite a few gig free to work with, and i dont recall there being any warnings about it that time, the re-install of 11.10 it came up tho.

Tried using boot repair within 11.10 (running off cd drive), but again drive space on Ubuntu partition is preventing proper diagnosis.

Any Ideas?

---

### Post by opensshd on 2012-09-14
Yah, if you can get booted with the liveOS and make some space, a full disk can have weird effects.

How did you try to repair the bootloader?

update-grub?

---

### Post by slalom72 on 2012-09-14
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) but I couldnt get it to work properly.

 Idealy i'd just like to clear the partition and re install good old 11.10 on its own, or 12 off a clean partition.

---

### Post by YannBuntu on 2012-09-14
Hi
Please could you indicate the URL that appears when using Boot-Repair ?

---

### Post by slalom72 on 2012-09-18
Finally fixed mbr and reformatted & installed 11.10 however the disk drive still isn't ejecting, using the touch pad or the drop down menus 'eject' function. Currently re-attempting to install Ubuntu 12  then going to see how it goes, it's not isolated to windows7 or Ubuntu.

---

### Post by slalom72 on 2012-09-18
Well I'm now successfully running 12.04, however i'm still having the disk eject issues, as mentioned before its in win7, ubuntu 11.10 and 12.04, and I still like the novelty of using dvd's besides its my bluray player, so id like to figure it out sooner rather than later. I have a screenshot but cant post it.

Help would be much apreciated.  ](*,)



P.S I got it wrong at the start the lappy is a 1645 not a 1650...my bad guys.

---

### Post by slalom72 on 2012-09-21
I tried to eject the disk whilst in the BIOS and it kept doing the same  thing (apparently this disables any third party software that could be interfering), the drive stops spinning, unlocks the disk, and attempts to eject, then gets  stuck. Ive already updated Quickset drivers (for the touch panel accross the top of keyboard), and I couldnt update dvd  drive firmware because it needs an empty disk drive. However, I dug two  plastic club membership cards out of my wallet (ones without the raised  text or card numbers) and jiggled the disk a little and out it slid, not  sure why it got stuck, maybe there is a slight burr on the disk, but Ive tried it now with a few other disks and they havent stuck again, so  hopefully its fixed, it sure beats replacing the BR disk drive.

Thanks for the advice guys.

---

### Post by YannBuntu on 2012-09-21
Please open another thread for this problem.
You will get better answers if the title/1st post is appropriate.

---

