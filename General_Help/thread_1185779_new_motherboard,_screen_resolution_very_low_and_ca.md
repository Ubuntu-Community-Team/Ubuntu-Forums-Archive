---
title: "new motherboard, screen resolution very low and can't change it"
date: 2009-06-12
forum: General Help
---

### Post by ozguitarplayer on 2009-06-12
Hi,
I have just had the motherboard replaced in my pc and now the the sceern resolution is very low at 640 x 480.
If I go to >System >Preferences >Screen Resolution the there is only one option and that is 640 x 480

How can this be changed? 
I do not use a graphics card.

---

### Post by utnubuuser on 2009-06-12
In Applications>>Accessories>>Terminal, type:

> sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by ozguitarplayer on 2009-06-12
thanks utnubuuser, 
I'm at work now so won't be able to try that for about 8 hours, I'll let you know the result

---

### Post by ozguitarplayer on 2009-06-13
many thanks, worked perfectly...so that I can learn a little more...what was that command that I wrote in terminal, (I do understand the 'reconfigure' part)

---

### Post by swisstone198 on 2009-06-13
You can run 
$ man dpkg-reconfigure
to show a description and how to use a command.

---

### Post by akakingess on 2009-06-13
> **swisstone198 said:**
> You can run 
$ man dpkg-reconfigure
to show a description and how to use a command.
Thanks Swisstone198, that is actually something that I have been wondering and now I will be able to learn a lot more. I can just see myself typing $ man [insert every command I read on this forum here].

akakingess

---

