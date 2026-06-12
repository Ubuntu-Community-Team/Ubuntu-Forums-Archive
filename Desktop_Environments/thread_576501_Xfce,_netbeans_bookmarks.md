---
title: "Xfce, netbeans bookmarks"
date: 2007-10-15
forum: Desktop Environments
---

### Post by dgavenda on 2007-10-15
In Xfce, it seems like ctrl-f2 returns to the last used workspace.  This could be useful but ctrl-f2 is used within netbeans to add/remove bookmarks.  Xfce seems to override netbeans and I can not add/remove bookmarks by pressing crtl-f2.

Is there a way to suppress Xfce into ignoring this keypress?  I would like to use ctrl-f2 as bookmark add/remove within netbeans.

Thx,
Dan

---

### Post by afoglia on 2007-10-15
> **dgavenda said:**
> In Xfce, it seems like ctrl-f2 returns to the last used workspace.  This could be useful but ctrl-f2 is used within netbeans to add/remove bookmarks.  Xfce seems to override netbeans and I can not add/remove bookmarks by pressing crtl-f2.

Is there a way to suppress Xfce into ignoring this keypress?  I would like to use ctrl-f2 as bookmark add/remove within netbeans.

Yes.  But it may not be easy.  Go to Window Manager Settings, and choose the keyboard tab.  You'll want to create a new set of settings.  Then set all the ones you want, and don't set the ones you don't.

It might be quicker to just create it (and perhaps set one keyboard shortcut just so it's not empty), and see where Xfce saves it.  [Looking at this thread]("http://ubuntuforums.org/showthread.php?t=205455"), I think the file will be ~/.themes/vnc/xfwm4/keythemerc .  Copy the defaults from /usr/share/themes/Default/xfwm4/keythemerc, and delete the Ctrl-F2 bookmark, and hopefully it will work.

---

