---
title: "Gnome occasionally starts ignoring user input"
date: 2007-12-13
forum: Desktop Environments
---

### Post by malachias on 2007-12-13
Hi

Every so often, gnome stops accepting user input. It's weird. The mouse moves, but won't click, and things that should be affected by mouseovers aren't. Assuming a text-field is in focus, typing won't do anything. Not even Ctrl-Alt-Backspace (restart gdm) or Ctrl-Alt-F1 (get to a tty) do anything.

However, the text cursor keeps blinking, unplugging/replugging in the network cable will connect/disconnect me from the network (and the network manager applet shows all its little animations without problem), and unplugging/replugging the power source (I'm on a laptop) pops up the 'running on batteries' tooltip and dims the monitor, etc. I can even continue to receive messages on pidgin.

I have a core 2 duo processor, and nothing's running at even close to 100% cpu, unless conky is lying to me. So far, the only "solution" i have found is to get to another computer (if available), ssh in and restart gdm.

Anyone else getting this?

---

