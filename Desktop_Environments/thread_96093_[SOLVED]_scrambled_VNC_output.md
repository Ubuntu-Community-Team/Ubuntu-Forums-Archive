---
title: "[SOLVED] scrambled VNC output"
date: 2005-11-28
forum: Desktop Environments
---

### Post by jegHegy on 2005-11-28
hello!

this is my first post, i've just installed Ubuntu 5.10 over the weekend, and having a lot of fun with it.

i've spent countless hours getting VNC to work on display :0, and the solution seemed to be vnc4server's vnc.so (renamed to libvnc.a as someone on the forum suggested, which i don't get sinse it's mentioned nowhere in the documentation, as far as i could see). finally got it up and running after a few failed attempts, no errors/warnings about VNC in Xorg's log.

i can connect fine, others can connect fine, but i get a VERY weird scrambled screen. i've googled and searched this forum for hours trying to find someone else with this problem, to no avail. attached is a screenshot of the phenomenon.

thank you in advance for anyone who can give me a tip as to what could be the cause of this.

---

### Post by ajgreeny on 2005-11-28
I saw this sort of scrambled display once just after installing the fglrx video driver and doing a control/alt/backspace to restart X.  After a rebot however it was all OK and has been ever since, though it did take a little while and some tweaking to get the fglrx to work properly.

---

### Post by jegHegy on 2005-11-28
i forgot to mention that i do have fglrx installed. i'll try rebooting, although X and GDM has been restarted numerous times since i've enabled the vnc module. i'll report back, thanks. :)

---

### Post by Jonne on 2005-11-28
have you tried different viewers? I see you use realvnc, maybe it's an older version or something.

I'd give it a shot with ultravnc, or tightvnc.

---

### Post by jegHegy on 2005-11-28
neither did rebooting or different VNC clients help, same results. :(

edit: ditched the vnc module method altogether and used x11vnc instead. works like a charm. :) thanks for the replies!

---

