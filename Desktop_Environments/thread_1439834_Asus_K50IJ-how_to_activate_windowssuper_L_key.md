---
title: "Asus K50IJ-how to activate windows/super L key?"
date: 2010-03-26
forum: Desktop Environments
---

### Post by vickoxy on 2010-03-26
Hi,
trying to set up ubuntu 9.10 on asus k50ij and one more issue that i have is missing super l/windows key. I am using it on dell mini 10v to hide all windows and to show desktop, but on asus it seems to be dead. I tried to set it up as usually in keyboard shortcuts-but have no response from that key.

Any idea?

---

### Post by vickoxy on 2010-03-26
Bump

---

### Post by vickoxy on 2010-03-27
No one?
I noticed that compiz is also using some keyboard shortcuts, but have no idea how to set Super key to show desktop.

---

### Post by vickoxy on 2010-03-28
Bump

---

### Post by vickoxy on 2010-03-31
Bump!

---

### Post by vickoxy on 2010-04-01
Some sort of bug? I tried to set it up in gconf-edito and through terminal ([http://ubuntuforums.org/showthread.php?t=891023](http://ubuntuforums.org/showthread.php?t=891023)), but still nothing-no way i can make only win key to show desktop...

---

### Post by vickoxy on 2010-04-02
Bump

---

### Post by alfh on 2010-05-08
Bump!

Using the super key for the same purpose. Just upgraded my old IBM Netvista from 8.04 to 10.04. Opening the keyboard shortcuts dialog and super key is not responding. I can't even delete shortcuts (the delete button is grey).

---

### Post by libssd on 2010-06-11
For extended discussion, see: [http://ubuntu-utah.ubuntuforums.org/showthread.php?p=9239960](http://ubuntu-utah.ubuntuforums.org/showthread.php?p=9239960)

**Short version**: At the command line:
xmodmap -e "add mod4 = Super_L"

This is a hack, and will need to be re-applied after upgrade to a new release. No explanation as to why the Canonical gods decided to change the default behavior of this key.

---

### Post by vickoxy on 2010-07-03
OK, so maybe this will work on Asus too-i have now ThinkPad R500. I finally found solution to make only win key to show desktop (as i was able to do in Hardy):

[http://forums.linuxmint.com/viewtopic.php?f=55&t=44908](http://forums.linuxmint.com/viewtopic.php?f=55&t=44908)

Thanks to **libssd**

> From command line: gconf-editor
Or 
Edit menus, and activate Configuration Editor in the System Tools menu

Default:
apps > metacity > global_keybindings > show_desktop <Control><Alt>d

Change to:
apps > metacity > global_keybindings > show_desktop Super_L

After making this change, Keyboard Shortcuts will show:
```

Hide all normal windows and set focus to the desktop           Super L
```
Top

---

