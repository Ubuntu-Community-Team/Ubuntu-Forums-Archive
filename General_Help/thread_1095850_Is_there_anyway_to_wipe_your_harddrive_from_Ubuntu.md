---
title: "Is there anyway to wipe your harddrive from Ubuntu?"
date: 2009-03-14
forum: General Help
---

### Post by berrypievision on 2009-03-14
I am wondering since I cannot access my DOS floppy that I have to wipe my drive clean, due to my keyboard not working in DOS or during BIOS screens.  So is there a way to wipe the drive from Ubuntu or any Linux OS?

Also, I am not talking partitions, but I mean the drive.

---

### Post by hikaricore on 2009-03-14
I'm not sure I completely understand what you're asking.

You want to completely reformat your hard drive?

---

### Post by berrypievision on 2009-03-14
Yes, to wipe it.

---

### Post by ajgreeny on 2009-03-14
Dukes Boot and Nuke (DBAN) which will run even from a floppy if you have one.

---

### Post by berrypievision on 2009-03-14
Well, isn't there a way to wipe (or format, whatever) the drive from your installed Ubuntu?  I seem to have problems with BIOS, DOS and such prompts.

---

### Post by theozzlives on 2009-03-14
> **berrypievision said:**
> Well, isn't there a way to wipe (or format, whatever) the drive from your installed Ubuntu?  I seem to have problems with BIOS, DOS and such prompts.

Huh? Ubuntu is on your HD if you wipe it, you wipe Ubuntu.  DOS is a thing of the past.

---

### Post by hysteresis on 2009-03-14
It sounds like you have a usb keyboard on a motherboard that does not support it. Or perhaps there is a setting in the BIOS to enable it.

---

### Post by arapa on 2009-03-14
Wiping your hardrive won't necessarily fix a problem with you bios - you could remove your hard drives completely and run them over with a forklift and still have the exact same bios. Are you wanting to flash the bios?

Are you sure you don't have a bad keyboard? Does your keyboard work in Ubuntu? Is it a USB keyboard? Wireless? PS/2? The command prompt/terminal/DOS and you bios are two different things.

---

### Post by krzysz00 on 2009-03-14
Wipe the drive (it will contain NOTHING but zeros after this, so make a FULL backup before proceeding) (in Terminal, will require keyboard
```
dd if=/dev/zero of=/dev/<drive device(usually sda for first drive in newer computers)
```

---

### Post by jchiar on 2009-03-14
Yes, shred works on some setups. Somebody mentioned DBAN, that is a boot tool that works on almost anything.
That command line post was on time.
This site explains it very well,
[http://linuxhelp.blogspot.com/2006/06/how-to-securely-erase-hard-disk-before.html](http://linuxhelp.blogspot.com/2006/06/how-to-securely-erase-hard-disk-before.html)
Danger Will Robinson! Danger! 
Be very careful with that stuff becuase it can render a media device unreadable/writeable.

---

### Post by anjilslaire on 2009-03-14
> **krzysz00 said:**
> Wipe the drive (it will contain NOTHING but zeros after this, so make a FULL backup before proceeding) (in Terminal, will require keyboard
```
dd if=/dev/zero of=/dev/<drive device>
```(usually sda for first drive in newer computers)

There. Fixed that for you.

---

### Post by krzysz00 on 2009-03-14
in the dd command above, to change zeros to random bytes make /dev/zero /dev/random or /dev/urandom

---

### Post by dhughes on 2009-03-14
> **berrypievision said:**
> I am wondering since I cannot access my DOS floppy that I have to wipe my drive clean, due to my keyboard not working in DOS or during BIOS screens.  So is there a way to wipe the drive from Ubuntu or any Linux OS?

Also, I am not talking partitions, but I mean the drive.


 You can't do it from the OS you're using because the hard drive is in use (mounted) you'd have to unmount it but then you can't use the installed OS.

 You can use the Ubuntu LiveCD, reboot and choose System>Administration>Partition Editor and select the hard drive you want to format. (If for some reason the hard drive is mounted choose to unmount it).

 You can also, obviously, use Partition Editor to create partitions and to format or partition other devices. It's useful but dangerous if you get confused and wipe out something you didn't mean too!

---

### Post by berrypievision on 2009-03-14
I've said before, that I am not talking of partitions, I am talking of wiping the drive.  Erasing partitions is not wiping the drive.

I think some of you misunderstand me.  I'm not trying to fix my BIOS or anything, it's just my BIOS is so screwed up that in certain circumstances, my keyboard will not work with it, on the BIOS screen (normally, however it will still take some commands on there) and on certain DOS prompts that I have for wiping and fixing programs.  However, for the most part, the keyboard works fine, and I was asking if I can format the drive form Ubuntu, and I should have said (meant) can I do it from a live CD distro, because I simply cannot do it from my DOS bootup.  I don't believe there is anything wrong with the keyboard, because it used to work fine in those situations, but slowly problems have arisen.  Usually wiping the drive would fix said problems, but the DOS bootup just won't work without the keyboard.

This DBAN I have read from people here can actually render a drive unusable.  Well, I don't want to risk that.  Any safe alternative programs for formating a drive?  Because I am not wiping it to sell it off or to be safe from someone trying to retrieve my data or anything, I'm doing it for the purpose of reusing it.

---

### Post by berrypievision on 2009-03-14
Also, the keyboard is USB, since a lot were asking.

---

### Post by dcstar on 2009-03-15
> **berrypievision said:**
> 
......
Any safe alternative programs for formating a drive?  Because I am not wiping it to sell it off or to be safe from someone trying to retrieve my data or anything, **I'm doing it for the purpose of reusing it**.

Simply deleting the partitions using the Partition Editor will achieve what you want.

---

### Post by berrypievision on 2009-03-15
No, partition erasing does not amount to wiping the drive.  I've erased my partitions plenty of times in the past two months, it doesn't really do anything since its not formating the data.

---

### Post by anjilslaire on 2009-03-16
Deleting partitions effectively erases the data, because with no partition table, the data is unreadable without forensic analysis.

That being said, zeroing the drive using the command above from the terminal of a Live CD, then creating new partitions will have you starting from scratch essentially.

---

### Post by berrypievision on 2009-03-26
Erasing partitions does not delete any data, nor does it format anything.  However, I may try this zero thing.  Thank you.

---

### Post by mrsteveman1 on 2009-03-26
You can dd the drive from within ubuntu, but i suspect it will stop working at some point during the process once files that are already open no longer have data in them anymore, and the system will probably either panic or just stop doing anything. It might work in single user mode though, at least has a better shot than in full desktop mode.

Best bet is to just boot a livecd and dd the drive from there, can't go wrong.

---

### Post by anjilslaire on 2009-03-28
> **berrypievision said:**
> Erasing partitions does not delete any data, nor does it format anything.  However, I may try this zero thing.  Thank you.


Understood, but for all intents and purposes you won't get the data back without a lot of work. With no readable partition table to tell the OS where the data is, it makes it very hard to retrieve. Possible, yes. Easy? No. Hence my reply:

[quote=anjilslaire]
**with no partition table, the data is unreadable** without forensic analysis.
[/quote]

---

### Post by CatKiller on 2009-03-28
Your keyboard does not work in DOS or in the BIOS setup because it is USB, and so requires something to interpret the USB signals as keyboard signals. This is provided by your OS, but DOS has no knowledge of USB keyboards, since USB was created much later than DOS. All remotely recent motherboard chipsets have the ability to provide this interpreter themselves, allowing the BIOS and DOS to receive keyboard input from a USB keyboard with no knowledge that it's a USB keyboard at all. However, since some old and crappy keyboards provided signals that were misinterpreted by this interpreter (generally meaning that each keypress didn't stop until another was pressed) the option to run this interpreter was disabled by default. The upshot of that decision is that you can't get into the BIOS using a USB keyboard to turn on support for your USB keyboard.

You can, however, use a non-USB keyboard temporarily to enter the BIOS in order to turn on the USB Keyboard Support option. Then you can use your USB keyboard for everything.

That isn't your main problem though. You can, as other posters have already pointed out, use **dd** to zero your drive (which takes a long time) or delete and create partitions on the drive (which formats your drive). You certainly don't need to run Windows to format your hard drive. That isn't your main problem either.

Your main problem is that if you need to regularly re-format your hard drive then **one or both of your RAM or hard drive are broken**. You can test your memory using memtest86+, which is included with Ubuntu, and on the Ubuntu live cd. I'd recommend running it from the live cd, since the data on your hard drive is suspect. Generally, the hard drive manufacturer's website will allow you to download an application to test the integrity of the hard drive. Hard drives fail - they are generally the first component to fail in a given computer. With a computer that is working properly you do not have to regularly re-format the hard drive to get it to work again. This is a symptom of a significant hardware problem.

---

### Post by dcstar on 2009-03-28
> **berrypievision said:**
> I've said before, that I am not talking of partitions, I am talking of wiping the drive.  Erasing partitions is not wiping the drive.

I think some of you misunderstand me
........
I don't believe there is anything wrong with the keyboard, because it used to work fine in those situations, but slowly problems have arisen.  **Usually wiping the drive would fix said problems,** but the DOS bootup just won't work without the keyboard.
........
Any safe alternative programs for formating a drive?  Because I am not wiping it to sell it off or to be safe from someone trying to retrieve my data or anything, **I'm doing it for the purpose of reusing it.**

Erasing partitions - in your case - **is** wiping the drive.

All a DOS/Windows "format" does is delete the partition data and read (yes kiddies, no writes at all) the data sectors to make sure that they exist.

If you want to waste your own time continually running a DOS/Windows format on a drive then go ahead, but don't do it believing that it is actually writing to a drive.

Hard Disk formatting effectively ceased 20+ years ago with the introduction of IDE drive technology.

---

### Post by berrypievision on 2009-04-04
Uh...erasing partitions is not deleting the data.  I am seeking to format the drive, not simply renaming data partitions so I can reuse the space.  I do not seek to make the hard drive simply free for more data, I want to wipe it completely clean but make it able to be used again.

> 
All a DOS/Windows "format"

I'm not talking of a DOS/Windows "format" though.  I'm talking of my program that does a DOD (Department of Defense) style wipes, which I've used in the past.

The thing about the keyboard is sort of pointless, since this keyboard at one time worked just fine in my BIOS screen, but nearly a year ago, stopped working alongside any other keyboard (as far as I know, I guess I should try again).  Plus, I do not use a USB keyboard.  I do not believe I ever indicated I ever did.

I don't think the main issue is the hard drive, as the hard drive is not broken, I simply want to have a clean slate with it.  It wouldn't hurt, and it would probably help.

---

### Post by CatKiller on 2009-04-04
> **berrypievision said:**
> Plus, I do not use a USB keyboard.  I do not believe I ever indicated I ever did.

:confused:

> **berrypievision said:**
> Also, the keyboard is USB, since a lot were asking.


> **berrypievision said:**
> I don't think the main issue is the hard drive, as the hard drive is not broken, I simply want to have a clean slate with it.  It wouldn't hurt, and it would probably help.

You've already been told how to write over the drive with zeroes, and how to write over the drive with random data, which is all those programs do. You could even do it multiple times if you wanted.

If you are experiencing problems that increase over time, and formatting the hard drive and re-installing helps, then your hard drive may be broken, even if you don't think it is. It's not like running the manufacturer's diagnostic will hurt. Does it ever make any noises?

---

### Post by berrypievision on 2009-04-06
Woops, never corrected that!  I forgot about that.  What I meant was not USB.  I've never used a USB keyboard in my life.

Sorry about that.

I've never heard my hard drive make noises as far as I know, but I have no idea really what you mean by that.  

As for the zero wipe thingie, will it allow me to use the hard drive again?

---

### Post by CatKiller on 2009-04-06
> **berrypievision said:**
> I've never heard my hard drive make noises as far as I know, but I have no idea really what you mean by that.  

Two of the more common hard drives - sticky arm or power control failure - lead to audible symptoms. With a sticky arm, you'll hear failures of the motion of the arm. With power control failures you'll hear a click as the read/write heads, no longer cushioned by an incredibly thin layer of air, smack into the platters, taking out a chunk of random data. As power is restored, you'll hear the hard drive spin up again. Grinding noises are obviously bad, but you can't really fail to notice those unless you've got a very noisy fan or always have music on.

There are other hard drive failures that are silent though. Problems with the logic board, bad cache memory chip, that sort of thing.

The problem with (many) hard drive failures is that they don't appear to be hard drive failures at all. Random bits of data just get changed or removed. When that bit is part of the video driver, the video starts acting strange. If it's part of an application, suddenly that application isn't as stable as it used to be. Audio files, and suddenly the audio system has glitches, or doesn't work properly. If it's the kernel, suddenly everything becomes unstable; kernel panics/BSOD, random restarts, that sort of thing. Memory problems show up in the same ways, for pretty much the same reason. One of the features of this sort of problem is that when you re-install the OS, you replace the bad data with good data and all the problems go away. For a little while, till something else gets damaged. So you see an increasing amount of instability until you re-install again and everything is fine. Unless you actually identify and fix the problem, it looks like registry-rot, or bad drivers, or any number of other excuses not to have a perfectly functional computer, and the user generally blames whoever made the OS.

It really is worth checking them both if you have any kind of unlocalised weirdness. And from time to time as a precautionary measure.

> 
As for the zero wipe thingie, will it allow me to use the hard drive again?Not straight away. You'd still need to partition/format the drive. I'm not sure what else you'd expect.

---

