---
title: "compiz/mate show main menu"
date: 2012-05-29
forum: Desktop Environments
---

### Post by benedictbrown on 2012-05-29
I just upgraded my system to 12.04 and switched from gnome 2.x to mate.  Everything went smoothly except that I can know longer figure out how to pop up my gnome menu (or any other custom menu) at the mouse cursor with either a keystroke or mouse button.

Under 11.04 I could get the main menu using the main_menu_key configuration setting in compiz.  But this no longer works.  I tried adding a main_menu_key to the core plugin in compiz (where all the other settings seem to have moved), but it has no effect.  It's possible the problem is that compiz only integrates properly with gnome, not with mate.

Does anyone have any suggestions about how to work around this, or how to fix the problem in mate and/or compiz?  I don't need the mate main menu--I'd be at least as happen with a custom menu à la openbox.

Thanks in advance,
Benedict

---

### Post by Frogs Hair on 2012-05-29
12.04 runs Gnome 3. I found a suggestion on the Mint forum to use the following command ```
compiz --replace
``` It was also suggested to make sure window decoration is enabled in Compiz. Mate is a Gnome 2 fork but I don't know how similar it is to Gnome 2.

---

### Post by benedictbrown on 2012-05-29
Thanks.  I'm already running compiz on top of mate.  The problem is just figuring out how to pop up a menu at the mouse cursor in that scenario.  Under gnome 2.x and the version of compiz in natty it worked.  Under mate and compiz 0.9.7.8 in precise it doesn't.

> **Frogs Hair said:**
> 12.04 runs Gnome 3. I found a suggestion on the Mint forum to use the following command ```
compiz --replace
``` It was also suggested to make window decoration is enabled in Compiz. Mate is a Gnome 2 fork but I don't know how similar it is to Gnome 2.

---

### Post by Frogs Hair on 2012-05-29
In what plugin is the main_menu_key configuration setting located ? I can't find it even with the extra plugins installed on the current version of Compiz.

---

### Post by benedictbrown on 2012-05-29
I can't find it in any of the settings either, so I tried adding it to core in gconf-editor (I have it set to use the gconf settings backend).  It used to be in the main compiz settings before the others migrated to the core plugin (based on its location in gconf-editor).

There is a "show main menu" option in the gnome settings, and that might well be the one.  But it doesn't seem to work with mate.  That's one reason I thought a specific mate compatibility plugin might be necessary.  It should be pretty easy to adapt the gnome compatibility plugin, but since I've never looked at the code, I'm not really sure.

> **Frogs Hair said:**
> In what plugin is the main_menu_key configuration setting located ? I can't find it even with the extra plugins installed on the current version of Compiz.

---

### Post by Frogs Hair on 2012-05-29
It's likely the setting was a gnome 2 feature and has been removed because the default Unity is now Gnome 3 based and also a Compiz plugin. The dconf editor has now replaced gconf editor in Gnome 3. 

I don't know if you can add a Gnome 2 feature to the compiz profile  latest version of compiz or not.

---

### Post by benedictbrown on 2012-05-29
I know about the shift to dconf, although I haven't fully internalized it yet.  But compiz is definitely using the gconf backends on my system and storing its settings there.  I'll try snooping in the compiz source when I get a chance and see if it's possible to just write a mate plugin for it that will add back the functionality I need.  It should be nearly identical to the Gnome compatibility plugin (or at least the gnome 2.0 compatibility plugin).

> **Frogs Hair said:**
> It's likely the setting was a gnome 2 feature and has been removed because the default Unity is now Gnome 3 based and also a Compiz plugin. The dconf editor has now replaced gconf editor in Gnome 3. 

I don't know if you can add a Gnome 2 feature to the compiz profile  latest version of compiz or not.

---

### Post by Narzeja on 2012-05-30
> **benedictbrown said:**
> I know about the shift to dconf, although I haven't fully internalized it yet.  But compiz is definitely using the gconf backends on my system and storing its settings there.  I'll try snooping in the compiz source when I get a chance and see if it's possible to just write a mate plugin for it that will add back the functionality I need.  It should be nearly identical to the Gnome compatibility plugin (or at least the gnome 2.0 compatibility plugin).

Through some Googling I found the following, which looks like a solution:
[http://forums.mate-desktop.org/viewtopic.php?f=2&t=42](http://forums.mate-desktop.org/viewtopic.php?f=2&t=42)

Although he's using a Fedora distribution it looks like it could be ported to Debian/Ubuntu. Unfortunately my time is not available to mess around with the compiz source and porting the compatibility plugin for Mate, so I switched to Debian Stable (still on Gnome 2.3) to get that original Compiz feeling. :p

---

