---
title: "Keyboard shortcuts settings GUI and lxqt-rt.xml are seeing keyboard differently"
date: 2019-01-25
forum: Desktop Environments
---

### Post by pling on 2019-01-25
The settings gui recognises the windows key as meta, so it eg lets my launch rofi on meta-q. But nothing I've tried works in the xml file - not W, S, M, Super_L, or Meta. And yes, I've restarted openbox, and yes the key combos I've written work as eg Alt-spacebar, etc.

---

### Post by pling on 2019-01-25
...I disabled the keyboard shortcut settings tool in autostart and the xml file worked properly when I rebooted. I should say that the shortcuts in the xml that weren't working were NOT using duplicate key combos to any in the gui tool.

This is, frankly, **appalling.** Firstly because when tools are chained that way then earlier ones shouldn't mess things up for later ones - this is a basic violation of how such chains are supposed to work, especially in linux. Presumably someone decided the deliberately break this principle (why?) And secondly because either testing of lubuntu was so poor that no one spotted this problem, or because people were aware the problem was there AND THEY DIDN'T EVEN ADD A WARNING NOTE TO THE XML FILE.

---

### Post by faure212 on 2019-02-07
I don't see anything named: "[COLOR=#000000]keyboard shortcut settings tool " or similar in the autostart tab of the LXQt Shortcuts settings.  I would like to try and disable it, hoping that the shortcuts might work, but I don't know how.[/COLOR]

---

