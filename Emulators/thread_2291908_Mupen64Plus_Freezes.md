---
title: "Mupen64Plus Freezes"
date: 2015-08-23
forum: Emulators
---

### Post by cranerja on 2015-08-23
When launching either mupen64plus through the terminal and through M64PY, it freezes on "Mupen64Plus started...". All the packages have been installed and this still happens. 
It is also odd that when using the gui, I have to set the paths manually.
(On 14.04)
Any information?

---

### Post by deadflowr on 2015-08-24
Moved to the ***Emulators*** subforum.

You might need to see if using a different Video plugin helps.

I'd look at the configuration file in /home/you/.config/mupen64plus/mupen64plus.cfg.
I believe it installs only the rice video plugin, but there are a few others which are available, or at least one other: glide64)

You can look in /usr/lib/x86_64-linux_gnu/mupen64plus for the names of any other video plugin you can try.

That's my initial two cents to start, at least.

---

