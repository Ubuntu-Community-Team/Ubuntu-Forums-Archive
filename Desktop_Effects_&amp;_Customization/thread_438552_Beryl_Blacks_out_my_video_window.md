---
title: "Beryl Blacks out my video window"
date: 2007-05-09
forum: Desktop Effects &amp; Customization
---

### Post by Goombie on 2007-05-09
So, I've been playing with Beryl version 0.2 for a day or so now, and I only have one problem with it: When I play a video file, I can't see the video! I try moving the player around, using VLC Media Player, changing the VLC options - no luck. I still get just a blank window when I play a video. I've tried it with different videos, too. Same result. Does anybody know how to fix this?

System info:
Ubuntu 7.04, dual-boot with Windows XP SP2
Graphics card: ATI Mobility Radeon 9100, 128MB RAM, open-source driver, using AIGLX 

I followed the instructions at [http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon") to install my drivers, then I installed Beryl and Emerald through the Add-Remove interface. 
Beryl is a great little program, and this video problem is the only thing stopping me from using it. :(

---

### Post by kaede on 2007-05-21
i try to play video using totem while running beryl. amazingly there's no problem with it. wonder what really caused the problem VLC or Beryl?

---

### Post by Goombie on 2007-05-22
Well, in this case it was Beryl, since I had the problem no matter what player I used. Thankfully, I got the problem fixed, so I hereby declare this topic useless and ready for vaporization. :)

---

### Post by abbot on 2007-05-22
Please post how you fixed the problem for people with the same problem who find this thread.

---

### Post by Goombie on 2007-05-22
Oh, yeah. Why didn't I think of that? :)
Ok, in a Terminal, type 'gstreamer-properties' without the quotes.
Go over to the video tab, and look for the section marked 'default output'.
Change the 'Plugin:' selection to 'X Window System (no Xv)' .
If you like, you can click the 'Test' button to verify that it works.
Close the dialog box, and everything should be good now.

---

### Post by madjr on 2007-05-30
This thread may also b of help for others with similar video problems or bluedots when using beryl

[http://www.linuxquestions.org/questions/showthread.php?t=496627](http://www.linuxquestions.org/questions/showthread.php?t=496627)

---

### Post by blueb73 on 2007-07-08
> **Goombie said:**
> Oh, yeah. Why didn't I think of that? :)
Ok, in a Terminal, type 'gstreamer-properties' without the quotes.
Go over to the video tab, and look for the section marked 'default output'.
Change the 'Plugin:' selection to 'X Window System (no Xv)' .
If you like, you can click the 'Test' button to verify that it works.
Close the dialog box, and everything should be good now.

woot woot, that worked!

---

