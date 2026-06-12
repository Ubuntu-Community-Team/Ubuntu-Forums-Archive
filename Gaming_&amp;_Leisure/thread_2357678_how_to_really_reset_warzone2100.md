---
title: "how to really reset warzone2100"
date: 2017-04-04
forum: Gaming &amp; Leisure
---

### Post by migzu on 2017-04-04
I've installed warzone2100. First time playing the game worked fine, but was not fullscreen. I set the game up for native resolution and fullscreen trough the setup-menu, but it seems like I can not launch the game after changing the options. I get

```
info    |04:45:04: [realmain:1145] Using /home/migzu/.warzone2100-3.1/logs/WZlog-0405_044504.txt debug file
error   |04:45:04: [wzMain2:1224] SDL_SetVideoMode failed (Couldn't find matching GLX visual).

```

It does not matter if I run the game as superuser or not. I've tried to reinstalling the package with --purge option selected, but that does not reset the game to the initial state where it worked.

I'm okay with running the game windowed and in the windowed-mode, but how do I get the game back to the initial state without reinstalling the os.

(the debug file has same output with the console)

---

### Post by kostkon on 2017-04-04
The solution can be found in the output you have provided. Delete the folder /home/migzu/.warzone2100-3.1 altogether, that's where the config file(s) is probably being kept.

---

