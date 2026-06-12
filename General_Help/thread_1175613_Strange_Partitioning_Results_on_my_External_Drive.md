---
title: "Strange Partitioning Results on my External Drive"
date: 2009-06-01
forum: General Help
---

### Post by Randypan on 2009-06-01
Hi Everybody, this is my first post.

I' m new to Ubuntu (and linux in general). The last few weeks I've been using Ubuntu Jaunty, paired with Vista in a dual boot configuration on my laptop and it's doing great. I use a 1 TB (kind of monstrous for my needs) Seagate external drive for storing my mp3s videos etc. It was using NTFS format up to this day, when I decided to format it into ext3 to avoid defragmentation -since I plan on abandoning Vista for everyday use. 
  
  I run Parted Magic from the live cd, shrunk the NTFS partition of the drive, created a new ext3 partition and copied my files over to the new partition. Then I deleted the old one and tried to move the new one to the beginning of the drive and stretch it to it's full capacity.
  The process lasted roughly 15(!) hours and I got an error message in the end. I found out then, that the files were copied over and moved just fine and were all intact, but the unallocated space was still there, so I run again the resizing operation. The results werte odd:
  The status screen showed that my used space was about four times bigger than the real thing (it was 150 Gb and now it says 600Gb out fo 1Tb !)
  I booted Ubuntu and it had a different opinion... My external drive Showed up as 300 Gb large, with the original 150 Gb worth of data in it. What went wrong?

I know that this issue is not directly related to Ubuntu but it's here in this forum that I have found most of the solutions to any linux-related problem I've encountered, so I guessed there would be a guy or two around here with the answer.

If there are things that I haven't specified about my hardware it's because I didn't know what would be useful and I didn' want to make a lenghthy post even lenghthier.

Thanks in advance, Randypan

---

### Post by Randypan on 2009-06-01
I run scan-for-errors on the partition with gparted and it fixed itself...

---

