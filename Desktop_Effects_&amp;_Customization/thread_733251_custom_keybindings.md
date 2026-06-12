---
title: "custom keybindings"
date: 2008-03-23
forum: Desktop Effects &amp; Customization
---

### Post by wiscados on 2008-03-23
How do I set keybindings to open custom applications, not just the ones in "System->Preferences->Keyboard Shortcuts", like pidgin, gnometris, amarok, etc.?

---

### Post by Locutus_of_Borg on 2008-03-23
apt-get install xbindkeys

then edit the conf file to your liking

---

### Post by wiscados on 2008-03-23
Thank you!!
But I couldn't actually get it working, I'll have to play with it some more.

---

### Post by Locutus_of_Borg on 2008-03-23
When I first installed it, I had an issue as well.  Depending on how you set it up, like if you configure the GUI mode or not, there will be one of two configuration files you need to edit. ~/xbindkeysrc is the non GUI mode file, I believe, and I don't remember what the other is.  If you ran ```
xbindkeys --defaults > $HOME/.xbindkeysrc
``` after install then use the one I just mentioned.  Might be best to edit them both though anyway.

Then just use ```
xbindkeys --key
``` to get the information on the keys you press to put into the configuration file.

For example, to open a terminal I have Ctrl+Alt+Z which looks like:

```
"gnome-terminal"
 m:0xc + c:52
    Control+Alt + z
```

in my .xbindkeysrc file.

Also you have to restart xbindkeys for the changes to take effect.

Hope that helps.

---

### Post by Locutus_of_Borg on 2008-03-23
Oh, 

.xbindkeysrc.scm

is the file you need to edit if you used the gui style. It uses the same syntax as the other.

---

