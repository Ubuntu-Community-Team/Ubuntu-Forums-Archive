---
title: "desktop disabled"
date: 2009-02-26
forum: Desktop Environments
---

### Post by jimmybarcelona on 2009-02-26
So i boot up ubuntu 8.04, and all of my desktop icons are gone. I try to right click to add new launchers, or drag and drop them from the applications menu, but neither will work. When I right click on the desktop, nothing happens. The pop up menu doesn't even appear. What would cause this?

---

### Post by taurus on 2009-02-26
Can you open/run any app in the Applications menu?

---

### Post by jimmybarcelona on 2009-02-27
everything works on the computer just fine, I could use it as is. I just like the desktop icons because it isn't my personal machine. It's a workstation in the computer lab where I work. Most of the people who use the computer lab have never used linux before, so I put a firefox, openoffice.org, and some other launchers on the desktop for them. The main one is a launcher to the shared folder that I have set up for them on one of the computers through Samba.
   Here's the strange thing though, all of the desktop icons reappeared yesterday. They all disappeared for about 2 days, then appeared exactly as they were. Could it be a setting somewhere that one of my coworkers accidentally may have messed with? If you know, please let me know, just in case it happens again.

---

### Post by taurus on 2009-02-27
You can change the permissions to run only for those icons.  Then, others won't be able to remove them from the desktop.  That's one possibility.

---

### Post by jimmybarcelona on 2009-02-27
will do. that was fairly obvious, but I'm pretty new to the linux scene. I'm still working on changing my mindset over to ubuntu and thinking outside of the windows box. thanks for the help.

---

### Post by little_penguin on 2009-03-01
Another thing you could check is a setting in the Nautilus preferences in Gnome Configuration Editor. See whether "Show desktop" is enabled or not:

In a terminal, or in the Run window by pressing Alt F2, type

```
gconf-editor
```

Then navigate to /apps/nautilus/preferences/show_desktop

and make sure it is ticked.

Hope that helps.

---

