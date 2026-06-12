---
title: "panel popup menu disabled"
date: 2009-06-10
forum: Desktop Environments
---

### Post by DrHow on 2009-06-10
I no longer get a full popup menu when I right click on a panel.  It just has the "Help" and "About Panels" options.  Gone are "Add to Panel", "Properties", "Delete This Panel", and "New Panel".  This is inconvenient.  Please someone give me a pointer for how to fix this.  

It happened after I was trying different functions which can be bound to key events in the system Configuration Editor.  It is the sort of thing you might want to be able to do to prevent modification of the panels; but, on going back into the Configuration Editor, I don't see an option that would freeze my panels this way.  However, if there is one, please clue me in.

It looks to me more like a bug caused corruption of the file which describes this menu.  In that case, what I need is the path to that file, so I can fix it (with the proper file from a system that works correctly).  So could someone point me to the file?

I am but a beginner with Linux.  I have already encountered the general problem here more than once.  Namely, given some properties of the system, how does one find the file that controls them?  Poking around in system files that clutter the top level of my home directory, I have found some of them; but it is just a matter of luck.  There must be some system to this stuff.  I would like to see a roadmap if one exists.  I would be very pleased if someone could point me to one.

---

### Post by mcduck on 2009-06-11
> **DrHow said:**
> I no longer get a full popup menu when I right click on a panel.  It just has the "Help" and "About Panels" options.  Gone are "Add to Panel", "Properties", "Delete This Panel", and "New Panel".  This is inconvenient.  Please someone give me a pointer for how to fix this.  

It happened after I was trying different functions which can be bound to key events in the system Configuration Editor.  It is the sort of thing you might want to be able to do to prevent modification of the panels; but, on going back into the Configuration Editor, I don't see an option that would freeze my panels this way.  However, if there is one, please clue me in.

It looks to me more like a bug caused corruption of the file which describes this menu.  In that case, what I need is the path to that file, so I can fix it (with the proper file from a system that works correctly).  So could someone point me to the file?

I am but a beginner with Linux.  I have already encountered the general problem here more than once.  Namely, given some properties of the system, how does one find the file that controls them?  Poking around in system files that clutter the top level of my home directory, I have found some of them; but it is just a matter of luck.  There must be some system to this stuff.  I would like to see a roadmap if one exists.  I would be very pleased if someone could point me to one.

Perhaps you enabled the "locked_panel" option while working with the gconf-editor? That's the only option I know that disables all panel configuration options..

You'll find the gconf key in apps/panel/global/locked_down.

---

### Post by drs305 on 2009-06-11
I agree with mcduck. To fix it, open gconf editor and untick the 'locked' option:
```

gconf-editor /apps/panel/global/locked_down

```

Added:
Although I'd encourage running the above to become familiar with gconf-editor, you can run this command to unlock the panel:
```

gconftool-2 --type bool --set /apps/panel/global/locked_down false

```

---

### Post by DrHow on 2009-06-12
> **mcduck said:**
> Perhaps you enabled the "locked_panel" option while working with the gconf-editor? That's the only option I know that disables all panel configuration options..

You'll find the gconf key in apps/panel/global/locked_down.

That was it!  Thanks.  

I lost interest in that group of configuration settings because the setting for "menu-key" there (default <Alt>F1) has no effect.  (I did successfully change it to <Super>F1 in metacity.)  But I apparently forgot about my experiment with "locked_down" in panel->global.

There is a general problem of apparently duplicated settings - especially between compiz and metacity.  How is one supposed to be able to tell which one is effective?  Even when compiz is running, I find that most of the effective settings are still under metacity.

---

