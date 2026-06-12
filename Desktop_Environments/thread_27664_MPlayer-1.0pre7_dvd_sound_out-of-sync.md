---
title: "MPlayer-1.0pre7 dvd sound out-of-sync"
date: 2005-04-17
forum: Desktop Environments
---

### Post by vaskark on 2005-04-17
The sound for my dvd's is out-of-sync with the video in MPlayer-1.0pre7. I'm not sure if I have DMA enabled or not (if that even matters). Anyone have a solution, or a link to a solution?

---

### Post by diebels on 2005-04-17
Don't think dma is enabled by default. Easy to check:
sudo hdparm -d /dev/dvd

---

### Post by vaskark on 2005-04-17
[QUOTE=diebels]Don't think dma is enabled by default. Easy to check:
sudo hdparm -d /dev/dvd[/QUOTE]

/dev/dvd:
 using_dma    =  0 (off)

So how do I enable it? Is DMA responsible for the sound being out of sync? And I also experience choppy video from dvd's on all my installed players (xine, mplayer, vlc, totem-xine). Will this help?

** Update**: Solved it. I edited /etc/hdparm.conf and added the following and rebooted:

/dev/cdrom1 {
    dma = on           
    interrupt_unmask = on
    io32_support = 0
}

(where cdrom1 is my dvd drive)

Sound and video work fine now. Yay! I'm finally happy that I got this working, although IMHO dvd playback is a long way off from the "just works" philosophy in Ubuntu.

*Also, can one of the admins move this thread to Hoary Desktop Support? I effed up. Thanks*

---

