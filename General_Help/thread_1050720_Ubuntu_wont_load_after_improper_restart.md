---
title: "Ubuntu wont load after improper restart"
date: 2009-01-25
forum: General Help
---

### Post by tigshadorakie on 2009-01-25
I used WUBI to install Ubuntu from within Windows XP. I have been using Ubuntu fine ever since. Just a short while ago I improperly shut down the computer. Now whenever I choose Ubuntu from the OS menu all I get is a GRUBFORDOS and a GRUB command prompt. Why is it doing this and how do I get Ubuntu to load again from this prompt. I restarted the computer from within Ubuntu not Windows. This is not the same as when it complains that windows was not shut down properly. Thank You. 

P.S I am a total beginner to all things Linux oriented.

---

### Post by HuaiDan on 2009-01-26
If you don't have a prompt, hit alt-f2 on the keyboard.

Then 
sudo /etc/init.d/gdm start


That will start your GUI.

gdm stop will manually stop your GUI.

---

### Post by tigshadorakie on 2009-01-26
> **HuaiDan said:**
> If you don't have a prompt, hit alt-f2 on the keyboard.

Then 
sudo /etc/init.d/gdm start


That will start your GUI.

gdm stop will manually stop your GUI.


This doesn't work. It says command not recognized. All I get is a paragraph of information on the top screen then the  command prompt GRUB:  

There is a list of commands there but I wouldn't know how to use them to load the kernel and boot.

---

### Post by mejbr2003 on 2009-01-26
same problem I'm having

---

