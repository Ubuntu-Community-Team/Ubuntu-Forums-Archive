---
title: "How do I setup GRUB? - 9 Operating Systems - 1 Hard-Drive"
date: 2009-01-16
forum: General Help
---

### Post by Panarchy on 2009-01-16
Hi

Well I've finally purchased it. Took me 3 months, but I did it!

[IMG]http://i41.tinypic.com/11jxfug.jpg[/IMG]

Nice new internal SATA 1 terrabyte hard-disk-drive :P

Well anyways, I've decided to put 9 operating systems on this hard-drive.

I've spent a lot of time working out the finer details, here is the excel file I made to help myself out in the working out of my partitioning schema: **[Download]("http://www.mediafire.com/?sharekey=50920fee786b36606787958b30ba2140e04e75f6e8ebb871")** (I've included both an .xls and a .xlsx).

And I have also created a perhaps easier to work out version, which you can view below;

[IMG]http://i42.tinypic.com/5xmkpc.jpg[/IMG]

Please help me with setting up my /boot/grub folder.

I would also like to know if it would be possible to put a loop into the boot.ini file and the BCD that will take you back to the grub menu. I will also [probably] use EasyBCD to list the OS's from the BCD listings.

Please help me out with doing these two things (especially the GRUB part of it).

Thanks in advance,

Panarchy

---

### Post by aheckler on 2009-01-16
Christ dude, shrink the images a little :)

---

### Post by Panarchy on 2009-01-16
Ah!

Sorry, sure man.

---

### Post by p_quarles on 2009-01-16
I removed the oversized images. Feel free to put them back on, but use the attachment feature built-in to the forum software. That will create thumbnails automatically. 

Thanks.

---

### Post by Bucky Ball on 2009-01-16
Man! One question: Why? Is this for education/experimentation or you need this particular setup specifically?

I'm presuming you have breakdowns of each 100Gb partition you have here (the partitions inside that). Also, I believe the Linux installs can share the same swap, someone correct me if I'm wrong. Lastly, there is 30+Gb free space at the end. Why? Back to the drawing board and absorb that, too.

I would seriously think about getting more specific/detailed about your partitioning here. For instance, you have two windoze installs on 100Gb allocation each, yet they are both capable of using NTFS of FAT32 for **DATA** storage (*not *OS install). Along those lines, Linux (and possibly some of the others) can use NTFS and FAT32 also. Hmm.

I would break it down to the maximum required partition size for each ***OS** *install (OS and its programs/packages/apps), then divide what's left into appropriate partition types for *data storage *requirements. This also puts the OSs all at the beginning or fastest part of the drive and so in theory ...

You might have something like:

Vista = 20
Windoze 7 = 20
Ubuntu = 15
Xubuntu = 10

... etc., depending on the requirements of the OS and how many programs you are going to add to that. You can go one step further and have a partitions specifically for programs also, which means Vista = 13, Xubuntu = 5, but with one drive that could slow things down a bit and generally wear the drive out.

Good luck with it ... \\:D/

---

### Post by Yellow Pasque on 2009-01-16
Wow. I thought I was crazy to run 3 different Linux distros on one drive. Well, read the grub manual very carefully.  Pay particular attention to the chainloader section. :P

---

### Post by Bucky Ball on 2009-01-16
ps: sorry I didn't cover the grub issue, my head is spinning thinking about that! :)

---

### Post by Panarchy on 2009-01-16
> **Bucky Ball said:**
> Man! One question: Why? Is this for education/experimentation or you need this particular setup specifically?

I'm presuming you have breakdowns of each 100Gb partition you have here (the partitions inside that). Also, I believe the Linux installs can share the same swap, someone correct me if I'm wrong. Lastly, there is 30+Gb free space at the end. Why? Back to the drawing board and absorb that, too.

I would seriously think about getting more specific/detailed about your partitioning here. For instance, you have two windoze installs on 100Gb allocation each, yet they are both capable of using NTFS of FAT32 for **DATA** storage (*not *OS install). Along those lines, Linux (and possibly some of the others) can use NTFS and FAT32 also. Hmm.

I would break it down to the maximum required partition size for each ***OS** *install (OS and its programs/packages/apps), then divide what's left into appropriate partition types for *data storage *requirements. This also puts the OSs all at the beginning or fastest part of the drive and so in theory ...

You might have something like:

Vista = 20
Windoze 7 = 20
Ubuntu = 15
Xubuntu = 10

... etc., depending on the requirements of the OS and how many programs you are going to add to that. You can go one step further and have a partitions specifically for programs also, which means Vista = 13, Xubuntu = 5, but with one drive that could slow things down a bit and generally wear the drive out.

Good luck with it ... \\:D/

Thanks, but I was thinking that with all this extra space I just bought, that I might as well.

And that free space at the end, I'll probably use as FAT32, although I might use it for another OS, or... well there are various uses for it, so I've kept it without anything for the moment.

> **Temüjin said:**
> Wow. I thought I was crazy to run 3 different Linux distros on one drive. Well, read the grub manual very carefully.  Pay particular attention to the chainloader section. :P

Chainloader? That's the one for windows... right?

Please help me write the menu.lst file.

Thanks

Panarchy

PS: Remade the xls & xlsx to fit on one A4 page. [Download it here]("http://www.mediafire.com/?sharekey=22f7c6c10e3361bc9cfb10f6b341fc9e62bcd34da1f9b540")!

---

### Post by Bucky Ball on 2009-01-16
[quote=Panarchy]Thanks, but I was thinking that with all this extra space I just bought, that I might as well.[/quote]

Yea, think you might be missing my point:

All operating systems on small partitions  = 100Gb

Data partitions = 900Gb
(ie: ntfs = 300, ext3 = 300, something else = 300 ... whatever is appropriate. You will then get all your operating systems at the beginning of the drive.) :)

---

### Post by Panarchy on 2009-01-16
Why would I want all my operating systems at the beggining of the drive?

---

### Post by bumanie on 2009-01-16
have a look at [GAG bootloader]("http://users.bigpond.net.au/hermanzone/p12.htm"), it's open source and handles up to 9 operating systems - You could do it with GRUB by chainloading 8 of the operating systems. It can be done, someone has chainloaded 100+ operating systems with GRUB. Having a dedicated /boot partition may also be helpful. Check out [Herman's grub page]("http://users.bigpond.net.au/hermanzone/p15.htm"), it  is the definitive guide to GRUB.

---

### Post by dagnabit dang doohickey on 2009-01-16
With those big honkin' partitions, [maximum absurdity]("http://www.justlinux.com/forum/showthread.php?p=861282") will never be achieved.

---

### Post by bodhi.zazen on 2009-01-16
If you are going to boot that many OS I advise you look at this thread, lots of sage advice

[How to Multi-boot (Maintain more then 2 OS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=724817")

---

### Post by snova on 2009-01-16
> **Panarchy said:**
> Chainloader? That's the one for windows... right?

Chainloading is when the bootloader, rather than load the kernel and jump to it, loads another bootloader. It would work with any OS.

---

### Post by Panarchy on 2009-01-17
> **bumanie said:**
> have a look at [GAG bootloader]("http://users.bigpond.net.au/hermanzone/p12.htm"), it's open source and handles up to 9 operating systems - You could do it with GRUB by chainloading 8 of the operating systems. It can be done, someone has chainloaded 100+ operating systems with GRUB. Having a dedicated /boot partition may also be helpful. Check out [Herman's grub page]("http://users.bigpond.net.au/hermanzone/p15.htm"), it  is the definitive guide to GRUB.

Thanks. Some questions about GAG;

Can it be run from a USB? (I know it can run from a floppy)

Is 9 the limit for the number of OS's it can have? Because I read that on the site, but I also saw a lot more in one of the screenshots...:confused:

> **snova said:**
> Chainloading is when the bootloader, rather than load the kernel and jump to it, loads another bootloader. It would work with any OS.

Hmm... that's a weird idea. Thanks for explaining it.

> **bodhi.zazen said:**
> If you are going to boot that many OS I advise you look at this thread, lots of sage advice

[How to Multi-boot (Maintain more then 2 OS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=724817")

Thanks, might be helpful.

Although I would still like some help in what I should have in each of my /boot directories.

Please tell me what to put in there, and what text to have in the menu.lst file.

Thanks in advance,

Panarchy

---

### Post by bumanie on 2009-01-17
As far as I know GAG can deals with a maximum of 9 OSes. I have not heard of it being able to be run off a usb thumb drive - you sound adventurous enough to give it a try! However, I doubt it will work without specific code being written for it to work in that manner.

---

### Post by Panarchy on 2009-01-17
^Hmm... okay.

It's just I don't have a floppy drive, tried installing one once, something like I didn't have the right internal power cable... so yeah.

Maybe you could recommend another multi-OS handling boot manager that can run from a CD or USB?

Cause I'll probably run into some problems whilst doing my work on GRUB, boot.ini and BCD, so it'll always be helpful to have a CD around that'll be able to boot directly into any partition...

If you have any recommendations, please tell me of them!

Thanks in advance,

Panarchy

---

### Post by Panarchy on 2009-01-20
Hi

Well I haven't received a reply for almost 3 days, so I've decided to update you on the progress, and to ask for some more advice.

I think I've worked out how to add an entry in the boot.ini to 'return/loop-back' to the GRUB menu. It has been worked out by following [this guide]("http://ubuntuforums.org/showthread.php?t=87751").

Now all that's left to do is to finish writing GRUB's menu.lst.

Can I get [some more] help on this front?

Thanks in advance,

Panarchy

---

### Post by Panarchy on 2009-02-01
Can someone please recommend a LiveCD capable of GRUB?

By this I mean that I would like a LiveCD capable of booting to ANY partition on my hard-drive.

I would like it to do this either by GRUB (likely), Lilo or BCD.

Thanks in advance,

Panarchy

PS: If you are going to recommend a GRUB solution for this, (GRUB LiveCD capable of booting to ANY partition), then can you please tell me if it would be possible to use custom menu.lst within it? Thanks.

---

### Post by mb_webguy on 2009-02-02
Unix-based operating systems (including Mac OS X) can each fit happily on an 8-12GB partition.  I'd put each Windows OS on a 25-30GB partition.  If you're a gamer, increase the size of the partition for the Windows OS you use for gaming by about 10GB.  Add a swap partition to be shared by all of the OSes that use it equal to your system memory.  The rest of the drive (which is about 800GB, more or less) can be formatted as ntfs (or ext3 if you use the ext2ifs driver in Windows) for your shared partition.

If you really want to get fancy, you can add a small (1-5GB) /home partition for each of the Unix-based OSes.

And as far as the bootloader, I'd just chainload GRUB, as others have suggested.

---

### Post by Yellow Pasque on 2009-02-02
[http://distrowatch.com/table.php?distribution=partedmagic](http://distrowatch.com/table.php?distribution=partedmagic)

---

### Post by T3kG33k on 2009-02-02
One cannot simply march into Mordor with only 9 operating systems.

---

### Post by Panarchy on 2009-02-02
^T3kG33k: Ah! How many do I need in order to march into Mordor?

> **mb_webguy said:**
> Unix-based operating systems (including Mac OS X) can each fit happily on an 8-12GB partition.

If you really want to get fancy, you can add a small (1-5GB) /home partition for each of the Unix-based OSes.

And as far as the bootloader, I'd just chainload GRUB, as others have suggested.

Thanks. However, I'd have to say, that with my 1TB hard-drive, that there would be plenty enough space to allow for a 100GB partition for each of my operating systems.

:popcorn:

Temüjin: Thanks, already using it! (svn version)

**I would like some help (please) in writing the menu.lst so that I can put my custom menu.lst onto the LiveCD.**

Please[LIST=1][*]Tell me which LiveCD to use (that will boot into my partitions via GRUB, Lilo or BCD)
[*]Write my menu.lst[/LIST]Thanks in advance,

Panarchy

---

### Post by Panarchy on 2009-02-02
Hello

I've changed my partitioning schema for various reasons.

Here is my *NEW* partitioning schema;

[IMG]http://i43.tinypic.com/72g9z6.jpg[/IMG]

Please help me create my menu.lst, so that I can put it into a LiveCD/BootCD which will contain GRUB and allow me to boot into any partition on my 1TB hard-drive, in case something happens to my computer and I can't access the GRUB menu (e.g. Error 17).

Thanks in advance for any help given in creating my menu.lst,

Panarchy

---

