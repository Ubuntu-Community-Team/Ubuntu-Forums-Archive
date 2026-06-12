---
title: "Errors while booting to kernel and starting RAID + most common xsession-error"
date: 2006-03-04
forum: Desktop Environments
---

### Post by Ragzy on 2006-03-04
Greetings!
First, im not sure if this is the right part of the forum to post this, sorry if I got this wrong. Second, Im new to Linux and Ubuntu, so this might be an easy one to solve.

So, here is my problem (the most annoying one) I do have some more errors in my xsession-error log. None of them is something I notice anything about, but the booting one is a pain, cuz it slows down the startup.

This is what it looks like:
fist I get: Booting to kernel...
Then
[4294639.873000] WARINING buffer I/O error on device hda6 logical block [31878]
repeatedly like 10 times (numbers change)
Then it looks almost the same when it starts RAID... I dont really know what raid is, other than something with the partitions. 

My disk manager says hda6 is a Windows virtual  FAT (vFAT)
accespath: none 
Size ~15MiB (free space not available)
Status: inaccessible.

I believe that I created it some time ago when I had XP and wanted to try Mandrake. I used partition magic and it was a partition needed for bootmagic or something.

Now I have Ubuntu (Breezy) on hdb along with an NTFS partition.
On Hda I have a file storage (music games videos etc.) and a Windows XP partition. And this onld 15Mib FAT partition.

I use Grub as boot manager. Windows and storage partition is both mounted without any problems. I have no idea why Ubuntu even tries to access hda6 on startup...


ANOTHER this, wich is my biggest problem in xsession-errors is a frequently reaccuring (spammed) message is:
** (gnome-cups-icon:8773): WARNING **: IPP request failed with status 1030

would be greateful for help on these two topics. I will now post my xsession-error log here..dont want to take up too much or your time. 

I have actually been trying to search for the two on google and on this forum, without any luck. 

And again, sorry if this is posted in the wrong forum, perhaps any kind moderator could move it if it gets on anyones nerves=P

Thanx=)

---

### Post by SpectralDesign on 2006-03-04
Well, I can't really help you out much, other than to provide a touch of insight into what raid is... it stands for Redundant Array of Inexpensive Disks... when used properly, it means that if one disk-drive fails (a not unheard of occurence) you don't lose any data because you can do two handy-dandy things:

striping: writing data to multiple drives simultaneously, this gives you more throughput.

redundancy: holding any portion of the filesystem on more than one disk, so that if there is a failure of a disk, the system can keep running without data loss.

It works best if it's hardware raid, because the hardware is designed specifically to manage the I/O and you get the best performance.  Software RAID would tend to be slower for most uses (though at the speed of today's drives, chances are you won't notice unless you have some heavy I/O going on!

---

### Post by Ragzy on 2006-03-05
ok, thanx for the info.
Anyone who can tell me if this I/O is a serious problem? /Is the partition needed for Partition magic? If not, is there any way to bypass it? I tried to check the disk with the original disk check on windows, wich ofcourse wouldnt run..is the partition damaged??

---

