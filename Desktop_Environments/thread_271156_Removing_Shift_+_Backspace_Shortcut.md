---
title: "Removing Shift + Backspace Shortcut"
date: 2006-10-04
forum: Desktop Environments
---

### Post by gorded on 2006-10-04
I've been having trouble trying to remove the shortcut Shift + Backspace in Xubuntu 6.06 i've looked in  Settings Manager > Keyboard > Shortcuts but the Shift + Backspace isn't there. I would aperciate any help on the subject.

Thank you

---

### Post by bwald on 2006-10-04
I'm sorry, I'm unaware of what the shift+backspace keyboard shortcut does.  Perhaps its something specific to your machine?

---

### Post by Vorticon on 2006-10-04
Do you mean control + shift + backspace?

---

### Post by g0rdy on 2006-10-11
It happens to me as well, just doing a Shift+BackSpace kills X and logs me out...

Running Dapper, Beryl Emerald

it is most annoying, also as the op said there is no configuration in the  System>Preferences> Keyboard Shortcuts  to define/un-define this

---

### Post by s_p_a_r_k_y on 2006-10-11
> 
As far as I know, the existing Kwin doesn't support Xgl/Compiz. I use cgwd. It is surprisingly stable for me. The only problem I encountered was the fact that the new compiz-start program doesn't do the xmod change, so things like shift-Backspace will kill the X server. Edit /usr/bin/compiz-start and add this line at the end to fix this problem:


xmodmap -e "keycode 22 = BackSpace Delete"
source: [http://www.linuxjournal.com/node/1000095](http://www.linuxjournal.com/node/1000095)

---

### Post by krimson on 2006-10-16
i am having this same problem, and for the life of me, i cant seem to fix it.. i put it in my sessions > startup programs as "xmodmap... = Backspace" and "xmod... = Backspace Delete"  and most all of the other ones... 
this does not seem to work for me for XGL/Beryl

---

