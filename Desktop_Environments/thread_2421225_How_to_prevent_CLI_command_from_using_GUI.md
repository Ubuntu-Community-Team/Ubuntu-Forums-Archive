---
title: "How to prevent CLI command from using GUI"
date: 2019-06-18
forum: Desktop Environments
---

### Post by dclabaut on 2019-06-18
Hello,
Is there a way to prevent CLI commands from opening windows in the GUI?

For example, in Ubuntu 18.04.2:
- mtr (my traceroute) spawns a GTK windows in the middle of the screen, effectively covering a large part of it. I would like it to run in the split-screen terminal where I typed the command. This way I can stop and restart it, or use a different IP, without having to move a window manually each time.
- when using a password-protected SSH key, I would like the prompt for the password to be in the terminal. The GUI one prevents me from copying the password from Keepass.

Thank you

---

### Post by kpatz on 2019-06-18
mtr on my Ubuntu 18.04 doesn't open any windows, and in fact the -g and --gtk options don't work.  Did you install a different version of mtr, or GTK+?  Or a different desktop manager?  You said Ubuntu, not Kubuntu or Xubuntu or Lubuntu, so I'm assuming the normal gnome 3.

ssh shouldn't open any windows either if you're using the command line tools.  Maybe you're running a ssh agent that has a GUI?

The command **unset DISPLAY** will cause the shell in that terminal to "forget" you're in a GUI environment and prevent anything launched from that shell from accessing the GUI display as well.

---

