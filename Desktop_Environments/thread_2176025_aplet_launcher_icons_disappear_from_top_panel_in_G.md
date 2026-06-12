---
title: "aplet launcher icons disappear from top panel in Gnome Fallback"
date: 2013-09-22
forum: Desktop Environments
---

### Post by Luxx on 2013-09-22
I installed Ubuntu 13.04 on another computer and never had this happen. A fresh install on a new computer from the same live USB does not behave the same.

First I couldn't find a way to add aplets to the top panel and had to install Alacarte. AWN is no longer available, I guess. Maybe that's why this install is behaving differently? But when I put an icon in the launcher it only works once and then it's gone. If I log out and back in, it's gone. I put certain launchers in my panel for my workflow. How can I keep them there?

If I can't get this computer to work like the other two I've used gnome-session-fallback with I am considering going to Fluxbox as my DE, but that is a whole world of customization projects I don't have time for right now. I have work with deadlines that comes first. I don't have the other computers anymore. Any suggestions for a possible quick fix please?

---

### Post by Luxx on 2013-09-22
Somehow in my searches I found a suggestion to reset compiz to defaults. There was a lovely little piece of terminal instruction. I wish I could link to it because it worked, but I can't find it now that I've rebooted. I'm sure it was somewhere in these forums. Whoever it was, thank you for posting.

---

### Post by Frogs Hair on 2013-09-22
I don't know if this is what you are looking for .  ```
dconf reset -f /org/compiz/
```

---

### Post by ibjsb4 on 2013-09-23
In the future you can check your window manager (compiz) by logging into gnome-classic no-effects at boot (login).  It does not use compiz :)

---

### Post by Luxx on 2013-09-24
Thank you, Frogs Hair. I had a heck of a time finding it in the forums myself. Perhaps adding it to this post will help someone else find the answer.
@ ibjsb4 - I hadn't thought of that.

---

