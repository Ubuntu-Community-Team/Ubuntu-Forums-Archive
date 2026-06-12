---
title: "Unity crashes when I move the cursor over menus."
date: 2010-10-31
forum: Desktop Environments
---

### Post by linux.is.skynet on 2010-10-31
I installed it on a desktop to try the Unity interface (net-book) since it'll be standard in the next release. The whole GUI reloads when I move the mouse over the menus. Sometimes it locks up and I have to alt-f4 reboot. I've tried both the Ubuntu Nvidia driver and the one from Nvidia's site. Gnome 2 and 3 work fine with 3d effects... Help? Thanks!

---

### Post by linux.is.skynet on 2010-10-31
Does anyone have any ideas? I can't find any answers on Google.

---

### Post by P4man on 2010-10-31
alt f4 reboot? Enlighten me?
How do you start unity? It should be selected as session in GDM, not started from the CLI.

---

### Post by linux.is.skynet on 2010-11-01
Alt F4 is a typo. I meant CTRL-ALT-F4 then CTRL-ALT-DEL since it freezes so bad that it's the only way to reboot other than holding the pwr button.  I don't start it from the CLI. I use the ubuntu-netbook option in GDM. When it loads, the interface flickers when I move my mouse over the left-hand panel. The GNOME top panel is not affected.

---

### Post by P4man on 2010-11-02
you shouldnt have a gnome top panel in netbook mode. Try uninstalling unity and install ubuntu-netbook instead. It includes unity.

---

### Post by Ryan Dwyer on 2010-11-02
I get the same behaviour on both my laptop and desktop. One has Intel graphics, the other ATI.

I installed it using apt-get install unity and selected it from the login screen. The "gnome top panel" the OP is referring to is Unity's top panel.

There's a Launchpad bug here: [https://bugs.launchpad.net/bugs/668013](https://bugs.launchpad.net/bugs/668013)

---

### Post by linux.is.skynet on 2010-11-02
@Ryan

Thanks, yeah I consider that the Gnome panel, I haven't really used Unity yet. I've added myself to those affected in Bug #668013.

---

### Post by SpUpUz on 2010-11-04
i have also the same problem

---

### Post by linux.is.skynet on 2010-11-04
I'm just going to keep an eye out for the a dev release of the Desktop version of Unity.

---

### Post by SpUpUz on 2010-11-05
is there any news on that problem?

---

### Post by linux.is.skynet on 2010-11-08
It doesn't look like it.

---

### Post by davbren on 2010-11-09
I'm getting a Unity hang also, a bit intermittent but still inconvenient.

---

