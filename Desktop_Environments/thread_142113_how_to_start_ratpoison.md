---
title: "how to start ratpoison?"
date: 2006-03-09
forum: Desktop Environments
---

### Post by evaristegalois on 2006-03-09
I downloaded ratpoison and installed it. However, (1) when I start it from the gnome-terminal I get the error message: ``ratpoison: there can be only ONE'' (assuming that it can't be open at the same time as gnome); (2) I go to the system console (Ctrl-Alt-F1) and invoke ratpoison, it complains that it cannot open display. How do I get ratpoison started? [P.S.: I am very new at linux and just want to use emacs on a screen that maximizes screen space -- ratpoison seems to be very good at this.]--evaristegalois

---

### Post by evaristegalois on 2006-03-09
On the other hand, you could just tell me how to make xterm be full-screen. (There is a hacker's solution out there but I'd shy away from that stuff.) --evaristegalois

---

### Post by Wolki on 2006-03-09
> **evaristegalois]I downloaded ratpoison and installed it. However, (1) when I start it from the gnome-terminal I get the error message: ``ratpoison: there can be only ONE'' (assuming that it can't be open at the same time as gnome) said:**
> --evaristegalois

Did you install it from the repositories? If you did, it should be automatically added to your login-screen options (under session), at least it does on Dapper. If it doesn't, save the following as /usr/share/xsessions/ratpoison.desktop:

> [Desktop Entry]
Encoding=UTF-8
Name=Ratpoison
Comment=Start Ratpoison as your window manager
Exec=ratpoison
Icon=
Type=Application

> On the other hand, you could just tell me how to make xterm be full-screen. (There is a hacker's solution out there but I'd shy away from that stuff.) 

In Gnome (with Metacity)? Open the Keyboard Shortcuts dialog (system->preferences->keyboard shortcuts), set a suitable shortcut for toggle full-screen, start xterm and use that keyboard shortcut. :)

---

### Post by evaristegalois on 2006-03-10
I am using Breezy, and yes, you are right, under ``Session'' at login I have the option to start with ratpoison. Thanks for the pointer! Secondly, I was already looking for help on keyboard shortcuts in gnome, and here they are! Great! Thanks a lot. I was astonished, however, to see that my new ratpoison terminal starts out with a gnome menubar(!) -- ratpoison is all about getting rid of clobbery things like menubars. The menubar can easily be removed (Alt-v b), but I imagine in the long run it's cumbersome to have to do that everytime you open a new terminal in ratpoison -- no menubars etc. being the whole point of the operation. Again, great help. Danke.--evaristegalois

---

### Post by Wolki on 2006-03-10
[QUOTE=evaristegalois]Secondly, I was already looking for help on keyboard shortcuts in gnome, and here they are! Great![/quote]

You can also set custom keyboard shortcuts for commands. You'll have to do that via the gconf-editor however, as a good GUI for this wasn't finished.  The relevant parts are under /apps/metacity/global_keybindings and /apps/metacity/keybinding_commands

> Thanks a lot. I was astonished, however, to see that my new ratpoison terminal starts out with a gnome menubar(!) -- ratpoison is all about getting rid of clobbery things like menubars. The menubar can easily be removed (Alt-v b), but I imagine in the long run it's cumbersome to have to do that everytime you open a new terminal in ratpoison -- no menubars etc. being the whole point of the operation. Again, great help. Danke.--evaristegalois

I'm not sure if removing menu bars is really ratpoison's point, as many programs don't work without menu bars. In this case, however it's probably because you're using gnome-terminal (the default terminal), use e.g. xterm instead. IIRC the HIG requests for full screen programs to drop their menu bars, so this might be a HIG bug in gnome-terminal.

---

### Post by evaristegalois on 2006-03-12
Thanks. I'll look into this some more.

---

