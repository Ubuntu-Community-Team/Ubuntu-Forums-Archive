---
title: "Error: cannot open display: 0: When opening any GTK application from the Terminal"
date: 2011-05-13
forum: Desktop Environments
---

### Post by mlupton on 2011-05-13
Hello, for awhile I have had this issue with the command line and every time I try to complete any command that requires GTK graphics, It always returns the error "Error: cannot open display: 0:" The "EXPORT display" command that I normally use to fix this issue is not working. The only issue that I can think might be the cause for this could be my upgrade to natty (which was in fact a clean installation), or when I edited plymouth so that the startup and shutdown animations would match my laptop's native resolution (by the way I would also appreciate it if I could do the same with the startup animation, only the shutdown really works). If anybody know how I could resolve this issue I would greatly appreciate it. Oh and for specifics on my machine, I am using an ASUS N82 with an NVIDIA GEFORCE GT335M graphics card, running Ubuntu 11.04 Natty Narwhal. Thanks in advance for any help you may or may not provide.

---

### Post by mlupton on 2011-05-16
Please, Anyone? D:

---

### Post by wildmanne39 on 2011-05-16
> **mlupton said:**
> Hello, for awhile I have had this issue with the command line and every time I try to complete any command that requires GTK graphics, It always returns the error "Error: cannot open display: 0:" The "EXPORT display" command that I normally use to fix this issue is not working. The only issue that I can think might be the cause for this could be my upgrade to natty (which was in fact a clean installation), or when I edited plymouth so that the startup and shutdown animations would match my laptop's native resolution (by the way I would also appreciate it if I could do the same with the startup animation, only the shutdown really works). If anybody know how I could resolve this issue I would greatly appreciate it. Oh and for specifics on my machine, I am using an ASUS N82 with an NVIDIA GEFORCE GT335M graphics card, running Ubuntu 11.04 Natty Narwhal. Thanks in advance for any help you may or may not provide.

Hi, I can tell you for my nvidia card I have to run the 173 driver or I have serious issues, but I am not sure your card uses the same one. I can not use the current one, also there is a bug report with fixes for nvidia cards, what I mentioned above is the fix for mine and it might be for yours. I hope this helps.):P

---

### Post by mlupton on 2011-06-06
I actually tried running the 173 Driver a little while ago, but the issue with that was that I couldn't even login to my computer after doing that. When I reverted back to the "current driver" my computer began to work again (I had to do all of this in low-graphics safe mode). I'm not sure if anyone's had any luck with this, but it is certainly irritating me.

---

