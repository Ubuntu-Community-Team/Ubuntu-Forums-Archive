---
title: "external harddisk question"
date: 2009-03-10
forum: General Help
---

### Post by Meow27 on 2009-03-10
hi, 
       im getting a 320 gb external harddisk soon, im interested in knowing the following

when i tell the bios to manually boot, will the device be recognized as a harddisk or a usb device?

when i load the harddisk in the bios, is there a way to boot different OSs from it (using grub or something, like having a partition with ubuntu and one with dream linux or something.)

3rd question, if i want windows to recognize my hard disk should i 
- leave a first primary partition as ntfs or fat32
- should my other partitions be extended or the other way around?

thanks in advance (if im not making sense, please point it out)

---

### Post by megamania on 2009-03-10
> **Meow27 said:**
> hi, 
       im getting a 320 gb external harddisk soon, 


The BIOS related part depends... from the BIOS you are using. :-)

Once you get the hard disk to boot, it will behave like a normal hard disk, so the bootloader will start and then the operating system(s) is/are loaded.

Regarding the 3rd question, speaking in general Windows will see the FAT32 and NTFS partitions, plus EXT2/3 partitions with special programs... But that's assuming you are talking about booting from another hard disk and then attaching the usb enclosure...

---

### Post by stanz on 2009-03-10
> when i tell the bios to manually boot,
will the device be recognized as a harddisk or a usb device?I've used an external hdd connecting with usb cables...
I've not had to do anything concerning BIOS...when using ubuntu.
Weather plugged-in before booting -- or with the system running, it was
recognized and showed on my desktop and in nautilus, with an icon.
(it used the brand name)
m$ should do the same {?}.

> when i load the harddisk in the bios, is there a way to boot different
OSs from it (using grub or something, like having a partition with ubuntu
and one with dream linux or something.)load into bios?
or do you mean to add it to the grub menu with additional boot options?
   bios...i don't think you need to go there...i could be wrong.

if your thinking grub and booting from that external hd...
there's much research you'll need to do (my advice) cause if
anything is entered wrong - booting will be broke!
but it is an harddrive, and partitioning for 1 or more os's can be done.

> 3rd question, if i want windows to recognize my hard disk should i 
- leave a first primary partition as ntfs or fat32
- should my other partitions be extended or the other way around?m$ xp asked me some questions and showed the drive same as usb stick,
this usually if just like a folder (becoming part of the directory).

on partitioning: m$ windows does not recongize linux...so I've always installed
and kept m$ in the front of my drives (beginning sectors).

when installing linux flavors (mainly ubuntu), m$ is reconized and added to the grub menu,
so you have the choice of booting to either. m$ will not do that (to my knowledge).

hope this helps ~ :)

---

### Post by detroit/zero on 2009-03-10
> **Meow27 said:**
> hi, 
       im getting a 320 gb external harddisk soon, im interested in knowing the following

when i tell the bios to manually boot, will the device be recognized as a harddisk or a usb device?That depends on your BIOS. In my current Toshiba laptop (Phoenix BIOS 1.48 ), USB devices are recognized as USB devices, but on my HP desktop (Phoenix BIOS 1.36) they sometimes show up as hard drives. I have one thumbdrive with a version of Slax on it that shows up as a CD. There's no one right answer to that question, I guess is the point...> **Meow27 said:**
> when i load the harddisk in the bios, is there a way to boot different OSs from it (using grub or something, like having a partition with ubuntu and one with dream linux or something.)Short answer: No, but..
Long answer: Yes, if... (someone else pick it up here.. :KS)> **Meow27 said:**
> 3rd question, if i want windows to recognize my hard disk should i 
- leave a first primary partition as ntfs or fat32
- should my other partitions be extended or the other way around?Windows can work with EXT2 & EXT3 partitions of you install [a program called ext2ifs]("http://www.fs-driver.org/"); it gives Windows the ability to read and write to EXT2 & EXT3 partitions. I'm still using Hardy because of the LTS status, but if I remember right, I think that if Intrepid (8.10) isn't the one to make the switch, then Jaunty (9.04) will be using the EXT4 filesystem format. I'm not sure if ext2ifs can handle that yet or not.. you'll have to read up on it. (**EDIT**: a quick Google search turns up this page about [Windows and EXT4 support]("http://www.linuxjournal.com/article/9449") - looks like it's all taken care of.)

I can speak from experience when I say that a FAT32 partition will cause you many headaches if and when you ever get around to wanting to enable file sharing and such for the drive. NTFS doesn't have any of those kinds of problems, and since Windows will work best with its' own formats, you might want to have an NTFS partition on hand, just in case the need arises. Maybe set aside 10 or 20 GB out of 320 just in case...

---

### Post by Meow27 on 2009-03-11
thanks for the comments =^.^=


but i do want the long answer, cause thats my biggest question lol


if i manually boot from the hard disk, (if grub is installed in there), will it work as if the local hard disk is nonexistent (at least for the boot up)?

---

### Post by megamania on 2009-03-12
> **Meow27 said:**
> 
if i manually boot from the hard disk, (if grub is installed in there), will it work as if the local hard disk is nonexistent (at least for the boot up)?
IF your bios supports booting from USB, and
IF you set the BIOS to boot from the USB disk first, then
YES, it will boot from the USB disk. :-)

It's like deciding whether to boot from cd, floppy or hard disk...

---

### Post by Meow27 on 2009-03-12
yo guys arent getting me

if i have grub installed on the disk, will the grub menu be different than the one of the host machine's harddisk?

---

### Post by megamania on 2009-03-12
> **Meow27 said:**
> yo guys arent getting me

if i have grub installed on the disk, will the grub menu be different than the one of the host machine's harddisk?
I'm getting you.

You will load the Grub that's on the disk you're booting from!

So, if you boot from the usb disk, you'll load the Grub that's on the USB disk.

---

### Post by Meow27 on 2009-03-12
yeah, you got me. now will that work?

---

### Post by megamania on 2009-03-12
> **Meow27 said:**
> yeah, you got me. now will that work?
post #6

---

### Post by Meow27 on 2009-03-12
ok. thanks to all who replied!

[/solved]

---

