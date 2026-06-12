---
title: "How do settings get applied instantly?"
date: 2011-05-07
forum: Desktop Environments
---

### Post by geoffreymatthews on 2011-05-07
I've been a Windows user for many years. I began using Ubuntu/Linux only recently. 

I noticed that on Ubuntu, all manner of setting changes get applied instantly. In CompizConfig Settings Manager, for example. Almost everywhere in Ubuntu, settings seem to apply instantly, without having to click an Apply or OK.

I wonder how that is possible. I have never seen that in Windows. I tried searching for an answer on the net, but got nowhere. Can anyone give me an answer? I'm not looking for a technical answer. Just wondering if it is specific to Linux/Unix.

Thanks in advance.

---

### Post by Copper Bezel on 2011-05-07
No, it's not, and it's not universal across Linux applications or environments; almost everything in KDE, for instance, requires you to hit an "apply" button, and this saves some time in some situations, as Gnome's theme changes, for example, take a bit to load into memory.

There are various ways that the applications themselves handle this. Some check for the values every time a signal is sent, so the current values are simply adopted automatically; some settings managers trigger the process in question to refresh or restart it completely; and again, some applications don't immediately apply their settings, requiring you to either click an "apply" button or reload the application.

In CCSM, the settings are stored either in a text file or in a series of text files under Gnome's own configuration directories. Values are saved as soon as you leave a text field or click a checkbox, and I think CCSM triggers Compiz to refresh some part of its settings.

---

### Post by geoffreymatthews on 2011-05-08
I have used KDE as well, and ya, stuff doesn't get applied instantly in KDE. Come to think, it's really only CompizConfig and a few other applications in GNOME that have instantly apply's.

Thanks for the reply!

---

### Post by Frogs Hair on 2011-05-08
Preset user permissions are also part of the equation , some settings can't be changed unless allowed by the administrator. When permission is granted you have given the ok.

My Nvidia X sever settings requires that quit button is used to save changes or the settings will revert .

---

