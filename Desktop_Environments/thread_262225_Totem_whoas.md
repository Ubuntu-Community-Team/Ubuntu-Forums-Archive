---
title: "Totem whoas"
date: 2006-09-21
forum: Desktop Environments
---

### Post by mbgb14 on 2006-09-21
My dads laptop seems weird when trying to view a DVD in Totem. First of all, rewinding and fast forwarding is virtually impossible - it jumps all over the place, and the time shows up wrong, secondly, it usually crashes after moving; and you have to close Totem. 

Secondly, once closed, you cannot restart the DVD. If you go into Totem, goto File, and play the DVD it says I don't have the right codecs - yet I do on first insert (Autoplay).. 

Whats wrong? Its really starting to tick me and my dad off - I'd hate to see him go back to Winblows just for that reason.

PS: Yes, libdvdread3 is installed.

---

### Post by skymt on 2006-09-21
Try installing VLC or mplayer, to see if either of those works better.

---

### Post by mbgb14 on 2006-09-24
Neh. Neither works. VLC just won't do anything when I goto Open Disk. 
And mplayer SORTA works. But I can't get to the menus at all. 

Frig, see, this is the kind of thing that deters n00bs from Linux (not that I'm a n00b).

---

### Post by qamelian on 2006-09-24
> **mbgb14 said:**
> Neh. Neither works. VLC just won't do anything when I goto Open Disk. 
And mplayer SORTA works. But I can't get to the menus at all. 

Frig, see, this is the kind of thing that deters n00bs from Linux (not that I'm a n00b).


The problem with MPlayer is that it doesn't support menus yet. With VLC you need to tell it where to find the disc or alternately, you can check the  "Probe Discs" box on the Disc tab and it will try to locate the device for you.

---

### Post by mbgb14 on 2006-09-24
Probe disks won't check. 
And where would my drive most likely be? 
It says

dvd://

---

### Post by qamelian on 2006-09-24
> **mbgb14 said:**
> Probe disks won't check. 
And where would my drive most likely be? 
It says

dvd://

It depends on the type of drive, whether is master or slave, etc. If you check in /etc/fstab, it should tell you which device it is. For example, on my laptop, it is /dev/hdc.

---

### Post by mbgb14 on 2006-09-24
So I'd put 

dvd:///dev/hdc

?

---

### Post by qamelian on 2006-09-24
> **mbgb14 said:**
> So I'd put 

dvd:///dev/hdc

?
Just ```
/dev/hdc
```

---

