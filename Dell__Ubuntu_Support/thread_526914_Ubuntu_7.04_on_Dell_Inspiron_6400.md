---
title: "Ubuntu 7.04 on Dell Inspiron 6400"
date: 2007-08-16
forum: Dell  Ubuntu Support
---

### Post by aavi on 2007-08-16
Hi 
I have installed Ubuntu 7.04 on my dell Laptop.I have two problems
1, The hardware information in System--> Preferences on clicking just pops up and closes without showing any info ,has any body encountered a error like this before?
2. The desk top effects on cliking shows a error composite extension not avialble and closes

help me in these please

---

### Post by limoral on 2007-08-16
Yes? I had never barged up against this.

Maybe something wrong happened.

---

### Post by aavi on 2007-08-16
No way.it was a clean install ,Can you tell me more on the desktop effects ,how did you enable it (if at all)

---

### Post by strabes on 2007-08-16
What kind of video card do you have? If you don't know, paste the output of this command:```
lspci | grep VGA
```

---

### Post by aavi on 2007-08-16
Its ATI Technologies Inc Radeon Mobility X1400

---

### Post by msangil on 2007-08-27
@ aavi

I have the same problem as you regarding the X1400.

In order to be able to install feisty and run the X-server properly I had to disable the composite extention after install (don't know if you had to do the same). Otherwise, the X-server crashed when starting up and I was returned to the command line.

The clue for this issue -I believe- is in

> **dulbirakan said:**
> Well brother you and I are both victims of ATI drivers. ATI frieglx does not support composite. 

Try this if you really want to but I tried it and the result was glitchy.

[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon")

I use X1600 btw.

[http://ubuntuforums.org/showthread.php?t=533940&highlight=ATI+X1400+composite](http://ubuntuforums.org/showthread.php?t=533940&highlight=ATI+X1400+composite)

If ATI frieglx trully does not support composite I believe there is nothing else we can do.

Does someone know how could I test if at least the xorg driver provides me with OpenGL capability?

---

### Post by Dark Star on 2007-08-27
Dell 6400 comes in 2 varients 1 with Inbuilt GPU and other with ATI :) I have with ibuilt GPU andeverything works like charm so I think its the case with your card .. Since ATI has crap Linux support :|

---

