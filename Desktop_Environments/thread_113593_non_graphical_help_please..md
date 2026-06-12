---
title: "non graphical help please."
date: 2006-01-06
forum: Desktop Environments
---

### Post by r4ik on 2006-01-06
I got my grapic card working until i changed nv into nvidea.
I am in rescue mode on that machine now and in desperate need for a command  
line to change nvidia back to nv.
Help would be very welcome !
Thanks in advance.

---

### Post by dcstar on 2006-01-06
[QUOTE=r4ik]I got my grapic card working until i changed nv into nvidea.
I am in rescue mode on that machine now and in desperate need for a command  
line to change nvidia back to nv.
Help would be very welcome !
Thanks in advance.[/QUOTE]
sudo dpkg-reconfigure xserver-xorg

will allow you to go through the whole X setup process again.

---

### Post by r4ik on 2006-01-06
Will that include setting back nvidia to nv ?

---

### Post by dcstar on 2006-01-06
[QUOTE=r4ik]Will that include setting back nvidia to nv ?[/QUOTE]
You will see a video card selection.

---

### Post by r4ik on 2006-01-06
Thank you very much i am on it.
Will reply when fixed.

---

### Post by r4ik on 2006-01-06
That worked VERY well it will go in my little how-to book.
Thanks again !
There was something about could not initialise HAL.
Any ideas about that or should i just run it agian ?

---

