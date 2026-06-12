---
title: "tried to reformat external HD with extension 3"
date: 2009-05-07
forum: General Help
---

### Post by cptrohn on 2009-05-07
with gparted... it seems to have reformated the external HD, but the thing is i can no longer transfer files to the external HD... LOL (Yep I screwed something up...:confused:  )

I keep getting an ```
access denied
``` error when I try to move files to it.... it power up and mounts just fine though...


Any ideas on what I did wrong?

---

### Post by wsonar on 2009-05-07
are you only going to be using this external drive on ubuntu and not pluging into a windows box?

---

### Post by cptrohn on 2009-05-07
> **wsonar said:**
> are you only going to be using this external drive on ubuntu and not pluging into a windows box?

No windows box's.... I only have an Ubuntu system and an older box that I installed puppy's Deep Thought on....

So I don't need fat or ntsf file systems on the external HD.

---

### Post by wsonar on 2009-05-07
what if you try to do a  mkdir on it does that work?

---

### Post by cariboo on 2009-05-07
Change the permissions of the mount point eg:

```
sudo chmod -R 777 /media/<mountpoint>
```

This will make the drive world read/writeable

For more info on auto mounting drives, have a look at [thread=283131]this[/thread] howto.

---

### Post by cptrohn on 2009-05-07
OK, the moutnpoint seems like it is the problem..

I will read up on this and try things out...

Thanks for the great link.

---

### Post by cptrohn on 2009-05-07
Hmm... Ok so I used gparted and reformatted the external HD back into vfat and it mounts and is completely useable again, drag and drop folders with no problems...


I used the ```
sudo mkdir /media/usb
``` when it was still in ext3 and could not get it to work no matter what I tried...

I guess I will just have to read up on this some more before I try again... (I have a larger HD that I want to put into an enclosure and use as well, the smaller one is going to be strictly for the puppy linux box)....

I guess I have some serious google work coming tonight... LOL

Thanks much for all the help, I will read more about that link tonight when I have more time.

---

