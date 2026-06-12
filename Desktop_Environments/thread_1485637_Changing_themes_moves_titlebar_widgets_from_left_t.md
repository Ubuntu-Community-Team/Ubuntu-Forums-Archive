---
title: "Changing themes moves titlebar widgets from left to wrong"
date: 2010-05-17
forum: Desktop Environments
---

### Post by 2cute4u on 2010-05-17
When I used Karmic, I only had to use gconf-editor to set the titlebar widgets to the left once, and they stayed there when I changed themes, no matter what theme I set.  Since I installed Lucid, every time  I change themes (other than to radiance or ambiance),  my titlebar widgets are moved from the upper left  to the upper right, and I have to use gconf-edit or to switch them back to the way they were.  

Why is this happening and what can I do to stop it?

---

### Post by plucky on 2010-05-17
> **2cute4u said:**
> When I used Karmic, I only had to use gconf-editor to set the titlebar widgets to the left once, and they stayed there when I changed themes, no matter what theme I set.  Since I installed Lucid, every time  I change themes (other than to radiance or ambiance),  my titlebar widgets are moved from the upper left  to the upper right, and I have to use gconf-edit or to switch them back to the way they were.  

Why is this happening and what can I do to stop it?

Read the [sticky](http://ubuntuforums.org/showthread.php?t=1469475) as that has an explanation of why the buttons have moved,and how to move them back.

Good Luck

---

### Post by 2cute4u on 2010-05-17
> **plucky said:**
> Read the [sticky](http://ubuntuforums.org/showthread.php?t=1469475) as that has an explanation of why the buttons have moved,and how to move them back.

Good Luck

The sticky says the **exact opposite** of what i want.  I don't want to move things to the old position, I want to keep things in the new position.  

Ambiance, and Radiance, specify the position in the theme file , all the others don't. when you save the theme it doesn't specify order.  I don't want to have to hand edit every theme, 

For me Radiance is how it should be, Ambience is how it should be. Every other theme moves them to the wrong position.   I want the default to stay, [COLOR="blue"]close, minimize maximize:menu[/COLOR]  by default, and not to change it to [COLOR="red"]menu:minimize, maximize,  close[/COLOR], when no order is specified by the theme.

---

### Post by 2cute4u on 2010-05-17
I think I posted this in the wrong forum. 

**Modorators**: please move this to Desktop environments.


Thank you

---

### Post by pj_kare on 2010-05-18
Being reasonably new to Ubuntu myself, I can't really help, though I did a bit of  searching and found this page below->

[COLOR=Blue][http://www.ubunter.com/apps/blog/entries/show/3111112-easy-gui-window-button-switcher-for-lucid-and-karmic-users](http://www.ubunter.com/apps/blog/entries/show/3111112-easy-gui-window-button-switcher-for-lucid-and-karmic-users)[/COLOR]  

It's not what you wanted but you may be able to use it for now. (If it works).

Otherwise, if you know how to do any programming (I don't) you might  want to go to this web page [COLOR=Blue][http://blogs.gnome.org/metacity/](http://blogs.gnome.org/metacity/)[/COLOR] and look under the heading GNOME bug 613522  towards the bottom of the page.
It suggests using a gkeyfile in the  theme directory. 
Another page that may help with gkeyfile: [http://www.gtkbook.com/tutorial.php?page=keyfile](http://www.gtkbook.com/tutorial.php?page=keyfile)[COLOR=Blue]
[/COLOR] 
Sorry I can't be of more help. :(

---

### Post by 2cute4u on 2010-05-19
thanks that utlility is helpful, but I shouldn't need to use something like that.  I filed a bug on launchpad

---

### Post by drs305 on 2010-05-19
> **2cute4u said:**
> I think I posted this in the wrong forum. 

**Modorators**: please move this to Desktop environments.


Thank you

Moved as requested.

---

