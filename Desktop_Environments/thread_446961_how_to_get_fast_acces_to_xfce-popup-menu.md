---
title: "how to get fast acces to xfce-popup-menu"
date: 2007-05-17
forum: Desktop Environments
---

### Post by szymon_g on 2007-05-17
hi.
i've got a problem(s).
i don't know how to configure a xfce4-popup-menu (standard menu panel, with groups of applications - by default uses ctrl + esc shortcut) to open/close when i press 'windows' key. when i used 'standard' way (menu > settings > keyboard > keyboard preferences > shortcuts > add new _setting shortcut for xfce4-popup-menu) it doesn't saw my win key

when i followed this mini-faq 

[http://forum.ubuntu.pl/viewtopic.php?t=12918](http://forum.ubuntu.pl/viewtopic.php?t=12918)

(unfortunatelly in polish, but i'll translate:
console/terminal : xev <pressing_win_key>

KeyPress event, serial 30, synthetic NO, window 0x2600001,
    root 0x5c, subw 0x0, time 79113581, (-379,-332), root:(172,0),
    state 0x0, keycode 115 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 30, synthetic NO, window 0x2600001,
    root 0x5c, subw 0x0, time 79113770, (-379,-332), root:(172,0),
    state 0x40, keycode 115 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

<sss@sss:$ xmodmap -e 'keycode 115=Menu'

and menu > settings >..... as i wrote before)

everything was ok (i.e system saw my win key as a menu key), it worked...
but i don't know how can i save this configuration?
what is a xfce's equivalent of kde's ~/.kde/env/win-key.sh ?
i've tried to write it into my .bashrc file, but it dont work

szymon


/////////// and my second problem 

what should i do to get acces to menu under right-click? i mean, whean i right-click on my desktop, i have options like 'create louncher' etc, but i wanna have the same menu as in xfce4-popup-menu. 
i've installed xfce4 from repository, it's version 4.4.0 my system is feisty fawn

---

### Post by nicepants on 2007-05-18
i can't help with your first question, but the second should be as simple as changing a setting in xfce's Desktop menu from the main settings manager. there should be a setting with a few options you can change - i'm at work, if you can't find it i'll check this thread again and let you know.

---

