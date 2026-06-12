---
title: "A couple of questions!"
date: 2006-07-13
forum: Desktop Environments
---

### Post by halvdansk on 2006-07-13
Hi! 

how can i get 1024x768 resolution in console?

how can i get that cool text (openbox) when i open gnome-terminal ?

thx :D 
[IMG]http://offload1.icculus.org/openbox/shots/full/nextgen.png[/IMG]

---

### Post by Lunar_Lamp on 2006-07-13
As for how to get the resolution in console, I'm not quite sure what you mean.

To get cool text when you open the terminal you need to know two things.  Firstly the text is created just by using the characters | \ / and _ along with a few others where needed (for more info google for ascii art).

To get things like that to load when you open a terminal, you need to edit your bashrc file.  To do this:

gedit /home/USERNAME/.bashrc 

or

gedit ~/.bashrc

As an example, the end of my bashrc file contains this:

```
echo "################################################################################
# 'He draweth out the thread of his verbosity finer than the staple of his 	#
# argument.'									#
#										#
#	- Holofernes, Love's Labour Lost					#			
################################################################################"
```

This results in my terminal loading like the screenshot attached.

---

### Post by halvdansk on 2006-07-13
***As for how to get the resolution in console, I'm not quite sure what you mean.***

when u press Ctrl+Alt+F1 it is 800x600 resolution and i want it to be 1024x768  (smaller text :P )

thx for the quick reply!

---

### Post by Lunar_Lamp on 2006-07-13
I think you need to append the option "vga=792" in your grub.conf file, but I cannot remember the exact syntax for this, you'll have to check up how it works.

Wait, just found a link that explains it:
[http://www.linuxplanet.com/linuxplanet/tutorials/6206/3/](http://www.linuxplanet.com/linuxplanet/tutorials/6206/3/)

Edit: the file that you need to edit is /boot/grub/menu.lst

---

