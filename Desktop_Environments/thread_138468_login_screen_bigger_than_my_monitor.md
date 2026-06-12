---
title: "login screen bigger than my monitor"
date: 2006-03-02
forum: Desktop Environments
---

### Post by ramaswamyps on 2006-03-02
the greeter screen is not fully visible in my 15" LG monitor
but it moves around with the mouse drag and can see the hiding buttons of actions session etc
the desktop setting of 800x600 does not apply to this login res?

---

### Post by MrDan on 2006-03-02
Hey that is kinda like my problem I' not alone!:cool:

---

### Post by noomz on 2006-03-02
May you want to comment out the line with "Viewport" and "Virtual" in /etc/X11/xorg.conf

:-k

---

### Post by ramaswamyps on 2006-03-02
could not find any lines mentioning Viewport or Virtual in /etc/X11/xorg.conf
worth mention is i have basically installed Ubuntu-5.10 and installed kde-3.5 by upgrading with apt-get.
:) :)

---

### Post by MrDan on 2006-03-02
I went in to the /etc/X11/xorg.conf and deleted the resolution that my monitor would not show for mine 1600x1200 from the different modes and then did a hard reboot after saving.  It worked. 

Hope this helps.

---

### Post by ramaswamyps on 2006-03-02
i too did the same as u did .removed the higher resolution of 1260x768 from all modes line.
now i can see the login screen fully.
thanks for ur experimenting.
:) :) :) :)

---

