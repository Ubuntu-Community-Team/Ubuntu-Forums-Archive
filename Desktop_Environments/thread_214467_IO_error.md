---
title: "I/O error"
date: 2006-07-12
forum: Desktop Environments
---

### Post by monergist on 2006-07-12
For the past week or so, when I boot up I get the following error:
```
I/O error on device hdc, logical block 1
I/O error on device hdc, logical block 2
I/O error on device hdc, logical block 3
...
I/O error on device hdc, logical block 7
I/O error on device hdc, logical block 0
```

Not really sure what's going on, but everything works fine when I boot into ubuntu. If anyone knows what the problem is please help. If you know what this is pointing to hardware wise let me know and maybe we can figure it out together :) 

Thanks in advance.

---

### Post by FurryNemesis on 2006-07-12
I don't want to cause any panic...

But my HD did that one weekend recently after 4 years of faithful service and   then it crashed, locked up and died. 

Even the Ultimate Boot CD couldn't save it. 

Back up everything now.

Perform a low-level format of the HD.

Re-install.

If it doesn't work, your hd is b0rked.

---

### Post by FurryNemesis on 2006-07-12
I forgot to mention that you could try this:

Boot into Grub, (esc at boot) and type fsck to check your discs.

That might just sort out some errors.

---

### Post by monergist on 2006-07-13
Eh, I was afraid it was something like that. I've got everything backed up, so I'm not TOO worried about it, and it won't hinder things I have to do for work, as my ibook will take care of stuff. Just frustrating. Haven't tried to reinstall yet because I haven't had time, may try it later. Thanks for your help

---

### Post by monergist on 2006-07-13
hmm I think I figured it out. Its not the hard drive, but the cd-rom.  I think I still have my bios set to boot from CD and I had a music cd in there. It wasn't able to boot (obviously) and so it spit out an I/O error.

wow. Nothing like overthinking something to make you feel dumb.


](*,)

---

