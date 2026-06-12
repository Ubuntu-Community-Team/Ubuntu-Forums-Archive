---
title: "gnome-terminal preferences.....or not!"
date: 2010-10-02
forum: Desktop Environments
---

### Post by pfnorris on 2010-10-02
I have noticed that since gnome-terminal was recently upgraded to 2.30.2 that irrespective of the settings in preferences it always opens at a width of 80 cols. In fact the option to set this through the preferences dialogue has been removed.

I have set it to 132 cols in gconf-editor it makes no difference. I then made that the default setting in gconf-editor. No joy. I then found the gconf.xml file(s) under .gconf in my user profile and set them manually. Still no luck.

Now I know I can achieve this with a couple of mouse clicks each time I launch the terminal. But that's a pain (or at least a papercut!!).

Does anyone know how to save my sanity by having the terminal open up automatically at 132 cols.:confused:

---

### Post by pfnorris on 2010-10-07
Anyone??

---

### Post by drs305 on 2010-10-07
There was a thread about this last week. At the time I read the post, in Lucid, I still had the option in Profiles to set the width. A short time later, after an update, I also lost the capability. We played with gconf-editor but even by changing the settings there could not restore the option.

On my 64-bit install (I'm currently in Maverick) I still have the option, so perhaps it is a bug and not an intentional decision to remove it.

I believe you still have the option of launching it with the command line or shortcut with the "--geometry" option to open it to the size you desire.

---

### Post by mcduck on 2010-10-07
I just answered the very same question a few days ago, so a simple search of the forums would have given you the answer. 

Anyway, you can go to System/Preferences/Preferred Applications, and on the System-tab set the default terminal to "Custom", command to "gnome-terminal --geometry 132x40" and the execute flag to "-x". 

(If you just type "gnome-terminal" in the command field it will automatically switch back to the default Gnome-terminal option, so type in the geometry part of the command first, and then add the "gnome-terminal" to the beginning)

This will affect any terminal you open, apart from the ones you open directly from the Applications-menu. For that one you need to edit the menu launcher (right-click on the menu and select "Edit Menus") in a similar way.

---

### Post by fergal on 2010-10-08
> **mcduck said:**
> I just answered the very same question a few days ago, so a simple search of the forums would have given you the answer. 

Anyway, you can go to System/Preferences/Preferred Applications, and on the System-tab set the default terminal to "Custom", command to "gnome-terminal --geometry 132x40" and the execute flag to "-x". 

(If you just type "gnome-terminal" in the command field it will automatically switch back to the default Gnome-terminal option, so type in the geometry part of the command first, and then add the "gnome-terminal" to the beginning)

This will affect any terminal you open, apart from the ones you open directly from the Applications-menu. For that one you need to edit the menu launcher (right-click on the menu and select "Edit Menus") in a similar way.

It does not work for terminals opened with ctrl-shift-n. They open at 80x24 (no matter what the size of the "parent" terminal) :(

Also, while trying to edit the Custom setting, as soon as I type the last character of "gnome-terminal" it immediately jumps off Custom and back to GNOME Terminal. I had to paste the full command into the input box. I'll file bugs.

---

### Post by mcduck on 2010-10-08
That's why I said you need to type in the geometry part of the command first... ;)

Anyway, ctrl-shift-n doesn't do anything at all on my computer. Check if you ave configured that shortcut in Compiz settings, you might have to add the geometry options there as well.

---

### Post by fergal on 2010-10-08
> **mcduck said:**
> That's why I said you need to type in the geometry part of the command first... ;)

Indeed you did! Anyway, I filed [https://bugs.launchpad.net/bugs/656804](https://bugs.launchpad.net/bugs/656804) for it.

> **mcduck said:**
> Anyway, ctrl-shift-n doesn't do anything at all on my computer. Check if you ave configured that shortcut in Compiz settings, you might have to add the geometry options there as well.

It only works when I'm in a terminal. On the File menu, the first entry is "Open Terminal" and it has that as a shortcut. I have no idea where that is defined.

---

### Post by pfnorris on 2010-10-15
Thanks all. At least I know it's not just me. By the way I did search first, but I obviously didn't ask the right question !!

---

