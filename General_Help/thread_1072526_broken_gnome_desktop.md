---
title: "broken gnome desktop"
date: 2009-02-17
forum: General Help
---

### Post by christian1991 on 2009-02-17
the application menu has stopped working. places and system still work fine, but the applications are not responding to clicks.
alt F1 does not work either.
any ideas?

---

### Post by wstout on 2009-02-17
well just to be sure have you tried logging out and back in? or restarting the X server (ctl-alt-backspace) ?

---

### Post by christian1991 on 2009-02-17
Yes, I have. This has been going on for a while now and the computer has been on and off several times.

---

### Post by wstout on 2009-02-17
ok this may be worth a try but be warned this will reset your desktop back to the defaults it come with. Press alt + F2 and type gnome-terminal into the dialog box since you can't access your menus. Then in the terminal enter the following commands: ```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel 
pkill gnome-panel 
```

That might do it, but if you have a lot of customization going you may want to wait for a better idea.

---

### Post by christian1991 on 2009-02-17
i did what you said, it did reset the desktop but the applications menu is still not responding.
any more ideas?
thanks anyway

---

### Post by wstout on 2009-02-17
maybe so... check this link out [http://ubuntuforums.org/showthread.php?t=875430](http://ubuntuforums.org/showthread.php?t=875430)   hopefully that will help

---

