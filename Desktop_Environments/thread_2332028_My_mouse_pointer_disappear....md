---
title: "My mouse pointer disappear..."
date: 2016-07-27
forum: Desktop Environments
---

### Post by noname34 on 2016-07-27
Good morning/evening. I have the version Lubuntu 16.04.1. 

When i lock the screen of the computer, or when i want change user, i can always use the mouse, but she is invisible. I research a long time on  Internet, in french and in english, but i didn't find a solution for me. 


Before, that's worked, but i think maybe "sudo apt clean", "sudo apt autoclean" or "sudo apt autoremove" are responsibles of this situation. 


I precise it is useless to change mouse, that's don't work. And if i have installed gedit, my folder xorg.conf is empty...I don't understand. 

I used others lines commands, but that was useless too...

Can you help me, please ? 

Thank you very much ! :)

---

### Post by Nada__Blue_Book on 2016-07-28
you need to make it confirm where is the problem is? Check your mouse with other system if there was problem on mouse then it need to change. Other was if the problem was on driver you need to install it..

---

### Post by noname34 on 2016-07-28
Thanks for your answer. My mouse works with other systems. How can i find the best driver for my material please? And how can i install it ? I know how install programs but not the drivers on lubuntu. 
I suppose it's the same thing, but sometimes, when i try to install programs, i need research name the exact packages's name.

---

### Post by PaulW2U on 2016-07-28
> **noname34 said:**
> When i lock the screen of the computer, or when i want change user, i can always use the mouse, but she is invisible. 
> **noname34 said:**
> My mouse works with other systems.
Hello noname 34. unfortunately you did not give us any details of the PC that you are using. Does it have Intel graphics?

[Bug #1568604]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1568604") has affected many users that are using Lubuntu and Xubuntu. From what you have written I'm not sure if this bug is affecting you or if you are describing something else. The bug is still showing as "Confirmed" but not fixed in the Xenial release. Is this what you are experiencing or is you issue different?

Please give us some technical information about your PC.

---

### Post by noname34 on 2016-07-28
Hello, my computer is a (or "an" ? ) HP Compaq dc7800 Convertible Minitour. 

For read my technical information about my PC, you can watch here : [http://www.cjoint.com/c/FGCobAAvkCA](http://www.cjoint.com/c/FGCobAAvkCA)

But, this link will disappear in twenty-one days. I think my problem is the same. When i lock my screen, and when i start it after, cursor becomes invisible...

For Intel Graphics, i think answer is "yes", because i have a processor Intel Pentium Dual CPU. 

Have i answered correctly to your questions ? :)

---

### Post by PaulW2U on 2016-07-28
> **noname34 said:**
> For Intel Graphics, i think answer is "yes", because i have a processor Intel Pentium Dual CPU. 

Have i answered correctly to your questions ? :)
Thanks noname34, then i think that you're also experiencing a bug to which over **400** users have marked the bug report to say that the bug is also affecting them.  :(

There are several workarounds and fixes suggested in the report but the easiest and safest for now is to switch to a virtual terminal and back again with **Ctrl-Alt-F1** and then **Ctrl-Alt-F7** each time you unlock your PC.

Hopefully the bug will be fixed soon and that the above helps in the meantime.

---

### Post by noname34 on 2016-07-28
In fact, Ctrl+Alt+F1 and Ctrl+Alt+F7 works, but i would like the bug can be really fix, because it's annoying to make that all the time. 

Thanks for the report, i will see it ! :)

---

