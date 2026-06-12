---
title: "Remove icons from top bar (gnome classic)"
date: 2011-10-19
forum: Desktop Environments
---

### Post by Termina on 2011-10-19
Ubuntu 11.10

So, I have several icons on the top bar (dock?) such as Firefox, Pidgin and a folder I accidentally dragged there.

If I right click, I only get the options Launch and Properties. No remove! 

This is just a terrible experience. Can you guess why Windows doesn't radically change their GUI every release? Almost as if people hate the GUI they're used to being changed around...

---

### Post by pastalavista on 2011-10-19
I haven't upgraded to 11.10 yet because I still see too many bug complaints in the forums, but I have been watching for fixes. 
Check out [this site]("http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html") for some help.

---

### Post by merlinus on 2011-10-19
Alt+right-click.

---

### Post by oneferna on 2011-11-23
I had to do a google search to figure out how to remove icons from the gnome bar in gnome classic. Wow.

I have been using gnome since about 2002 and this is the most pathetic thing I've ever seen.  

Thank you for the answer to this question and reading my venting.

---

### Post by jimmydean886-2 on 2011-11-23
That usually is the shortcut that works at first for me, but you need <super>+<alt>+Button 2 to open it at times. I read about it and the article mentioned a setting, but I haven't found it.

---

### Post by jerrrys on 2011-11-23
Gnome2 was ten years mature and gnome3 is young and hopefully will mature fast.  I too miss features in classic, but they will come

---

### Post by mikebridge on 2012-02-09
Yeah, I've been doing nothing but Googling for 30 minutes trying to configure this horrible Gnome 3 interface so that it's somewhat usable again.  If I have to do that, it's very, very poorly done.

---

### Post by jerrrys on 2012-02-09
Maybe you need to improve your search method.

[http://www.googlubuntu.com/](http://www.googlubuntu.com/)

---

### Post by prusswan on 2012-02-10
alt+lmb+right click, also remember to send Mark your best regards

---

### Post by lovevn on 2013-01-23
I have the same problem with my gnome panel on Ubuntu 12.04
I drag some icon into gnome panel. Now I want to remove them, but when I push and keep Alt+right click or Alt+windows+right click on a icon, it doesn't display menu for choose. What should I do? 
:(

---

### Post by lovevn on 2013-02-12
Well, finally I found the soluttion. I log in Ubuntu with Gnome classic no effects, then, amazingly, I hold Alt and right click, it show menu that includes Remove icon. 
Other way: use terminal:
```
 gconftool –recursive-unset /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-pane
```
to reset gnome-panel. I hope this will be useful for you! :D

---

### Post by markba on 2013-05-13
> **prusswan said:**
> alt+lmb+right click, also remember to send Mark your best regards
This works. There is not need to reset the panel. 
What a bizar key-combo, who designs this stuff? :D

---

