---
title: "Nautilus cannot modify &quot;Open With&quot;"
date: 2006-02-18
forum: Desktop Environments
---

### Post by speedsix on 2006-02-18
I want .jpgs to open with gThumbviewer by default. If I right click on a jpeg and go to propeties and attempt to change the default program to open with it won't let me unless I log in as root which then only changes the default for the root user.

Any ideas?


I've looked in the nautilus help but it refers to buttons that don't exist, maybe from a previous version.


Thanks

Dom

---

### Post by ipp3l1 on 2006-02-18
Click on the file with right mous -> Properties -> Open with and there you can choose and also add new programs to the list :)

---

### Post by speedsix on 2006-02-18
That's the problem, the program I want is in the list but it won't let me click the radio button and set it as default unless I log in as root :???:

---

### Post by ipp3l1 on 2006-02-18
That's strange, it works like a charm to me...
Have you tried to change it in a directory where you have rights to write?

---

### Post by speedsix on 2006-02-18
Yep, I cannot add programs to the list or change the default program.

Strange.

---

### Post by ipp3l1 on 2006-02-18
There must be a way to do this via shell (Terminal) aswell, but I realy don't know how to do it... Have you tried to for example reinstall nautilus or something?

---

### Post by speedsix on 2006-02-18
It's ok I've sused it, ~/.local was owned by root for some reason, changed it all to be owned by me and it works :confused: 


Thanks

---

### Post by Cybolic on 2006-03-30
I'm still having this problem, running Dapper.

I've made sure that all my files in home are read/write-able by me, but I still can't change the default program for any filetype... I think it might have something to do with Thunar being installed ... :/

---

