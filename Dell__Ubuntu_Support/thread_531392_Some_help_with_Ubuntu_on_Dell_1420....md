---
title: "Some help with Ubuntu on Dell 1420..."
date: 2007-08-21
forum: Dell  Ubuntu Support
---

### Post by MrSootentai on 2007-08-21
I am having some problems getting my Dell to dual boot Ubuntu and Windows Vista. The main problem I have is that I want to keep my Dell MediaDirect partition.

Can anyone help me out here? I have no idea how to do this. Last time I tried on the laptop, I didn't understand where to install the GRUB loader.

I didn't understand where to install the Ubuntu, where SHOULD I install it? I have to use the Alternate Ubuntu CD to install it because the LIVE distro CD boots with an error.
Here's a screen cap from my Windows Vista Disk Manager....
[http://img32.picoodle.com/img/img32/9/8/21/f_DiskManagemm_763d5c6.jpg]("http://img32.picoodle.com/img/img32/9/8/21/f_DiskManagemm_763d5c6.jpg")
I plan on using the UNALLOCATED space to create the Ubuntu 'ext3' and 'swap' space. I just don't understand what to do when I am done installing Ubuntu. It asks for where to install GRUB and it's default location is (hd0) but if I do that it messes it up.

I know this may seem like a lot but can anyone help me out here??

---

### Post by jnorthr on 2007-08-21
Here is a link to the grub documentation [http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/) for version 0.97 of supergrub.

When you reboot your machine from the live distro CD, do you see any menus or GUI presented by either vista or ubuntu ? In order for ubuntu (or any other o/s) to be used on a machine along with windows, a special utility called a super grub ( grand unified uinversal booter?) is written to the first sector of your first hard disk - hd0. Grub is given control first when your machine is booted. It should examine the various partitions on your machine and present you with a list of which o/s partitions you can boot from. 

You are correct in that grub will blitz your hd0 sector zero but by doing so in the future, when you next reboot after a complete installation, you will be presented with a grub menu to offer you a choice as to which o/s to choose.

Good idea to use that spare room for ubuntu partitions. Put the swap partition first (size about twice ram size ) then allocate the remainder for / - the root. 

You can review [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty) for a beginner's howto. Once you digest that, come back here with more questions before you try it again. Best get some backups done of your vital data BEFORE you do anything else. You never know.

---

### Post by sebald on 2007-08-22
ah, yes, just what I was going to ask.

Same here, the Feisty live CD wouldn't boot. 

I ran Knoppix live CD and it booted fine (but no wireless). parted shows an interesting scheme: a little 70mb partition (FAT), the main OS partition (NTFS) , and a smaller partition (10GB?, NTFS) with Windows restore files.( I think it's all available on the disks that came with the machine if you mess things up royally and want to go back to the factory default)

So are we safe to take some space from the main Windows partition and let grub install as usual?

My version has builtin wireless b and g (didn't go for the n, too new), the T7300 processor, and the GeForce video chip option. Hope Feisty knows what to do with the video :confused:

---

### Post by sebald on 2007-08-23
Well, I took courage and shrank the main partition to free up space and used the resulting space... 

Well, the Feisty alternate CD didn't find network (hardwired) during install, and didn't end up installing anything usable... the DVD again couldn't find network, but installed a system where the X server failed to start, but I at least have a command line at which I can login! That's getting somewhere, I guess.

Some other forums are saying that Gutsy betas are resolving these issues, but I will poke around a bit more for answers.

After install, the grub screen shows the usual Ubuntu entries, plus "Windows Vista/Longhorn (loader)" which loads Vista just fine, and "Windows XP Embedded", which is probably the small 70mb partition that you can access somehow to boot and restore your Vista system.

More to come...

---

### Post by MrSootentai on 2007-08-23
> **sebald said:**
> Well, I took courage and shrank the main partition to free up space and used the resulting space... 

Well, the Feisty alternate CD didn't find network (hardwired) during install, and didn't end up installing anything usable... the DVD again couldn't find network, but installed a system where the X server failed to start, but I at least have a command line at which I can login! That's getting somewhere, I guess.

Some other forums are saying that Gutsy betas are resolving these issues, but I will poke around a bit more for answers.

After install, the grub screen shows the usual Ubuntu entries, plus "Windows Vista/Longhorn (loader)" which loads Vista just fine, and "Windows XP Embedded", which is probably the small 70mb partition that you can access somehow to boot and restore your Vista system.

More to come...


Following the guide here...[http://ubuntuforums.org/showthread.php?t=509408]("http://ubuntuforums.org/showthread.php?t=509408")
I was able to get it booted and running without any problems.
But whenever i pressed the MediaDirect button the bootloader got screwed over. To fix that I put in my Vista Reinstallationg cd to fix it [PM me if you want some help with that].

But everything had worked great until my wireless and network adapter didn't not work at all. I started messing with the packages and ended up screwing up the whole thing.

I am going down for a bit to reinstall it and get it working again.

If I get the wireless or wired working I will post up here again.

---

### Post by mike999999 on 2007-08-23
I know that the media direct button turns on  (and off) the media direct partition. So if you get the error 17, you can turn off the system, press the button again, and it will boot normally. 

What did you do with the vista disk that fixed it?

---

### Post by MrSootentai on 2007-08-23
Once I got that GRUB Error 17,
I put in my Vista Installation Disc that I got with my laptop and let it run on boot. [Press F12 on boot and select CD drive].
Let the CD boot, after it asks you the normal language info you should have an option to Install Vista or Repair.
Choose repair and let Vista auto-repair if it can.
If it can't, click that Repair button again on the menu and choose the command prompt option after it shows you have no Vista installation on the computer.

Type *bootrec /rebuildbcd*
then *bootrec /fixmbr*
then *bootrec /fixboot*.

Worked for me three times already.

But now I may have to get a system exchange because my laptop's battery is loose to the point that it seems like it will fall out soon.
And my bluetooth adapter isn't working under Vista anymore for some reason.
Dell customer care should call me back soon to talk about it...

---

