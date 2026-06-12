---
title: "Black screen"
date: 2009-05-26
forum: General Help
---

### Post by dpreed77 on 2009-05-26
Hi I installed Ubuntu 8.10 on a Thinkpad T400. After updating 8.10, I immediately upgraded to 9.04 (after I hit the upgrade button a box popped up saying that I needed to restart, which I did not do b/c I was already upgrading). After logging into Ubuntu 9.04, which installed on the machine, all I get is a black screen. I waited a while, tried restarting a few times, but the black screen does not go away. 
So, I started all over again. This time I waas able to restart after the update. Ubuntu 9.04 installed and works great. 
The problem is that the broken Ubuntu 9.04 is still on my laptop. When I start up a screen showing multiple operating systems shows up. How can I delete the OS that does not work? Please help with step by step instructions, as you can tell I am fairly new to this!

---

### Post by JB from Wawa on 2009-05-29
hey, put "Ubuntu Black Screen Recover - Kernel Upgrade" in youtube search and you should get this

[http://www.youtube.com/watch?v=f8y29gqX9SU](http://www.youtube.com/watch?v=f8y29gqX9SU)

may be helpful. Or you can ask the guy who made this vid cos he looks like an expert to me.

---

### Post by JCoster on 2009-05-29
If you enter a console and run:
```
sudo gedit /boot/grub/menu.lst
```

..then it's as simple as deleting the Ubuntu's that don't work, keeping the ones which do and clicking save.

Then restart your computer and they'll no longer show up in GRUB!

---

