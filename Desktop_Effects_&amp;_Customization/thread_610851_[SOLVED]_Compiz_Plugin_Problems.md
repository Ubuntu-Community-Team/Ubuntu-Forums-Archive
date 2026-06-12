---
title: "[SOLVED] Compiz Plugin Problems"
date: 2007-11-12
forum: Desktop Effects &amp; Customization
---

### Post by The_PhAnT0m on 2007-11-12
I'm using Ubuntu 7.10 and Compiz. I am using CompizConfig Settings Manager to manage Compiz's settings. For some reason when I click on some of the plugins to activate it, and then I go somewhere else and come back, the plugin is deselected and won't turn on. Anyone know why?

---

### Post by Zorael on 2007-11-12
Try switching to a flat-file configuration backend in preferences, it helps in many cases.

---

### Post by The_PhAnT0m on 2007-11-12
Thanks for the help. A flat-file configuration backend is the only option for the backend and so it is already being used. Any other ideas?

---

### Post by Zorael on 2007-11-12
Ah, hm, that's a new one.

Are you starting Compiz via a script, or a launcher? If so, try adding 'ccp' as an argument to it; that will make it use its own flat-file format.

For instance, this is my script (with Nvidia tweaks):
```
__GL_YIELD="NOTHING" compiz --loose-binding --ignore-desktop-hints ccp
```

---

### Post by rundee_f on 2007-11-12
have u installed the extra plugins for compiz (dependancies)?

---

### Post by The_PhAnT0m on 2007-11-13
@rundee_f: I installed all the plugins and a installed them through Synaptic.

@Zorael: I tried the command you suggested(I have an Nvidia card) and the same thing hapened. I ran it through a terminal to see if it would say what was happening. When I went to turn on the Expo plugin, it said:
```
/usr/bin/compiz.real (core) - Error: Can't load plugin 'expo' because it is built for ABI version 20070606 and actual version is 20070915
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'expo'
A handler is already registered for the path starting with path[0] = "org"
```

It than repeated the last line MANY times. The same thing happened for all the plugins that wouldn't work. Mean anything to you? Thanks again for the help.

---

### Post by gillis on 2007-11-13
i have the same problem.. some plugins like negative screen cant be enabled. i can click on the checkbox, but when i come back to the option screen its disabled again.. i also installed all plugins.

---

### Post by The_PhAnT0m on 2007-11-16
I fixed my problem. I replaced the package compiz-compcomm-plugins-main with compiz-fusion-plugins-main and then I could use all the plugins. And as an added bonus there were even more plugins. :) Thanks for the help!

---

