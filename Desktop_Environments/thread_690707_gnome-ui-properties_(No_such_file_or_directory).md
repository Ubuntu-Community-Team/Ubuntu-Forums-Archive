---
title: "gnome-ui-properties (No such file or directory)"
date: 2008-02-07
forum: Desktop Environments
---

### Post by CodeNosher on 2008-02-07
When I try to run System | Preferences | Menus & Toolbars I get this error:

[FONT="Courier New"]*Failed to execute child process "gnome-ui-properties" (No such file or directory)*[/FONT]

When I try to run Menus & Toolbars from the Gnome Control Center the screen flashes very quick.  I thought I'd run gnome-control-center from cli and try it.  I get this when I do:
[FONT="Courier New"]
**** (gnome-control-center:4068): WARNING **: error launching file:///home/jason/.local/share/applications/gnome-ui-properties.desktop [Failed to execute child process "gnome-ui-properties" (No such file or directory)]**[/FONT]

Just starting gnome-control-center gives me this:

[FONT="Courier New"][B]** (gnome-control-center:4161): WARNING **: 
error raised: [libslab_get_gconf_value: error getting /desktop/gnome/applications/main-menu/lock-down/user_modifiable_apps]

** (gnome-control-center:4161): WARNING **: 
error raised: [load_xbel_store: couldn't load bookmark file [NULL]
]

** (gnome-control-center:4161): WARNING **: key not found [/apps/control-center/cc_actions_list][/B]
[/FONT]

The only thing that I can think of that I have done recently is added a program called Ubuntu Tweak.  This may have been a problem before that since I don't hardly ever run control center or the Menu & Toolbars stuff.

I searched for gnome-ui-properties as something I could install but I can't find anything.

Any thoughts on what is happening and how I could fix it?

---

### Post by talsemgeest on 2008-02-08
Try reinstalling the packages through synaptic.

Hope this helps :)

---

### Post by CodeNosher on 2008-02-08
Which packages?  

I searched for gnome-ui-properties and nothing comes up.

I re-installed the Menus and gnome-menus and libgnome-menu2.

This didn't fix it.

---

### Post by talsemgeest on 2008-02-08
just do a search for gnome, and look for whatever you have installed. Reinstall whatever has something to do with the menus.

---

### Post by tcommbee on 2008-02-08
did you check in console if this command exists at all? i have a full gnome install and it's not there. you probably have an old link because this functionality should be in one of the tabs in "Appearance" (gnome-appearance-properties), which is installed in the package gnome-control-center.
I get the same warnings when starting control center, but as long as they don't become errors, i don't care :D

---

### Post by CodeNosher on 2008-02-09
Well that explains it.  Thanks.  The functionality has been moved, but the menu option remains.

thanks.

---

### Post by talsemgeest on 2008-02-10
If its fixed, mark this thread as solved

---

