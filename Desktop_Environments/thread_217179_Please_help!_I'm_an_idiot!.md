---
title: "Please help! I'm an idiot!"
date: 2006-07-16
forum: Desktop Environments
---

### Post by lwr on 2006-07-16
Right ok. I was trying to get some 3d graphics working, but installed ati drivers instead of the correct nvidia ones. Now i have only the terminal. No login, no anything. I've been trying to use Aptitude but i don't really know what i need to install. Please help!

Thanks

---

### Post by r4ik on 2006-07-16
Did you try Ctrl Alt F1 to log in ?

---

### Post by lwr on 2006-07-16
That doesn't seem to do anything. I forgot to mention i get an effor maessage saying 'failed to start X server', so i can't start gdm.

---

### Post by r4ik on 2006-07-16
Try,

sudo dpkg-reconfigure xserver-xorg

Good luck !

---

### Post by matthew on 2006-07-16
Try this

at the command prompt enter
```
sudo dpkg-reconfigure xserver-xorg
``` 
Follow the menu prompts and just choose the defaults except when it asks for your specific video driver. Instead of "ati" choose "vesa"

When it's done, reboot and let us know what happens

EDIT: beat me by 5 seconds... :)

---

### Post by phibxr on 2006-07-16
Also, when trying to start vith "ati", check the logs afterwards and paste them here. Someone might be able to give some pointers from them.

---

### Post by matthew on 2006-07-16
> **phibxr said:**
> Also, when trying to start vith "ati", check the logs afterwards and paste them here. Someone might be able to give some pointers from them.That wouldn't be helpful...read this again from the OP. :)[QUOTE=lwr]...installed ati drivers instead of the correct nvidia ones...[/QUOTE]

---

### Post by stanz on 2006-07-16
No Fear ~ The Terminal.... ;)
I've done this a dozen times too! 
This, i used with 5.10, and cruized thru the whole thing, with many defaults- left as is....then changed to my liken`- once fixed and workin`.
> sudo dpkg-reconfigure -phigh xserver-xorg Or...
[nano or gedit] >  nano /etc/X11/xorg.conf from there ~ your in the drivers seat ! :rolleyes:

---

### Post by lwr on 2006-07-16
Cheers guys! That's brilliant. It's all working now, even better than before (I enable my favourite 1152x864 resolution while I was there). I'd have been stuffed without you. Thank you!

---

### Post by matthew on 2006-07-16
Yay!! Congratulations.

---

### Post by stanz on 2006-07-16
=D>  This is what it is **all abou**t...rock on!  \\:D/

---

