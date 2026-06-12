---
title: "xubuntu 6.10 disappearing desktop icons"
date: 2007-04-18
forum: Desktop Environments
---

### Post by possumator on 2007-04-18
Hi,

I have created various application launchers on my desktop for convenience. Since doing this, it seems some have disappeared. When I browse my trashcan to view my home folder, etc. (the only way I know how to get there...LOL) I can see the icons showing up in the desktop folder. However, they are still missing from the desktop. And when I try dragging an icon out of this folder onto the desktop, it does move to the desktop ok, but then appears as a second instance of that icon in the folder (expected behavior I suppose). 

The question is why are they disapearing? 

TIA...possumator

---

### Post by lysergic on 2007-04-19
Hello mate, i'm quite new to Xubuntu and Xfce myself but i have been noticing the same problem on my box.. Because Xfce is a GTK Desktop Environment my knowledge is that each individual part of the GUI is rendered seperately, as opposed to other DE's.. The program that controls the desktop (the background, the icons, the right click function) is called 'xfdesktop'...
So if your desktop is lost or icons go away, all you need to do is simply invoke the xfdesktop..

From your shell type $~ xfdesktop    to load the program and bring your desktop back. 
Alternatively type   xfdesktop&  from the prompt, the & simply tells the process to load on its own, and not in the shell.. 

Hope this helps

---

### Post by possumator on 2007-04-29
Very good information,

thanks!

I was running Xubuntu 6.10 for several months on an old Compaq Armada M700 with only a PII 366 and 192MB. While a tad slow, it did pretty much everything I needed and even ran the Eclipse IDE (albiet with some help from the swap file).

Since then I have moved to an AMD64 3400+ system and haven't looked back:-)

The old dino-laptop is now a faithful Ubuntu 6.10 LAMP and Subversion WEBDAV server for learning how to develop Ruby on RAILS and PHP5.

---

