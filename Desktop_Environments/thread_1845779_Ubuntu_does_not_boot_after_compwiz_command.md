---
title: "Ubuntu does not boot after compwiz command"
date: 2011-09-17
forum: Desktop Environments
---

### Post by Amazonian28 on 2011-09-17
Hi All, 
 
I recently installeld ubuntu 10.04 and have been trying to get the aero snap feature in. Inside the terminal, I typed compwiz and pressed enter accidentally before I had the chance to type in parameters. After that command, my entire window flipped. As in, it was not only upside down, but all the letters were reversed. My terminal now had the oldest command on the bottom, and the newest one on top, and my "compwiz" command looked like "ziwpmoc" upside down and mirrored. I didnt' know how to reverse the effect since it made my computer very laggy as well. So I forced a reboot. now when I choose to boot Ubuntu, it does the initial load but does not get to the ubuntu loading page. It just goes blank, until I press ctrl+alt+del, then the ubuntu logo appears, but a few seconds later, my computer restarts. 
 
Does anyone know how to fix this? I'm clueless since I'm new to linux.
 
Thanks!

---

### Post by Copper Bezel on 2011-09-17
I'm baffled by every part of this.

Do you mean *compiz*?

Edit: Here, a couple of the more confusing things.

* A single command without root privileges can't, to my knowledge, render your computer unbootable. It could muck up your account settings, depending on what happened, but you should still be able to get to the login screen.

* I've never heard of and can't find anything called Compwiz, but Compiz is the window manager and compositor in Ubuntu. It is indeed responsible for the "Snap" behavior, but that plugin isn't available in 10.04.

* How far into the boot process do you get? What do you see on the screen (before you tried the keystroke?) Try pressing Ctrl + Alt + F1 instead to see if you can get to a console screen.

---

