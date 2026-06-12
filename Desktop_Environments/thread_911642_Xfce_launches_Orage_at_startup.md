---
title: "Xfce launches Orage at startup"
date: 2008-09-05
forum: Desktop Environments
---

### Post by scip on 2008-09-05
I have ubuntu 8.04 running Xfce (and gnome and kde). For some reason, when I log into Xfce, the Orage calendar and preferences windows open at startup. I've unchecked the "Save session for future logins" checkbox during logout, but it still opens.

Is this a bug or is there something else that is controlling the launch of this? Not a big deal, just a bit annoying.

I should add that I checked the Autostarted apps in the Settings Manager and Orage is not included in the list.

---

### Post by Predator106 on 2008-09-05
Well I'm just throwing this out there, but try closing that program and then clicking save the list of running applications, the button, not the checkbox. If it isn't there, just ignore me :) I only use GNOME but am still trying to be helpful :).

---

### Post by kjohansen on 2008-09-05
Orage can also be added as a panel item.  So it is possible that the clock you have on a panel is causing it to be opened.  You can remove it from the panel and then add the basic clock.

---

### Post by randcoop on 2008-09-10
Did you find the answer to this question?  I have the same problem and nothing seems to be able to stop Orage from starting when XFCE starts.  I have removed it from the panel, but still no help.

---

### Post by randcoop on 2008-09-10
The fix is to close all orage that are running, then remove the .cache folder from your home directory.  .cache is where the settings from the previous sessions are saved.  If you do this, the next time you log in, orage will not start.

---

### Post by etnlIcarus on 2008-09-10
Before I uninstalled Orage (one possible solution) I'm pretty sure there was an autostart entry for it.

[img]http://img148.imageshack.us/img148/9531/autoti4.png[/img]

Alternatively, go to the ~/.config/autostart directory and delete anything relating to orage.

---

### Post by scip on 2008-09-17
> **randcoop said:**
> The fix is to close all orage that are running, then remove the .cache folder from your home directory.  .cache is where the settings from the previous sessions are saved.  If you do this, the next time you log in, orage will not start.

Yes, deleting the .cache directory from my home directory worked, thanks!

---

### Post by MusashiAharon on 2008-12-07
I have the same problem, but closing the Orage windows and running ```
rm -rf ~/.cache/
``` didn't work for me.

I then tried removing the Orage clock panel and removing ~/.cache/, but that also didn't work.

---

### Post by morgengenuss on 2008-12-09
go to orage preferences -> display -> calendar start -> hide (radiobutton)

this should work in general and can be especially useful if you use orage in your panel and clicked it and it opened every session after that.

---

