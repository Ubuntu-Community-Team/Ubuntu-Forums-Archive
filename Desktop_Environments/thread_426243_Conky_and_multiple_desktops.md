---
title: "Conky and multiple desktops"
date: 2007-04-28
forum: Desktop Environments
---

### Post by koshatnik on 2007-04-28
Hello, 

Just compiled and installed conky 1.4.5 and im having a weird problem - in both fluxbox and in gnome, when I switch desktops conky disappears on the other desktops. It still remains visible in desktop 1 though. Its annoying because its never done this before. I even tried the repo's version and that does it too. Have I enabled, not enabled something stupid in the conkyrc file that makes it behave like this?

This is a clean ubuntu install on Edgy.

Any suggestions? (probably done something stupid)

---

### Post by herrma29 on 2007-07-27
bump...I'm having the same problem.

---

### Post by herrma29 on 2007-07-28
Alright, figured it out.

I added this to my conkyrc file:

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

I'm not sure exactly which part does what, but it worked for me to get my conky to A. Stay up when using the show desktop button and B. show on all desktops.

---

### Post by alexrudd on 2008-04-18
> **herrma29 said:**
> ...
I'm not sure exactly which part does what, but it worked for me to get my conky to A. Stay up when using the show desktop button and B. show on all desktops.In case anyone still cares, the key is "sticky" as an option after "own_window_hints"

---

