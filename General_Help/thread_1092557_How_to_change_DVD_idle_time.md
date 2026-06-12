---
title: "How to change DVD idle time?"
date: 2009-03-10
forum: General Help
---

### Post by nickbuntu on 2009-03-10
Hi there,

I'm happily using Ubuntu on my Dell XPS M1330 notebook, and I've got DVD playback working in Totem and everything. The only annoying thing is that the DVD drive will spin down after only about 5 seconds of inactivity, which is enough for it to happen before I choose what to click on the menu of the DVD I'm watching, causing a pause while it slowly spins up. 

Is there a command to change the spindown time to something more reasonable, like 30 seconds? I tried hdparm with no luck, I guess it only works for hard drives:

```
$ sudo hdparm -S 6 /dev/cdrom

/dev/cdrom:
 setting standby to 6 (30 seconds)
 HDIO_DRIVE_CMD(setidle1) failed: Input/output error
```

---

### Post by dcstar on 2009-03-10
> **nickbuntu said:**
> Hi there,

I'm happily using Ubuntu on my Dell XPS M1330 notebook, and I've got DVD playback working in Totem and everything. The only annoying thing is that the DVD drive will spin down after only about 5 seconds of inactivity, .........

All questions about pre-release software should be referred to the appropriate development forum (as it says in the post at the top of this forum).

---

