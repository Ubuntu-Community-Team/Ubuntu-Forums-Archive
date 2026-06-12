---
title: "Using Windows or Super key for hot-key combos"
date: 2012-04-19
forum: Desktop Environments
---

### Post by M_Mynaardt on 2012-04-19
Hi!

I figured out how to configure, with care, the key bindings in the file **~.config/openbox/lubuntu-rc.xml** to make your own hot key combinations and all that.

***However***, I can't seem to do that with the Windows or Super Key.  Every time I press the *Windoze* key, the LXDE menu pops up from the panel.  Just as if I'd used Alt-F1, one of the default hot-key combinations in Lubuntu.  The problem there is, that if I have a hot-key combination with the windows key, all I get is the LXDE menu and not, say, my browser opening up as I'd like with "Windows-w".

I've noticed several hot-key combos already in the file, like "Windows-r", "Windows-F1", etc.  But none of them work either; all I get is the LXDE menu whenever I try those ones.

Does anyone know why this is?  I'm sure it's a simple thing I don't know how to fix.  I'd just like to disable the windows key from opening the LXDE menu, and use it for hot key combos instead.

Any help would be appreciated!

Thanks!

---

### Post by jyoz on 2012-07-10
Instead of using "Windows-w" try using "W-w" whereas the capital "W" stands for the Windows/Super key. See if this works. 

Also, the Windows Key is also defined as "Super_L" (for the Windows key left of the spacebar) and, if applicable, "Super_R" (to the right of the spacebar).

Currently, I'm using "Super_L" to bring up the LXDE menu, but not with any other combo. So if "W-w" doesn't work maybe "Super_L-w" might. 

Good luck, try looking at the LXDE forums they may have a lot more documentation and info on this.

---

### Post by M_Mynaardt on 2012-07-11
> **jyoz said:**
> Instead of using "Windows-w" try using "W-w" whereas the capital "W" stands for the Windows/Super key. See if this works. 

Also, the Windows Key is also defined as "Super_L" (for the Windows key left of the spacebar) and, if applicable, "Super_R" (to the right of the spacebar).

Currently, I'm using "Super_L" to bring up the LXDE menu, but not with any other combo. So if "W-w" doesn't work maybe "Super_L-w" might. 

Good luck, try looking at the LXDE forums they may have a lot more documentation and info on this.

Hi there!  I should have posted this earlier, but I did find a fix to this.  There were two keybinding statements in the Openbox file that caused this.  Remove them, or comment them out, and this one little problem is solved.  One set the left super/window key to bring up the LXDE menu and the other set the right super/window key (if there is one) to bring up the LXDE menu.

If memory serves, someone who's more in the know that me, pointed this out to me in LXDE forums.


```
<keybind key="Super_L">
  <action name="Execute">
    <command>lxpanelctl menu</command>
  </action>
</keybind>

<keybind key="Super_R">
  <action name="Execute">
    <command>lxpanelctl menu</command>
  </action>
</keybind>
```

These are found in **~/.config/openbox/lubuntu-rc.xml**.  This is the file you have to handle with care, since it sets a lot of your system ***stuff*** …

Both of these prevented the Super Key from being used as part of a hot-key combination.  Therefore, I got rid of those, and … voilà!  It works properly!  I also found there were also a few keybindings in there set for some of the hot-keys I wanted.  For example, I wanted Super-e to open the editor.  But there was already on there for Super-e to open the file manager.  So, I just had to take a bit of time to edit the key bindings and I got the hot key combinations I wanted with the super key.

Groovy, Man!
:guitar: stands for the Windows/Super key. See if this works. 

Also, the Windows Key is also defined as

---

