---
title: "How to save desktop configuration?"
date: 2007-02-16
forum: Desktop Environments
---

### Post by muguwmp67 on 2007-02-16
I'd like to try redesigning my desktop, but do not want to lose my current configuration (in case I need to go back to it).  Is there an app I can use to backup and restore gnome/beryl configurations?  Or should/can I just make a copy of my home folder and store it somewhere?

---

### Post by Waappu on 2007-02-16
Hi

Beryl from SVN repository has feature in Beryl Setting Manager to export current configuration.

Open Beryl Setting Manager and in General Options tab there is "settings, profiles and desktop integration" where you can export/import settings.

I think other way is backup ~/.beryl folder and then restore it

---

### Post by muguwmp67 on 2007-02-16
Thanks, will this save things like panel configuration too?  If not, is that all in the gconf directory?

---

### Post by Waappu on 2007-02-16
Hi

From Beryl Setting Manager you can only save Beryl settings. If you want save Emerald theme you should open Emerald Theme Manager and use that to save your themes.

Panel configuration seems to be in ~/.gconf but I'm not 100% sure is there all what you need to backup

---

### Post by drs305 on 2007-02-19
> **Waappu said:**
> Hi
Panel configuration seems to be in ~/.gconf but I'm not 100% sure is there all what you need to backup

I would like to save my panels and am content with the other settings. Would someone please confirm the above or tell me how I can save the panel setup I have created (launchers, order, icons, etc). I would also like to copy the panel setup to other computers.

I went to Syst, Prefs, Themes but I don't seem to be able to save the theme unless I change something else (and I don't know if Themes save the panel info anyway).

Thanks.

---

