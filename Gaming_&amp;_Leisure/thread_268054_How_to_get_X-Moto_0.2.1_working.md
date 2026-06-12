---
title: "How to get X-Moto 0.2.1 working?"
date: 2006-09-29
forum: Gaming &amp; Leisure
---

### Post by User-007 on 2006-09-29
Hi,

I did not found an adequate help anywhere. How to install x-moto 0.2.1 to Dapper? Is there somewhere a step-to-step help for doing that? I have not been able to get the game working.

Thanks 
MOTOCROSSER

---

### Post by Perfect Storm on 2006-09-29
[http://gaming.gwos.org/index.php?option=com_content&task=view&id=105&Itemid=63](http://gaming.gwos.org/index.php?option=com_content&task=view&id=105&Itemid=63)

---

### Post by User-007 on 2006-09-30
Thanks for a link.

Unfortunately all in the compilation did not work correctly. Has someone been able to get XMOTO working in Dapper?

Thanks
User JB

---

### Post by Perfect Storm on 2006-09-30
please post what went wrong or didn't work. (You can paste the terminal output.)

---

### Post by User-007 on 2006-09-30
Hi.

Attached file contains of the history when running "./configure" and "make". Unfortunately, the text file being attached was too big so I renamed it to be "svg" file so in order to read it, rename the file again to plain text file.

Thanks. I hope you you can help me.

User JB

---

### Post by Perfect Storm on 2006-09-30
It looks like you havn't installed a proper 3D acceleration card driver for your graphic-card.

> checking for OpenGL library... no

The game requires that.
Most of the errors from make seems to point at this.

---

### Post by Mickeysofine1972 on 2006-09-30
Just so you know...

Xmoto is in the repos for Edgy Eft!

Mike

---

### Post by User-007 on 2006-10-01
Mikey, could you give further information about that? What to add in the repo list?

I will test the 3D issue later today.

Thanks
Oba

---

### Post by User-007 on 2006-10-01
For a continuing discussion about 3D issue, check this:

[http://www.ubuntuforums.org/showthread.php?t=269010](http://www.ubuntuforums.org/showthread.php?t=269010)

User JB

---

### Post by User-007 on 2006-10-01
Ok, it seems that this is related to OpenGL. So please could someone give me help how to get OpenGL completely working in Dapper?

User JB

---

