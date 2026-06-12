---
title: "No option to get Konqueror (or Dolphin) to navigate with single click!"
date: 2018-07-09
forum: Desktop Environments
---

### Post by jtappin on 2018-07-09
I've just upgraded from Artful to Bionic. And now konqueror no longer navigates with a single click:-(

In the past under the "Settings -> Configure Konqueror", in the "File management -- Navigation" tab, there was an option to select single or double click, and now it is not there (ditto in the corresponding tool for Dolphin).

How do I get my single click back?

---

### Post by jtappin on 2018-07-09
I did manage to find a (not ideal) method.

Add the line
SingleClick=true
to the [KDE] section of ~/.config/kdeglobals.

---

### Post by speartip on 2018-07-09
I'm sure from memory it's just a simple case of going to System Settings / Desktop Behaviour / Workspace & "Single Click to Open Files & Folders"

---

### Post by jtappin on 2018-07-10
> **speartip said:**
> I'm sure from memory it's just a simple case of going to System Settings / Desktop Behaviour / Workspace & "Single Click to Open Files & Folders"

That is in effect the same menu as the Konqueror/Dolphin configuation menu, and the option has disappeared there as well. 

The menu changes aren't actually Kubuntu-specific, the options are also missing on my Manjaro machines--but there the original setting has been propagated whereas the Kubuntu upgrade lost the settings.

---

