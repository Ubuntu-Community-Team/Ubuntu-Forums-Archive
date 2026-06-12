---
title: "MonoDevelop Menu Issue"
date: 2007-03-11
forum: Desktop Environments
---

### Post by ShareBuntu on 2007-03-11
Hi there,

Due to some unforeseen event the menu entry for MonoDevelop went crooked. I removed the entire package using:

sudo aptitude purge mono mono-gmcs mono-gac mono-utils monodevelop

Then, I reinstalled using:

sudo aptitude install mono mono-gmcs mono-gac mono-utils monodevelop

Yet, after all that, there is no sign of a menu entry (KDE) for MonoDevelop. Any ideas?

---

### Post by ComplexNumber on 2007-03-11
can i assume that you're using kde?
i wouldn't have thought that it would appear in the kde menu. its more a gnome application. i don't remember it appearing when i were using kde on PCLinuxOS. it appears in the gnome menu, though.

---

### Post by ShareBuntu on 2007-03-12
> **ComplexNumber said:**
> can i assume that you're using kde?
i wouldn't have thought that it would appear in the kde menu. its more a gnome application. i don't remember it appearing when i were using kde on PCLinuxOS. it appears in the gnome menu, though.

That's correct, I'm using KDE. It was definitely there before I borked the menu. You'd think completely removing it and re-installing it would fix the entry.

---

### Post by ComplexNumber on 2007-03-12
you haven't mentioned in what way you have borked the menu.

---

### Post by ShareBuntu on 2007-03-12
I managed to fix the menu issue by editing .config/menus/applications-kmenuedit.menu. Alas, not before I deleted /etc/mono in and attempt to rid the system of any mono traces. Even after purging and reinstalling, MonoDevelop simply would not start. It's looking for a file called machine.config that was located somewhere in /etc/mono.

My last resort is to do a clean OS install but I'd like to avoid that. Any ideas on machine.config?

---

### Post by ShareBuntu on 2007-03-12
Here's the error:

```
Unhandled Exception: System.Configuration.ConfigurationException: Cannot find /etc/mono/2.0/machine.config ()
  at System.Configuration.DefaultConfig.Init () [0x00000]
  at System.Configuration.DefaultConfig.GetConfig (System.String sectionName) [0x00000]
  at System.Configuration.ConfigurationSettings.GetConfig (System.String sectionName) [0x00000]
  at MonoDevelop.Core.AddIns.AddInService.GetAddInDirectories (System.Boolean& ignoreDefaultPath) [0x00000]
  at MonoDevelop.Core.AddIns.AddInService.Initialize () [0x00000]

```

---

