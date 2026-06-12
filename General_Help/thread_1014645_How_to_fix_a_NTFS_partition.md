---
title: "How to fix a NTFS partition?"
date: 2008-12-18
forum: General Help
---

### Post by XtremeGamer99 on 2008-12-18
I was gaming on my Windows XP partition last night when I got the BSOD. Eh, no save game there, but when I rebooted and selected Windows XP from the GRUB menu, this:

```
Booting 'Microsoft Windows XP Professional'

root  (hd0,0)
 Filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1
```

This scared me senseless. So I booted up into Debian, which is run off of my second hard drive. Checking /dev, I confirmed that the first hard drive (sda) and the Windows partition (sda1) were registering, but when using mount, I get this:

```
~$ mount -t ntfs-3g /dev/sda1 /mnt/ntfs -o force
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.
```

So, I think I have a corrupted partition. I have some data on that partition that is valuable, and I don't have any recent backups (as a matter of fact, I was planning to to backups this weekend and reload Windows =/). Anyone know a way to fix this?

BTW, I know this isn't a Ubuntu/Linux question, but whatever way I do fix this will have to be from a Linux distro since I can't boot into windows.

---

### Post by Polygon on 2008-12-18
do you have a windows cd lying around anywhere? I know on my vista live cd you can click on this thing and it will attempt to fix any problems a ntfs partition has. If you have an xp cd, i can see if i can figure out something for you

and what you saw first with the 'chainloader' and all that, thats normal, thats just the GRUB boot entry, its hanging there because it cant load the partition cuase its like corrupted

---

### Post by XtremeGamer99 on 2008-12-18
> **Polygon said:**
> do you have a windows cd lying around anywhere? I know on my vista live cd you can click on this thing and it will attempt to fix any problems a ntfs partition has. If you have an xp cd, i can see if i can figure out something for you

and what you saw first with the 'chainloader' and all that, thats normal, thats just the GRUB boot entry, its hanging there because it cant load the partition cuase its like corrupted

Yes, I have the XP CD. Problem is, though, is that I just tried booting from it and it didn't work. It would boot from the CD after displaying "Press any key... yada yada", then it would display the "Setup is checking your system hardware", the screen goes black and then it hangs.

I'm not sure why it hangs; I've installed Windows on this computer multiple times without running into this problem. Anybody have any insight into this as well?

---

### Post by jrusso2 on 2008-12-18
> **XtremeGamer99 said:**
> Yes, I have the XP CD. Problem is, though, is that I just tried booting from it and it didn't work. It would boot from the CD after displaying "Press any key... yada yada", then it would display the "Setup is checking your system hardware", the screen goes black and then it hangs.

I'm not sure why it hangs; I've installed Windows on this computer multiple times without running into this problem. Anybody have any insight into this as well?


try running chkdsk -f from the recovery console

---

### Post by Polygon on 2008-12-18
aha

i used to have that exact same problem with my xp sp1a cd

turned out the problem was, xp was checking your disks, and it would try to scan the linux drives, and the fact that it was formatted with ext3 or whatever would blow its mind, and it would crash. Unplugging the linux drive did the trick and next time i tried it, i was able to use the xp cd sucessfully 

im not sure if any programs exist on linux to check and repair ntfs filesystems.....maybe try putting it into an existing windows computer and then repairing it there?

---

### Post by XtremeGamer99 on 2008-12-18
> **jrusso2 said:**
> try running chkdsk -f from the recovery console

Well, I would. However the setup doesn't get past the scanning portion as I said. =)

> **Polygon said:**
> aha

i used to have that exact same problem with my xp sp1a cd

turned out the problem was, xp was checking your disks, and it would try to scan the linux drives, and the fact that it was formatted with ext3 or whatever would blow its mind, and it would crash. Unplugging the linux drive did the trick and next time i tried it, i was able to use the xp cd sucessfully 

im not sure if any programs exist on linux to check and repair ntfs filesystems.....maybe try putting it into an existing windows computer and then repairing it there?

Seems logical. Microsoft has a problem recognizing anything they haven't made themselves. I'll give that a try. =)

> and the fact that it was formatted with ext3 or whatever would blow its mind

That made me lol quite hard. xD

---

### Post by jrusso2 on 2008-12-18
You know you can also run the recovery console from the XP CD.

---

### Post by jerome1232 on 2008-12-18
Well there is ntfsfix, it's capable of fixing basic ntfs errors, if you install ntfsprogs you'll get it. 

With that being said I would do everything I can to use chkdsk instead, it's made by the guys that made the nt file system ;)

And uhhhhhhh personally if you want to try ntfsfix I would make an image of your drive then run ntfsfix on the image, that way you don't risk destroying any data, just the image. (I don't know how good ntfsfix is I've only used it for removing hibernation files/unclean log files).

---

### Post by XtremeGamer99 on 2008-12-18
> **Polygon said:**
> aha

i used to have that exact same problem with my xp sp1a cd

turned out the problem was, xp was checking your disks, and it would try to scan the linux drives, and the fact that it was formatted with ext3 or whatever would blow its mind, and it would crash. Unplugging the linux drive did the trick and next time i tried it, i was able to use the xp cd sucessfully 

im not sure if any programs exist on linux to check and repair ntfs filesystems.....maybe try putting it into an existing windows computer and then repairing it there?

No good. Still hangs after scanning the hardware. Linux was on the second drive, while Windows was on the first drive. Grub, on the other hand, was installed on the first drive I think. But anyway, I disconnected the linuc drive and it still hangs.

I can't install the drive in any other computer since it's a SATA drive, and my PC is the only one in the house that handles SATA drives... =(

So... now what? I can't boot into rescue mode on the CD, and I can't boot into the actual partition... >.<

---

### Post by Polygon on 2008-12-18
> **jrusso2 said:**
> You know you can also run the recovery console from the XP CD.

point is, the xp cd is crashing before he even gets a chance to select the option to use the recovery console.

---

### Post by XtremeGamer99 on 2008-12-18
> **jrusso2 said:**
> You know you can also run the recovery console from the XP CD.

... That's exactly what I said. I tried booting from the CD, and it gets to the "Scanning Hardware" portion then dies.

> **jerome1232 said:**
> Well there is ntfsfix, it's capable of fixing basic ntfs errors, if you install ntfsprogs you'll get it. 

With that being said I would do everything I can to use chkdsk instead, it's made by the guys that made the nt file system ;)

And uhhhhhhh personally if you want to try ntfsfix I would make an image of your drive then run ntfsfix on the image, that way you don't risk destroying any data, just the image. (I don't know how good ntfsfix is I've only used it for removing hibernation files/unclean log files).

thanks for the info, I'll keep that in mind in case all else fails. =)

---

### Post by jrusso2 on 2008-12-18
I would say its a hardware issue then.  There are some discs around that do hardware diagnostics and hard drive diagnostics if you can search for them.

---

### Post by XtremeGamer99 on 2008-12-18
> **jrusso2 said:**
> I would say its a hardware issue then.  There are some discs around that do hardware diagnostics and hard drive diagnostics if you can search for them.

I don't think it's a hardware issue: Knoppix works, which means the DVD drive works. The HDDs themselves work as far as I'm aware of. Video card (8800GT) works. I can boot from other Linux CDs, such as Debian and Ubuntu. I've never had any problems with my hardware...

---

### Post by XtremeGamer99 on 2008-12-18
Is there a way to make a chkdsk floppy? I have a floppy drive and I could try that...

---

### Post by XtremeGamer99 on 2008-12-18
woot! Good news: Got the XP CD to boot.

I had to switch the first and second drive around, making the Linux drive the 'primary' SATA and the corrupted Windows drive the 'secondary'.

Now I've just got to figure out how to use the recovery mode on the CD. Never used it before now... <_<

---

### Post by jerome1232 on 2008-12-18
You should be able to press 'r' to drop to a recovery console then arrive at a command prompt.

chkdsk /f c: I think is the command that'll check it (I haven't used chkdsk since like......... I've used win98 lol so my syntax may be off a bit)

---

### Post by TheLocalGraveDigger on 2008-12-19
glad switching the drives around for you worked but my problem is the same thing happens with one drive with a ext3 partition in spot 1 and a NTFS in spot 2. Chopping the drive in half to separate the ext and NTFS seem a little extreme to me so now im almost out of options.

---

