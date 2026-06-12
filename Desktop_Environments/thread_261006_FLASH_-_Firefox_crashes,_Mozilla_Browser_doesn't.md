---
title: "FLASH - Firefox crashes, Mozilla Browser doesn't"
date: 2006-09-19
forum: Desktop Environments
---

### Post by kekojeep on 2006-09-19
Hi there guys.. after experimenting with various topics about fixing flash sound problems, my situation is this: the only way to get flash working WITHOUT CRASHING JUST ON MOZILLA WEB BROWSER is to use the commands 

sudo mkdir -p /tmp/.esd/
sudo touch /tmp/.esd/socket

then Flash works, sound OK, no crashing in youtube but this only works in Mozilla Web Browser.. Firefox doesn't open anymore after I use those commands in prompt, before using the commands Firefox opens but hangs at 2 sec when viewing Youtube videos..

Before using commands, both browsers open but both crash at 2 seconds of flash video on Youtube.. after commands, Mozilla Browser works, but I gotta type those two commands everytime I log in. My questions: 

- How do I make this command automatically executed at login?
- How do I make Firefox work just like Mozilla Browser is working now?

Any help will be greatly appreciated!

Thanks,

André Tomasi

---

### Post by kekojeep on 2006-09-20
Anybody? Still with the same problem, can't understand why works in Mozilla Browser but not in Firefox..

[ ]'s

---

### Post by neymac on 2006-09-20
Try install Swiftfox and see if there is same problem.

See [http://getswiftfox.com/ubuntu.htm](http://getswiftfox.com/ubuntu.htm)

---

### Post by kekojeep on 2006-09-20
Neymac, thanks for the tip.. on Switfox, flash worked like a charm with no complications.. I'm switching to Swiftfox for now, though I'm still curious about what's the matter with Firefox + Flash..

Thanks for the help!

[ ]'s

---

