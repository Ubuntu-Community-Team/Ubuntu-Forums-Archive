---
title: "Installing XP besides Ubuntu"
date: 2006-07-07
forum: Desktop Environments
---

### Post by Skerit on 2006-07-07
I thought it would go quite smooth ... it did not!
Seems like a bad movie tagline, that's how it feels like.

I have 3 HDs, Ubuntu Dapper is my only os on the first one (and the entire system) but now I need to install XP besides it. I did this, it wrote over the MBR, as I thought it would. After a reboot nothing loaded. No windows, no grub. 
I wanted to do the "Restore Grub" trick, by "reinstalling" ubuntu, and skipping to installing the boot loader but I couldn't mount my root partition in the partition manager because ubuntu doesn't recognize any partitions on my first hard drive.

When I'm in the Windows installer all three partitions are there.  So I don't really know where I go from here... 

[SIZE="1"]I'm almost ashamed to say it; I need windows. In 4 months I'll be using linux for an entire year, I almost felt like a traitor when I had to install windows for school on the laptop (the one I am on now) 

During all this time I came to love the entire ubuntu philosophy even more and I'm happy where I am. Unfortunately; though heave efforts are being made, Linux non-linear video editing still isn't what it's supposed to be. (There's still no programme to premiere like gimp is to photoshop) I've tried Jahshaka, even mainactor, never really could install Diva, but it didn't matter, neither where good enough, I have to use Premiere Pro 2.[/SIZE]

---

### Post by jbruelas on 2006-07-07
Have you tried to install Windows XP first?

I have done the installation without any trouble (first Win2k, next Winxp, and last, but not least, Ubuntu, which is my main environment

Or maybe you could give a try to a software calle System Commander ([www.v-com.com](www.v-com.com))

Hope this can help you out

Best regards from Mexico

JBRuelas

---

### Post by Skerit on 2006-07-07
> **jbruelas said:**
> Have you tried to install Windows XP first?

I have done the installation without any trouble (first Win2k, next Winxp, and last, but not least, Ubuntu, which is my main environment

Or maybe you could give a try to a software calle System Commander ([www.v-com.com](www.v-com.com))

Hope this can help you out

Best regards from Mexico

JBRuelas


I would happily like to install XP first and then reinstall Dapper but whenever I reinstall XP nothing happens, it sitll won't load. So basically, I can install the Windows MBR stuff, but it won't work and I can't install GRUB or LILO which would work if I could install it.

Not even deleting the 2 ext3 partitions (which weren't important; / and /opt) helped...

---

### Post by VirtuAlex on 2006-07-07
> **Skerit said:**
> I have 3 HDs

Are they 3 physical HDs? Then have you tried to switch the boot sequence in BIOS or switch HDs cables? I believe Win likes to be on the first HD where the boot record is.

---

### Post by teet on 2006-07-09
I think you need to boot up with your windows XP install CD.

Choose the Repair installation option.

Then at the command prompt type

fixmbr       or       fixmbr \Device\HardDisk0

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)

Then install windows.

Then install ubuntu.

-teet

Edit:  the command may be 'format /mbr' ... it's been awhile since I've done it.

---

