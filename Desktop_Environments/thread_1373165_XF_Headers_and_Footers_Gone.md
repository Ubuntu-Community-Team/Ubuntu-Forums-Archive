---
title: "XF Headers and Footers Gone"
date: 2010-01-05
forum: Desktop Environments
---

### Post by Timbot2000 on 2010-01-05
Booted up my device today, and much to my dismay, both my top and bottom fields in GNOME were gone! I can still access applications by right-clicking on the desktop, but I need to get into my Network Manager today. I seem to remember something about a hide function for these, if you are going to suggest I unhide these, great, just tell me specifically how to unhide them. 

Thanks in advance

---

### Post by MichealH on 2010-01-05
Press CTRL +ALT +F1 to got text login Login to the text mode and run this command (Dont worry its a safe command)

```
[FONT=Arial]**r****[B]m** -rf .gnome .gnome2 .gconf .gconfd .metacity[/B][/FONT]
```

Then press CTRL + ALT + F7 and your Gnome should be restored to Factory Settings

---

### Post by Timbot2000 on 2010-01-05
Sorry, ran the command (took awhile until I realized I needed a space before the periods), but still no bars.

---

### Post by MichealH on 2010-01-05
Maybe you had a faulty install or have you run any commands recently with rm in them? (Except mine)

---

### Post by Timbot2000 on 2010-01-05
Not likely, everything was golden until today. 
In an aside, in the Xfce setting manager, I can call up all the functions, except "Panels" which stays away

---

### Post by Timbot2000 on 2010-01-05
SOLVED!

Couldn't be easier

Go to usr/bin/xfce4-panel 
right-click "execute"

and voila!:guitar:

---

