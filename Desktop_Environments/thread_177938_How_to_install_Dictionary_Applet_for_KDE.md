---
title: "How to install Dictionary Applet for KDE?"
date: 2006-05-17
forum: Desktop Environments
---

### Post by linuxa on 2006-05-17
Hi there

What packages do I need for the Dictionary applet so that it appears as an addition to the Applet list in the Panel Menu?

This could be too much of a noob question since posts to do with said applet all seems to be associated with how to configure it. People seem to get right away how to install it (or have was it meant to be installed by default?)

I've been meaning to install the packages dict, dictd, dict-gcid. But those might not really be the ones that I'm looking for.

Can anyone point me in the right direction please?

Thanks in advance :mrgreen:

---

### Post by ajgreeny on 2006-05-17
You can use synaptic or apt-get to install gnome-dictionary, and then make a panel link to the application quite easily by right clicking in an empty area of the panel.  I use Kubuntu with KDE but prefer gnome-dictionary to the KDE kdict version and it works well in KDE so should be OK in gnome.

---

### Post by linuxa on 2006-05-21
Thanks for the reply **ajgreeny**. But I was thinking of having something like a searchable dictionary in the KDE panel as in the screenshot.

Any ideas?

(image from article at: [http://www.linuxjournal.com/node/8668/print](http://www.linuxjournal.com/node/8668/print))

---

### Post by aysiu on 2006-05-21
Have you tried this? ```
sudo apt-get update
sudo apt-get install kicker-applets kdict
```

---

### Post by linuxa on 2006-05-27
[QUOTE=aysiu]Have you tried this? ```
sudo apt-get update
sudo apt-get install kicker-applets kdict
```[/QUOTE]


Thanks, that worked wonderfully :D

---

