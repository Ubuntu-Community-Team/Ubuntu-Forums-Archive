---
title: "I just can not get grub splash issue"
date: 2005-01-14
forum: General Help
---

### Post by edemark on 2005-01-14
Hi all
I have a small problem. I am a newbee so I would like to have a nice splash screen to see while my laptop start up my ubuntu linux. So i have reviewed some (may not all) pages related to how to make GRUB use a splash screen. So as i have observed i needed to download hoary grub pkg and install it. So i did it. Then i have installed grubconf (warty) to be able to edit menu.lst graphically. Then i downloaded some grub splash screens which i set up with grubconf (unhide menu as well). Everithing looked fine. When i restarted my laptop a nice splash screen came up. I thought that it was going to work all right BUT after letting to time out grub to start ubuntu everythig got back to text mode. NO PROGRESS BAR AND NICE BACKGROUN only the usual processes and ok-s on the right.
So my question is, how to have this picture and progress bar insted of the usual text screen?

thanks for the help

---

### Post by edemark on 2005-01-14
Sorry I have just read that I should not have posted my question here but in sub forums. So pls put this message where it should have been posted

Anyway i am witing for answers
thanks

---

### Post by wallijonn on 2005-01-14
As far as I know there is no way to install a SPlash screen into Warty. Do a search for "splashscreen" where this issue is discussed more fully. It has to do with the kernel. Change the kernel to Hoary and your whole system may get mucked up.

---

### Post by edemark on 2005-01-14
[QUOTE=wallijonn]As far as I know there is no way to install a SPlash screen into Warty. Do a search for "splashscreen" where this issue is discussed more fully. It has to do with the kernel. Change the kernel to Hoary and your whole system may get mucked up.[/QUOTE]
 Thanks for the answer.
However it makes me sad a bit because i was really up to see a nice progress bar with a background picture. Anyway i was thinking about to learn kernel compiling. Though i am not sure to do so with ubuntu or with slackware (because this latter one has beautiful documentation on this issue). But still thanks for the help

edemark
pd i am really up to make splash screen working bec i want to make my colleges be surprised about linux bec here where i work everybogy uses win

---

### Post by Sensebend on 2005-01-15
Recompiling a kernel isn't all that hard, know that you can mess things up if you don't know what you are doing. Once you've done it once or twice it becomes extremely trivial.

---

### Post by macewan on 2005-01-15
usplash is the recommended route from what I've read. you may want to wait.

---

