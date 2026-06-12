---
title: "Audio drivers for dell 1420"
date: 2008-05-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by cooldudeny on 2008-05-20
Hi i just installed ubuntu 8.04 on my dell inspiron 1420 but i think i need to the audio drivers since the audio is not loud enough and is not stereo quality 

does anyone came across issue like this it was working just perfect when i was using ubuntu 7.10 

need some advice if there is anyone who can help me out

---

### Post by notwen on 2008-05-21
Dell's Linux Wiki has a section specifically for your issue.  Check [here]("http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Upgrade") for their fix.

---

### Post by cooldudeny on 2008-05-21
> **notwen said:**
> Dell's Linux Wiki has a section specifically for your issue.  Check [here]("http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Upgrade") for their fix.

that does not work for me because i do have sound it is just that it is not loud enough like before and not stereo quality like before or the way it is supposed to be

---

### Post by LisaM on 2008-08-10
Did you ever get this problem solved?  I have the same problem after installing 8.04.  I have sound, but the volume is very low and hard to hear.  The volume control is already set to max.

Thanks!

---

### Post by cerise on 2008-08-21
I would also like to know if this problem was solved. :confused:

---

### Post by shae on 2008-08-21
Launch a terminal and type
```
alsamixer
```

And see if the master channel is set really low.

---

### Post by anjilslaire on 2008-08-21
^^Correct. I have a 1420, and one of the channels (master or front) was set really low. Raising it fixed the issue.

---

### Post by LisaM on 2008-08-22
> **cerise said:**
> I would also like to know if this problem was solved. :confused:

Yes.  Right click on the audio icon at the top, and left click on Open Volume Control.

Select Edit > Preferences  Check all of the checkboxes.  Now, look and make sure that none of the volume controls are muted.  This solved the problem for me.

---

