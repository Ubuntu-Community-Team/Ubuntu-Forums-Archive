---
title: "GDM not starting"
date: 2006-01-14
forum: Desktop Environments
---

### Post by s_g_robertson on 2006-01-14
Please bear with me if I have not got my teminology correct.  

I have been mucking about a bit after I installed Ubuntu and tried installing kubuntu-desktop as well.  All was going well until I decided to remove kde using synaptic, this seemed to work perfectly  Now my situation is the when I boot up I get a command prompt login, if I login and then do sudo gdm then I get the normal login screen and everything works fine.  How do I fix whatever I have broken so I get take straight to the nice pretty Ubuntu login.  

Thanks for your help in advance.

Stephen.

---

### Post by s_g_robertson on 2006-01-14
It seems I can answer my own question.  I tried something that I thought I had tried before, which was editing my default-display-manager file.  What I had done wrong was to have the path as /usr/bin/gdm rather than the correct /usr/sbin/gdm.

I guess I know need to figure out the difference between sbin and bin!!!

Cheers
Stephen

---

