---
title: "How safe is gparted on non-ext partitions?"
date: 2009-05-18
forum: General Help
---

### Post by maflynn on 2009-05-18
I'm planning on altering my HFS+ (Mac partition) and EXT3 partitions, giving more space from one to another but I really don't want to corrupt the HFS+ (nor the ext), so this leads me to the question how stable is gparted on non-native partitions.

---

### Post by colin.p on 2009-05-18
I have no idea about HFS file system, but I just adjusted my NTFS down 10 GB and increased my / partition by same amount. I also adjusted my swap down to 1 GB and increased the size of my home partition. I booted into 8.10 and then tried my XP and all is well.
So I would say it's pretty safe and very easy to do, at least for windows, but if anyone has tried Mac I'm sure they will chime in soon.

YMMV
Colin

---

### Post by maflynn on 2009-05-18
I was tempted to put this thread in the apple sub forum here but I thought that its a more general question with regard to gparted. 

In searching I did find this [thread]("http://ubuntuforums.org/showthread.php?t=972145&highlight=gparted+hfs")

> 
I know this is an old topic but I just wanted to add my experience with partitioning using Leopard's Disk Utility and gParted. In a nutshell, to avoid having to go through what could be an annoying time consuming task of completely erasing your Mac disk and then restoring a back up because Disk Utility fools you into thinking there's no way to delete or resize or otherwise manipulate partitions of ANY file system (even the HFS+ which is Apple's own file system) on your disk, [COLOR="Red"]once you get Ubuntu up and running, I'd recommend sticking to gParted almost exclusively for all future partition creation, deletion, and resizing, be it for Mac or Linux partitions; post Ubuntu install, Disk Utility has only been reliably useful for formatting an already mapped but unformatted partition for Mac as HFS+ or enlarging (using unallocated space created in gParted) or shrinking a Mac HFS+ partition [/COLOR]

(emphasis not added)

So at least in thread it states that while gparted is not officially supporting HFS+ it does work on it and it does a better job then OSX's disk utility.

I keep my OSX partition backed up thanks to Time Machine so I'll probably pop in my gparted-live disc and let this run over night

---

### Post by coffeecat on 2009-05-18
Take care with HFS+. What Gparted doesn't tell you (or not that I've noticed) is that when it creates a HFS+ partition, it's the non-journalled, not the journalled, version of HFS+. And you need hfsutils and possibly another couple of hfs* packages installed from the repos to be able to create them in the first place.

I discovered this the long way round (by dint of much experimenting and head-scratching) because I couldn't understand why a HFS+ partition created with my Mac was read only in Ubuntu, whereas a HFS+ partition created in Ubuntu was read and write in both OSs. Of course, the Mac Disk Utility defaults to the journalled version, and when I chose non-journalled I was able to write to a HFS+ filesystem created on my Mac.

Whew!

Then there's the complication of Apple and MSDOS partition tables. Just have a look in Device > Create Partition Table in Gparted and you'll see what I mean. :(

But I have no experience of resizing HFS+ partitions. I've never worked out how to do this in the Apple Disk Utility (if indeed it's possible) and I haven't attempted it in Gparted.

You ask about non-native filesystems. If you're thinking of NTFS, Gparted creates and resizes NTFS partitions that XP is happy to use. It creates NTFS partitions that both Vista and Windows 7 are happy to use (in my limited experience), but don't try to resize a NTFS partition that you want Vista (or W7) to use. Linux forums are awash with horror stories about this.

---

### Post by coffeecat on 2009-05-18
I posted just as you posted and I didn't know about that thread. Useful - thanks.

What I don't understand about the Apple Disk Utility's inability to shrink a HFS+ partition, is that this functionality is built-in (or so I understand) to Boot Camp, whereby you shrink the Apple root partition to give yourself space for <shudder> a Windows partition on the same drive.

Ho hum.

---

### Post by maflynn on 2009-05-19
I may hold off on using gparted on my HFS+ partition, while I do have recent backups, restoring it will be a major waste of time.  Besides I just finished reinstalling/restoring my programs and data because I installed a new 500gig drive.

There's a program called iPartition available for OSX that is designed to non-destructively alter HFS+ partitions, I may spend the money on that and then use gparted for EXT partitions.  I hate to spend $$ on such a uni-tasker that I'll not use very often

---

### Post by HavocXphere on 2009-05-19
> **colin.p said:**
> I just adjusted my NTFS down 10 GB and increased my / partition by same amount. I also adjusted my swap down to 1 GB and increased the size of my home partition.
Now that sounds like a good plan.

More on-topic: I'd definitely make major backups first, but I haven't heard of gparted being unstable/screwing up things.

If you can, make sure that your PC is on a UPS while you are doing this. Cause if the power goes during the change then things are going to hit the fan with or without gparted. If you don't have access to a UPS then do the change during non-peak electricity usage times since the mains are generally a bit more unstable during peak.

---

