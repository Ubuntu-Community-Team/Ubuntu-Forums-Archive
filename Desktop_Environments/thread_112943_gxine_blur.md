---
title: "gxine blur"
date: 2006-01-05
forum: Desktop Environments
---

### Post by azelter on 2006-01-05
When I updated my computers to breezy a couple of months back, I found that all the avi files (movies) from my digital camera that I played back with gxine were now blurry. Whenever there is movement in the video, gxine makes everything blurry (as if the shutter speed of the video camera had been really slow). This wasn't the case in any previous version of gxine. The odd thing is that breezy still plays these videos fine using xine. I thought the two programs had the same guts and so wouldn't expect one to do one thing and the other another. This change happened on four different computers that I have upgraded, including one Mac running breezy for ppc. The problem is still there on the computer that I have running Dapper Duck too (which runs gxine 0.5.something rather than the 0.4.something that breezy uses). If anyone has any ideas or has had this problem too - I'd love to hear about it as it's a pain not to be able to use my favorite player for avi files. 
Thanks!
Alex

---

### Post by moontide on 2006-01-06
I had a problem with totem and xine-ui running badly. lots of choppy stop start movement. I ran the command "xine-check" and xine reported several weaknesses in my setup (Ubunto 5.10) as follows:

xserver didnt set up any HTRR support, no MTRR ranges set up for graphics card.(MTRR support not utilised) mabey upgrade xserver. 
Install xine-lib
run command: "hdparm -d1 /dev/hdd". I installed xine-lib and ran the hdparm command.(this fixed sticky video performance, but needs to be added to a boot time file to work every time). After using the hdparm command my video's run perfectly.
Hope this helps.

---

### Post by azelter on 2006-01-06
Thanks but those arn't the problems. DMA is set and hdparm.conf is optimized for my systems. Also, gxine plays dvds from the dvd drive and from the hard drive perfectly. This problem seems to be only with my avi files. Plus the optimizations you mentioned would increase the perfomence of all the video players on the system, whereas xine plays my avi files fine and I only have problems with gxine.

---

### Post by moontide on 2006-01-06
[QUOTE=azelter]Thanks but those arn't the problems. DMA is set and hdparm.conf is optimized for my systems. Also, gxine plays dvds from the dvd drive and from the hard drive perfectly. This problem seems to be only with my avi files. Plus the optimizations you mentioned would increase the perfomence of all the video players on the system, whereas xine plays my avi files fine and I only have problems with gxine.[/QUOTE]

There is so much to this stuff, now I need to find out about hdparm.conf. I checked my previous install (Libranet 3.0) and that wasn't optimized either It seems, because it was all comented out.

---

