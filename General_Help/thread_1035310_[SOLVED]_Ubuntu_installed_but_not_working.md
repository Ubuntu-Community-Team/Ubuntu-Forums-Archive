---
title: "[SOLVED] Ubuntu installed but not working"
date: 2009-01-09
forum: General Help
---

### Post by Zaki ur Rehman on 2009-01-09
Hi Guys
I installed ubuntu. After instalation it reboots the pc. Then start ubuntu, ask user name and pasword, after this a simple screen appears with nothing on it, no effect of mouse click, keyboard etc. Could anyone guide me what happening?? what to do now?

---

### Post by namdung on 2009-01-09
Ur hardware specs? Any video card?
Which Ubuntu version?

---

### Post by Zaki ur Rehman on 2009-01-10
Installing it again. I downloaded it and I think its 8.XXX that is available for download online. The system is Dell optiplex. If it not get solved, I told you soon. Thanx for reply buddy.

---

### Post by abn91c on 2009-01-10
if you got to the login and only the mouse moved its probably Compiz, if your dell has an Intel 845 series video you will get that. After reinstall if the same thing happens try this press ctrl+alt+f1 to get to a prompt then type```
sudo apt-get remove compiz
sudo apt-get remove compiz-core
``` then reboot

---

### Post by Zaki ur Rehman on 2009-01-10
I want to format the disk while installing ubuntu. Same as we do in winxp installation. How could we do that? is it possible or not??

---

### Post by Peter09 on 2009-01-10
During the installation tell the program to 'use the whole drive' This will result in a complete format of the drive, all old contents will be lost.

---

### Post by abn91c on 2009-01-10
> **Zaki ur Rehman said:**
> I want to format the disk while installing ubuntu. Same as we do in winxp installation. How could we do that? is it possible or not??
somewhat the same, at the installation partitioning screen select the option **guided:use entire disk**. Ubuntu will format and make all the partition it needs automatically. depending on you system hardware it can take from 30 to 60 min to finish

---

### Post by Zaki ur Rehman on 2009-01-10
no work after reinstall. No keyboard or mouse response, no prompt by ctrl+alt+f1.
I want to re format my partition and install it again in the light of your guidance.
and also tell me how/what to chose the partitioning option when it ask me?? As I dont know anything about it.

---

### Post by abn91c on 2009-01-10
> **Zaki ur Rehman said:**
> no work after reinstall. No keyboard or mouse response, no prompt by ctrl+alt+f1.
I want to re format my partition and install it again in the light of your guidance.
and also tell me how/what to chose the partitioning option when it ask me?? As I dont know anything about it.

follow this guide it has step by step screenshots [http://news.softpedia.com/news/Installing-Ubuntu-8-10-97417.shtml]("http://news.softpedia.com/news/Installing-Ubuntu-8-10-97417.shtml")

---

### Post by Zaki ur Rehman on 2009-01-10
I did the same. And now installing again with using entire disk option. Let see what happened.:???:
could I connect a ubuntu pc with a windows pc via lan? and how can I put proxy etc???

---

### Post by Zaki ur Rehman on 2009-01-10
Hi guys
I got installed and run it successfully. But I chose safe graphic mode when starting the installation. Now its not allow me to enable the graphic enhancements. I want to change the resolution but how????

---

