---
title: "KMenu"
date: 2006-06-04
forum: Desktop Environments
---

### Post by justin.tyler on 2006-06-04
I'm having some serious trouble with the kmenu. I upgraded using adept, and all went well, except that KDE didn't upgrade. I'm guessing this could be because it asked me about upgrading the kdedeamon or something like that, and I told it no, because I was unsure if the necessary termination of KDE would affect adept's progress.

Long story short, I manually installed kde from the repository. The issue is, my kmenu is non existant. The taskbar is only displaying one thing, an icon for firefox. It doesn't show open programs, no clock, no kmenu. I can edit the kmenu however, but it still doesn't show up. I've tried sudo apt-get -f install, sudo apt-get install kdm, sudo apt-get install kubuntu-default-settings, etc.

Does anyone have any ideas?

---

### Post by manubreizh on 2006-06-06
hi,
did you try 
sudo apt-get install kubuntu-desktop ? maybe it's kicker missing...
you can also try with the key codes (ini my case, Alt+F1 makes kmenu appear), or with a right-click on the panel, you can add applets (like kmenu button)...
hope that'll solve your problem

---

