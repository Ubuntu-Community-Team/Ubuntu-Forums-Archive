---
title: "Unable to use virtual consoles"
date: 2009-05-14
forum: General Help
---

### Post by Reilithion on 2009-05-14
I'm running Jaunty on an AMD64 with dual monitors.  Ever since I edited my Xorg configuration file to make use of both of my graphics cards, I've been unable to switch to a virtual terminal.

When I try, with Ctrl-Alt-F3 for instance, both screens go black and then the primary screen shows that it's in an invalid video mode.  I suspect I could type, login, and issue commands, but since I can't see what I'm doing it's difficult to know for sure.

I'm always able to use Ctrl-Alt-F7 to return to my X session, and I've only observed this behaviour once an X session has been started.

I edited my xorg.conf file while running Intrepid and had this issue at that time as well -- upgrading hasn't fixed it.

I really rather need my virtual consoles.  I'd appreciate any clues anyone has.

---

### Post by Reilithion on 2009-05-31
Attached is my xorg.conf for reference.  Seems correct, but maybe I am missing something?

---

