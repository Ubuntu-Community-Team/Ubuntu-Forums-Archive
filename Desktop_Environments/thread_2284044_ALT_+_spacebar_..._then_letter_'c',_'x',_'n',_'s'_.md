---
title: "ALT + spacebar ... then letter 'c', 'x', 'n', 's' ... etc ... discontinued ?!?!?!"
date: 2015-06-26
forum: Desktop Environments
---

### Post by Muzafsh on 2015-06-26
Alt+Space then pressing N to Minimize 
Alt+Space then pressing X to Maximize/Unmaximize 
etc ... 



I was just trying the current Ubuntu 15.04 UbuntuGnome and Lubuntu flavors, live CD and now installed versions as well. I can't for the life of me manage without the above way of things(window managment) i am so used to it. I can't think why were the 'N', 'X', 'C' 'S' alphabet key actions that were standard when one pressed Alt+Spacebar and invoked the above discontinued in the latest ubuntu versions.

Is it true its being discontinued or its some kind of a bug ?

thanks for looking.

---

### Post by PaulW2U on 2015-06-26
Moved to ***Desktop Environments*** as you're asking about official Ubuntu flavours.

---

### Post by kurt18947 on 2015-06-26
At least some key combinations seem to work on Ubuntu-Gnome 14.04.2.  Alt-Space X/N/C seem to function. What is Alt-Space S function?  I don't see an action there. I was unaware of this key combo function until this post.

---

### Post by vasa1 on 2015-06-26
> **kurt18947 said:**
> At least some key combinations seem to work on Ubuntu-Gnome 14.04.2.  Alt-Space X/N/C seem to function. What is Alt-Space S function?  I don't see an action there. I was unaware of this key combo function until this post.
This is what I have with the Openbox window manager (version 3.5.2) on Lubuntu 14.04.2. **Alt-spacebar, S** sends the current window to (another) desktop.

I haven't tried 15.04 and so can't answer OP's question.

---

### Post by kurt18947 on 2015-06-27
Apologies, I missed that Muzafsh was asking about 15.04.  I just loaded Xubuntu 15.04 64 bit. The key combinations seem to work as expected on a Thinkpad X series. I don't know about other *buntu 'flavors'.

---

### Post by mc4man on 2015-06-27
Don't use 15.04 but in my 14.04 alt+space is default disabled, in 15.10 it's default enabled. So try setting, this is for Ubuntu or I guess Ubuntu Gnome - 
```
gsettings set org.gnome.desktop.wm.keybindings activate-window-menu "['<Alt>Space']"
```
So here the various window menu letters do work in 14.04 & 15.10, at least those shown (n,x,M,R)  - edit > c also works
Other bindings related to windows can be found in system settings > keyboard > shortcuts or dconf-editor > org.gnome.desktop.wm.keybindings

---

### Post by Muzafsh on 2016-04-27
> **kurt18947 said:**
> Apologies, I missed that Muzafsh was asking about 15.04.  I just loaded Xubuntu 15.04 64 bit. The key combinations seem to work as expected on a Thinkpad X series. I don't know about other *buntu 'flavors'.

thanks @kurt18947 ...

Oh ... i don't understand ...In Xubuntu 15.04 the key's in question are working ?

I had tried it on UbuntuGnome flavor ... it didn't work back then(15.05)

AND ITS NOT WORKING NOW !!!
I recently upgraded my nephew's HP Elitebook 2560p with UbuntuGnome 16.04 LTS afresh ... and i am having the same problem as described in OP !!!

can anybody confirm if this issue exists in Ubuntu Vanilla(Unity) or not ?

looks like UbuntuGnome has this problem specifically !!!

Is it a bug or by design ?
any devs around ? ... who can confirm the same ?

in the meanwhile would really appreciate a workaround !!!

thanks

---

