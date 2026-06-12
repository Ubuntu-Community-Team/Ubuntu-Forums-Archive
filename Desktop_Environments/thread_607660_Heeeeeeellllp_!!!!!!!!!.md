---
title: "Heeeeeeellllp !!!!!!!!!"
date: 2007-11-09
forum: Desktop Environments
---

### Post by Mr-Business on 2007-11-09
Ok ... iam newby in ubuntu and i was disable in users and usergroups mine persmisions so i cant nothing do... how i can return my access level back with root command ? 
Please answer fast !

---

### Post by Mr-Business on 2007-11-09
Someone ? Here is 5000 ppls online and none can help ? :confused:

---

### Post by KhaaL on 2007-11-09
try choosing to boot in fail safe mode (single user). from there you'll be at a textual console, enter "startx" to start the graphical interface. 

once there, you can change your permissions but be aware that you'll be running as root, so be careful not to mess something up!

PS. change the topic to something more relevant to your problem, the odds of you getting help will increase then :)

---

### Post by Mr-Business on 2007-11-09
What is command for changin acess ?

---

### Post by KhaaL on 2007-11-09
At the boot, you'll have a few choices to choose from (the standard is usually Ubuntu 7.10, kernel 2.6.22-14). Instead of choosing that, choose the one that ends with recovery mode, which is:

Ubuntu 7.10, kernel 2.6.22-14 (recovery mode)

---

### Post by LunatikOwl on 2007-11-09
Try:
System->Administration->Users and Groups

---

### Post by Mr-Business on 2007-11-09
> **LunatikOwl said:**
> Try:
System->Administration->Users and Groups
I cant because my acces is unchecked for administatives... 

How i can give back myself access with console ?

---

### Post by mcduck on 2007-11-09
> **Mr-Business said:**
> I cant because my acces is unchecked for administatives... 

How i can give back myself access with console ?

You can't. You have the exactly same permissions in console as you have in desktop. Like already said, you need to boot into recovery mode and fix it that way.

---

### Post by Mr-Business on 2007-11-09
Problem solved simply by modifing /home/etc/group file.
Thanks all !

---

