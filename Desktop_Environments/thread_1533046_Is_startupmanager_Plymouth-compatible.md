---
title: "Is startupmanager Plymouth-compatible?"
date: 2010-07-17
forum: Desktop Environments
---

### Post by betlog on 2010-07-17
Is startupmanager Plymouth-compatible?

---

### Post by Frogs Hair on 2010-07-17
I installed it in 9.10 , but was unable to change the splash screen with it. You can ask the on their web site as well , just use the link in the software center and select ask question.

---

### Post by betlog on 2010-07-17
it seemed a little inappropriate asking them how to fix my issue... but I guess they can just ignore me too :]
[https://answers.launchpad.net/startup-manager/+question/118099](https://answers.launchpad.net/startup-manager/+question/118099)

---

### Post by wallpaper_thief on 2010-07-28
theres another GUI that can help you choose an installed plymouth theme, called alternatives configurator

---

### Post by betlog on 2010-07-28
Hmm, ok thnaks. Ths does actually answer my question. thanks
[RIGHT] 
[/RIGHT]
  Kalternatives offers a GUI to configure the alternative systems (a system that allows you to select one alternative file for many in the filesystem). Kalternatives is available as KDE configuration module, integrated by default into KDE's System Settings.

This is an advanced GUI of the update-alternatives program shipped with dpkg.

---

### Post by betlog on 2010-07-28
wel... actually.. it doesnt answer the original question, but it does offer something related and mostly useful

---

### Post by JustinR on 2010-07-28
It doesn't help with changing the themes or anything but it will disable if it you want.

---

### Post by wallpaper_thief on 2010-07-29
> **betlog said:**
> Hmm, ok thnaks. Ths does actually answer my question. thanks
[RIGHT] 
[/RIGHT]
  Kalternatives offers a GUI to configure the alternative systems (a system that allows you to select one alternative file for many in the filesystem). Kalternatives is available as KDE configuration module, integrated by default into KDE's System Settings.

This is an advanced GUI of the update-alternatives program shipped with dpkg.

it pales in comparison to the CLI version of the "update-alternatives" tool, since it only configures currently installed alternatives. with the cli update-alternatives you can do that, but also install new ones,  using 

sudo update-alternatives --install etc etc etc

removes themes, etc.

you can't do that with the GUI provided. As is the case with most tools, the CLI version provides capabilities that GUI doesn't, because implementing ALL the capabilities possible with CLI tools would take more time than is useful. afterall, creating GUIs are most time effective and cost effective when they simply provide tools that average users would use most often, not wasting time including tools only advanced users (not me, btw, lol, i'm still a newbie) would use.

---

