---
title: "Screen resolution"
date: 2006-06-26
forum: Desktop Environments
---

### Post by lnxquestions on 2006-06-26
Hi
I have just installed ubuntu on my hard drive and every thing seems to be ok but the screen resolution . 
The defult is 1280 * 1024 and i want to change it to 1024 * 768 , and every time i do that gnome restarted and after i insert my login info i found the resolution is still the same .
What is the problem her and how can i fix it ?
Regards

---

### Post by ahaslam on 2006-06-26
[QUOTE=lnxquestions]Hi
I have just installed ubuntu on my hard drive and every thing seems to be ok but the screen resolution . 
The defult is 1280 * 1024 and i want to change it to 1024 * 768 , and every time i do that gnome restarted and after i insert my login info i found the resolution is still the same .
What is the problem her and how can i fix it ?
Regards[/QUOTE]
If you want your max, default resoloution to be only 1024x768, edit your xorg.conf (sudo nano /etc/X11/xorg.conf) - make a backup first if unsure. Go to the'screen' section and remove the resoloutions that are above your requirements. Upon reboot the highest resoloution listed will be used.

Tony.

---

### Post by lnxquestions on 2006-06-26
Thanks Tony i will try it now .

---

### Post by lnxquestions on 2006-06-26
Ok .. I did it but i couldnt save the file ... Will you help me ?

---

### Post by ahaslam on 2006-06-26
[QUOTE=lnxquestions]Ok .. I did it but i couldnt save the file ... Will you help me ?[/QUOTE]
I apolagise, I've not given you the easiest method.
Once edited using nano, you'll need to press 'Ctrl' & 'X' to exit. Press 'Y' to save, Press 'enter/return' to use the existing file name. That should sort you out.

Tony.

---

### Post by lnxquestions on 2006-06-26
Ok thanks alot Tony everything worked great .

But i would like to know does everybody have like this problem ? Or it is just me ?

---

### Post by ahaslam on 2006-06-26
[QUOTE=lnxquestions]Ok thanks alot Tony everything worked great .

But i would like to know does everybody have like this problem ? Or it is just me ?[/QUOTE]

Glad to help.

On Breezy you would select the resoloutions that *you* wanted during installation, so it was never a problem. I can't remember being asked such questions with Dapper, it  just automatically selects *all* supported resoloutions that your graphics can provide. Seeing as a lot of people use the maximum resoloution supported, it's rarely an issue.

I hope you enjoy using Ubuntu.

Tony.

---

### Post by lnxquestions on 2006-06-26
Thanks again Tony .

---

