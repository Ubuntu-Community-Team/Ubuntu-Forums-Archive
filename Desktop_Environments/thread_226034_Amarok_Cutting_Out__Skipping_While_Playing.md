---
title: "Amarok Cutting Out / Skipping While Playing"
date: 2006-07-30
forum: Desktop Environments
---

### Post by dkaplowitz on 2006-07-30
Hello all,

I've got a problem with Amarok on Ubuntu 6.0.6 under Gnome (and it seems to be happening in Fluxbox too). Amarok keeps briefly cutting out while playing music. There is no fault with the audio sources I'm using. I have disabled system beep/system sounds. Amarok is up to date and is using Xine. This problem is intermittent and I can't seem to reproduce it, but it happens at least 2-3 times during the course of a 5 minute song. 

It's almost as if a CPU process is interrupting it. When running gkrellm it seems to always happen when there's a CPU spike reported by gkrellm. I can't figure out what it is by running top though. Metacity would be my best guess, but that doesn't work under Fluxbox does it? I've run a later version of Amarok on Gentoo recently and didn't have this problem at all.

Anyone have any ideas what I can do to track this down? 

Thanks for any help.

Dave

---

### Post by Lord Illidan on 2006-07-30
It seems like a problem with dma.

Try running this in a terminal

```
sudo hdparm /dev/hd*
``` and show us your output.

---

### Post by dkaplowitz on 2006-07-30
Ah, that's a good lead, actually. Thanks for the reply. But these are all sata drives. DMA's only for IDE, no? 

Anyway, here goes:
```

$ sudo hdparm /dev/sd*

/dev/sda:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 4500/255/63, sectors = 72303840, start = 0

/dev/sda1:
 IO_support   =256 (???)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 4500/255/63, sectors = 69304347, start = 63

/dev/sda2:
 IO_support   =256 (???)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 4500/255/63, sectors = 2, start = 69304410

/dev/sda5:
 IO_support   =256 (???)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 4500/255/63, sectors = 2988027, start = 69304473

/dev/sdb:
 IO_support   =256 (???)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 9039/255/63, sectors = 145226112, start = 0

/dev/sdb1:
 IO_support   =256 (???)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 9039/255/63, sectors = 497952, start = 63

/dev/sdb2:
 IO_support   =256 (???)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 9039/255/63, sectors = 1992060, start = 498015

/dev/sdb3:
 IO_support   =256 (???)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 9039/255/63, sectors = 142721460, start = 2490075

/dev/sdc:
 IO_support   =256 (???)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 38913/255/63, sectors = 625142448, start = 0

/dev/sdc1:
 IO_support   =256 (???)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 38913/255/63, sectors = 625137282, start = 63

/dev/sdd:
 IO_support   =256 (???)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 38913/255/63, sectors = 625142448, start = 0

/dev/sdd1:
 IO_support   =256 (???)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 38913/255/63, sectors = 625137282, start = 63

/dev/sde:
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 30401/255/63, sectors = 488397168, start = 0

/dev/sde1:
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 30401/255/63, sectors = 488392002, start = 63

```

sdd and sdc are where all my audio files reside.

Cheers,

Dave

---

### Post by dkaplowitz on 2006-08-01
Any more ideas?

---

