---
title: "Update renders my xps m1330 unusable"
date: 2008-12-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by johnlugh on 2008-12-16
Hi, I'm running Intrepid and after an update last night- everything's gone downhill. 

When I boot my computer, I get a blank screen which slowly becomes striped and this is all I see. I'm pretty sure that Ubuntu is still loaded but I don't even see my BIOS load or grub boot options normally. Just the striped screen.

Funny thing is that once in a long long while, I do see these options and after I enter recovery mode and fix the XServer, everything loads up fine. After a couple of minutes however, the text and screen becomes tinged with blue and everything hangs. 

Am I right in saying that the problem is the xorg.conf file? Something to do with the update caused this incompatibility but I can't figure out what. The current xorg.conf file seems to be very simplistic (it's the default one set when I chose the fix XServer option in recovery mode). It doesn't say anything about nvidia or anything. 

Btw, if there's anyone with an M1330 and has Intrepid with current updates working- could u possibly help me out by pasting your xorg.conf file here? 

Any help would be realllly appreciated, I've been extremely frustrated with this and my laptop is my life :P

---

### Post by Zeedok on 2008-12-17
Sorry Pal, welcome to the frustrations of the m1330.  I don't think your problems have anything to do with Ubuntu.  The m1330 ships with an Nvidia card that has proven faulty (as do a large number of laptops from other manufacturers I might add).  The symptoms are freezing, intermittent stripes of colour on the screen and ultimately failure of the machine to boot-up at all.  I have already had the motherboard (which the graphics card is soldered to, hence one component fails, the whole thing gets replaced) _twice_.  I hope your machine is still under warranty - the most recent replacement is supposed to use 'a new batch' of the GPU which will not repeat the error - I'll be extending my warranty anyway just in case.

Here's my [post]("http://ubuntuforums.org/showthread.php?t=729692") from the first time it happened to me and [here]("http://en.community.dell.com/blogs/direct2dell/archive/2008/07/25/nvidia-gpu-update-for-dell-laptop-owners.aspx") is the official blog post from DirecttoDell.

Hope this info is helpful - I really hope they sort this issue out properly because I love my laptop in all other respects.

---

### Post by johnlugh on 2008-12-17
Ok, thanks for breaking the news to me. Feel a bit silly that I spent all that time trying to fix it- at least i'm still under warranty!

Dell technician is going to replace the motherboard soon, hope it all goes well. Have you got the most recent batch with the new GPU? Any issues with it? Thanks.

---

### Post by Zeedok on 2008-12-17
My second GPU died around the time of the intrepid release (late October) and I haven't had any problems so far.  Fingers crossed the "new batch" has slved the problem for all of us.

Good luck.

---

