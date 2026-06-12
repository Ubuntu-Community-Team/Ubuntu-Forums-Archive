---
title: "Howto handle unresponsive lock screen"
date: 2020-11-30
forum: Desktop Environments
---

### Post by AllesMeins on 2020-11-30
From time to time I'm confronted with an unresponsive lock screen, making it impossible to unlock my system after it went to sleep. The problem comes in two different flavours: Sometimes I can type my password and confirm with Enter and than nothing happens. Other times I can't even get to the password prompt because the lock screen won't respond to any key presses. Since I can't find any pattern it is probably hard to debug, so I'm more interested on your input on how to recover from such a situation. As far as I can tell it is indeed only the password promt that is having problems. I can use my mouse, I can even click the "suspend"-button in the top right corner and it works as expected.

All my other processes seem to still be running as well - I can change to another console and see the CPU load of my open programs - so I'd like to find a way to get back into my system without having to restart and losing all my unsaved data. So, do you have any tips on how to handle such a situation? (Of cause if this is a known problem with a working solution so this doesn't happen again at all, i take it as well :-) )

I'm using Ubuntu 20.04 with the newest updates.

---

### Post by skipbarker on 2020-12-07
Sleep issues are always fun. Have you tried restarting GDM from another TTY session? I'd also look at hardware drivers, they are usually the culprit for sleep issues.

---

