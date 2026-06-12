---
title: "Taskbar grouping"
date: 2007-12-23
forum: Desktop Effects &amp; Customization
---

### Post by SyCo123 on 2007-12-23
Hi,
I've just re-installed Ubuntu with 7.10. 

My issue is the open windows on the task bar. In pre 7.10 I could choose to have all open windows show on every workspace taskbar or only the ones relevant to the workspace you were in. I'd like the latter, where only the workspaces current windows show on the taskbar. I have compiz effects working, cube and everything.

Am I missing the control for this or is this option gone now compiz is in control?

---

### Post by SyCo123 on 2007-12-30
Anyone?

---

### Post by Forlong on 2007-12-30
Right-clik on the dotted space between the Show Desktop button and the first open window in the lower panel and choose Properties.

There should be the option you are looking for.

---

### Post by SyCo123 on 2007-12-30
Thanks for the reply.

Under Preferences>Windows List Content
'show windows from current workspace' is selected. Yet I still get all the windows from every workspace.

---

### Post by Forlong on 2007-12-30
So when you stop Compiz everything's alright?
Has it always been this way on Compiz? Do you have ccsm (compizconfig-settings-manager - "Advanced Desktop Effects Settings") installed and did you change something there?

---

### Post by SyCo123 on 2007-12-30
Not sure how i would stop compiz. It's the dektop manager in 7.10 isnt it?

And yes I have the settings manager installed so it's very possible I've chaned someting, played with a lot of stuff when I got it working! 

Do you know where the setting for that is in the manager?

---

### Post by Forlong on 2007-12-30
> **SyCo123 said:**
> Not sure how i would stop compiz. It's the dektop manager in 7.10 isnt it?
It's Gutsy's default window manager. But GNOME's window manager (Metacity) is still installed.
You can either go to *System &#8594; Preferences &#8594; Appearance &#8594;  Visual Effects* and choose None or run this via [Alt]+[F2]
```
metacity --replace
```
> **SyCo123 said:**
> And yes I have the settings manager installed so it's very possible I've chaned someting, played with a lot of stuff when I got it working! 

Do you know where the setting for that is in the manager?
No, I'm not aware of any setting for this but you might have somehow messed with gconf.

Try switching to the "Flat-file Configuration Backend" at *Preferences &#8594; Backend* (in the configuration manager - you might want to save your profile first) and click on "Reset to defaults". Then restart Compiz and see if it helped.

---

