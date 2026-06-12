---
title: "Lost my Username and Password... need help find out username"
date: 2006-08-04
forum: Desktop Environments
---

### Post by cobbweb on 2006-08-04
Hi, 
 
 I installed Ubuntu on my fathers office computer about 3 months ago, however they didn't turn it off for the three months. I told them to reboot to see if had left their Windows OS installed on the system. They rebooted and found that the Windows OS wasn't there. When we tried to go back into the Linux OS it is asking for our Username and Password. I am sure I can figure out the password if i knew what user name I used. Is there any way to find out what user name I can use????? This is very important for their business, 

 Thanks a bunch, 
 
Cobbweb

---

### Post by 23meg on 2006-08-04
Boot with a live CD, mount your Ubuntu partition and navigate to your /home folder where your user will have self titled folder.

---

### Post by cobbweb on 2006-08-04
Very good. I will tell them to try this. I im and Idaho and they are in Utah so it makes it hard for me to fix their computer manually. (most is vnc/ssh stuff) If they didn't have a live cd is there anyway I could use the "finger" command or somthing.... without being logged in? Thanks a lot for your help 32meg, 

 
Cobbweb

---

### Post by aysiu on 2006-08-04
Better yet, boot to *recovery mode*. Type ```
cd /home
ls
``` You'll see the username there.

Then, instead of guessing the password, you can just reset it: ```
passwd *username*
``` Then reboot ```
reboot
```

---

### Post by cobbweb on 2006-08-04
> **aysiu said:**
> Better yet, boot to *recovery mode*. Type ```
cd /home
ls
``` You'll see the username there.

Then, instead of guessing the password, you can just reset it: ```
passwd *username*
``` Then reboot ```
reboot
```


You are truely amazing. Worked great for my computer at home, however, how can I boot into recovery mode when grub doesn't really "stop" and do the whole "let you select stuff" thing? Thanks again, 
 
Cobbweb

---

### Post by 23meg on 2006-08-04
If the menu is displayed at all, quickly press an arrow key when booting.

---

