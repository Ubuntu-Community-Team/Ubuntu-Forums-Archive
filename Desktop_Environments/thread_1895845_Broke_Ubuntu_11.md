---
title: "Broke Ubuntu 11"
date: 2011-12-15
forum: Desktop Environments
---

### Post by jgray152 on 2011-12-15
So im new to Linux / Ubuntu and don't know my way around it very well and I seem to find ways of messing it up without trying to hard.

I really don't know what I did since I was browsing the internet, playing with the multi-work space thing and was downloading a partitioning program.

Then all went crazy and Firefox was crashing, programs wouldn't load so I rebooted only to find that Ubuntu would stop loading half way through.
 
I would get the Ubuntu loading screen then it would turn to what looked like a terminal and tell me about a couple things that it was trying to do. I didn't write anything down and thought I could access the partition in widnows 7 to get the logs but it doesn't appear to be so.

I also tried whatever "recovery" option there was listed during boot...lots of...failures, errors and can't dos. lol.

So obviously im a complete novice to Ubuntu / Linux so anyone want to help me out?

---

### Post by jgray152 on 2011-12-15
Anyway I can access error logs? If not I guess ill just have to write down some things I see on the screen.

---

### Post by jimmydean886-2 on 2011-12-15
Which partition editor were you installing?

---

### Post by BC59 on 2011-12-15
Sorry to say but in these cases the only viable solution is to reinstall the system. 

Boot from the disk you installed Ubuntu and choose try instead of install. Then find your personal files and make a backup.
If some files need special privilages to be copied, open a terminal pressing CTRL+ALT+T and run

```
gksudo nautilus
```

From this nautilus you can copy all the files you need without restrictions.

Then do a fresh install of Ubuntu.

---

### Post by critin on 2011-12-15
> **jgray152 said:**
> Anyway I can access error logs? If not I guess ill just have to write down some things I see on the screen.

Not from Windows.  Ubuntu is a separate system.
> 
 and thought I could access the partition in widnows 7

This sounds like you may be using Wubi, yes?  Is ubuntu installed **inside** of Windows so that you can see it's installed from the 'Remove Programs' in Windows control center?

---

### Post by jgray152 on 2011-12-16
Thanks for the replies.

Luckily I have only been playing around getting used to Ubuntu so I havn't created any personal files and theres nothing I need to back up.

I'll just reinstall it I guess. 

I forget the name of the partition program....it was available through the software manager. Once I get it back and running I'll let you know.

I ran Ubuntu and Windows 7 side by side on different partitions. Didn't install Ubuntu inside Windows. 

I love how fast and secure Ubuntu is so im still going to keep trying to figure it out.

Any way I can add more launcher menus? I searched but I found directions for maybe an older ubuntu OS that didn't make much sense to me.

---

### Post by jgray152 on 2011-12-17
The partition software was GParted Partition Editor

---

