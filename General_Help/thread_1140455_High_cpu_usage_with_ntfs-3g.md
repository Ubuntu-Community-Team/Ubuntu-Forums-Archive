---
title: "High cpu usage with ntfs-3g"
date: 2009-04-27
forum: General Help
---

### Post by poohter on 2009-04-27
Lately I have been getting 48% and higher cpu usage when downloading torrents with transmission onto a WD passport formatted in ntfs. The passport is not fragmented and this has really only started happening recently.

I should note that the drive is an external usb which I have been using forever to d/l torrents to and only recently have I noticed heavy cpu usage.

---

### Post by 666f6f on 2009-04-28
I'd search in [http://forum.ntfs-3g.org](http://forum.ntfs-3g.org) using this Google Query "site:forum.ntfs-3g.org torrent cpu"

---

### Post by sotiriss on 2009-04-30
poohter i'm having exactly the same problem. It also happends when i download files from firefox to my ntfs partition.

---

### Post by unc0nn3ct3d on 2009-07-06
Same problem here but it occurs when the system is idling and doing absolutely nothing.. CPU usage from ntfs-3g sits around 70-80% but I imagine it would be 100% if there were no other processes using the CPU.

I ran ntfsfix on the main partition on the drive abut that didn't do a thing, going to try rebooting into windows, run chkdsk and defrag it.

---

### Post by niksakl on 2009-11-11
I have the same problem here.
I have high cpu usage when using my ntfs partitions.
When I copy big files or multiple files on it, my cpu (q9550) works almost on 100% load, even causes the system to be unusable from time to time during the copy. This is a terrible performance issue for me, plz suggest a solution!
I am running kubuntu 9,10 64 bit, but had these problems in 9,04 32 bit too... I hoped this matter would be solved when i upgraded to 9,10 with a clean install, but unfortunately didn't happen...

---

### Post by huygens on 2009-11-16
It seems that this is a known bug, without a work around as of now: [https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/392204](https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/392204)

---

### Post by niksakl on 2010-03-04
Also pls everybody have a look at this one, in my case i think it's what i am looking for but for me no solution so far...

[http://ubuntuforums.org/archive/index.php/t-1152176.html](http://ubuntuforums.org/archive/index.php/t-1152176.html)

---

### Post by achilleas.k on 2010-08-09
Apologies for resurrecting dead threads but I had the same problem after getting a replacement drive for a damaged one. Now since the two drives were the same I started wondering what could have caused this and then I remembered I changed some BIOS settings when I installed the new one while I was checking on it. Specifically, I enabled 32 bit file access and SMART monitoring. 

The problem mostly occurred when I was copying large files over the network onto the Linux mounted NTFS drive. Network usage would drop substantially (~10 mbps instead of over 90 that I normally get) and the mount.ntfs-3g process would hit near 100% CPU usage.

I have disabled 32 bit file access and I'm going for it again. I'm getting great network speeds and the process is keeping itself pretty low, at around 20% usage, sometimes going up to 40% but never above 50%.

I can't be sure whether this is the same cause for everyone's problems, but it seems to have done it for me.

---

### Post by gradinaruvasile on 2010-08-09
NTFS is not fully supported under Linux. Ntfs-3g is a reverse-engineered driver. So it has its problems.

I saw this isssue on every single computer that had Ubuntu + ntfs partitions.

I just reformatted everything to ext3/ext4 and had no problems since.

You might file a bug against ntfs-3g.

---

### Post by achilleas.k on 2010-08-09
> **gradinaruvasile said:**
> NTFS is not fully supported under Linux. Ntfs-3g is a reverse-engineered driver. So it has its problems.

I saw this isssue on every single computer that had Ubuntu + ntfs partitions.

I just reformatted everything to ext3/ext4 and had no problems since.

You might file a bug against ntfs-3g.

While I understand that Ntfs-3g can not be expected to work as well as "native" filesystem drivers, I don't think it's proper to chuck every problem or slowdown onto the "don't expect it to work" pile and call it a day. I've noticed a considerable increase in performance by changing that setting and thought I'd share it with the rest of the community.

If others who have had this problem find that it gets solved this way and for some reason or another require to have an NTFS drive (thereby not being able to reformat every drive to ext#), I believe it's still worth mentioning that workarounds exist.

I personally trust the ntfs-3g driver more than I do an ext3 driver for Windows, so if I'm going to be using a filesystem for a drive that should be accessible by both OSes, it's going to be NTFS.

---

### Post by oldos2er on 2011-11-06
Closed, necromancy.

---

