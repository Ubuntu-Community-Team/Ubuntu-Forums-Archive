---
title: "keyboard not working in hardy!"
date: 2008-12-10
forum: General Help
---

### Post by deewanagan on 2008-12-10
Hi ubuntu geeks!
i have an hp laptop, in which i have installed ubuntu and windows. i have been using ubuntu for about 8 months now. everything was working well till this morning.this morning i was working on it, and suddenly keyboard stopped working. i don't remember installing/removing anything in last days. i can log in,mouse(built in) works fine, but i can't use my keyboard. any help is appreciated. thanks

---

### Post by ajcham on 2008-12-10
Just to eliminate the possibility of a hardware problem, have you tested the keyboard in Windows?

---

### Post by deewanagan on 2008-12-10
yeah, i m using windows right now, plus i can log in to ubuntu(can write my user name and password).

---

### Post by ajcham on 2008-12-10
Are you using Gnome or KDE?

If KDE, [this link]("http://symbolik.wordpress.com/2007/05/11/ubuntu-keyboard-problem/") describes what appears to be the same problem.  Let me know how you get on.

---

### Post by deewanagan on 2008-12-11
Hello! i m using gnome, so ur suggestion work, but i found something similar under the home directory "/.gconf/desktop/gnome/accessibility/keyboard
" for gnome. but it ddnt work also.
please help!
thanx

---

### Post by ajcham on 2008-12-11
I think we are nearly there. It is almost certainly related to something in your .gconf, and the accessibility options seem to be prime suspects.

A lot of people with this issue just delete their .gconf, but obviously you lose a lot by doing that.  I would suggest removing (or better yet, renaming) the ~/.gconf/desktop/gnome/accessibilty directory and seeing if that fixes the problem.

If it doesn't, I would try renaming the .gconf directory to gconf.bak, or something.  That will almost certainly solve it, and then you would be able to restore your config files a few at a time until the problem recurs. This would be very useful, as you would be able to keep most of your configuration, and you will have identified the file which caused the problem, which will be very helpful to other users.

Good luck!

---

### Post by deewanagan on 2008-12-12
Hello,
so the trick did work, and problem solved. thanks for help. the problem was with the keyboard config file under .gconf directory. i renamed it and after restarting the machine, another file was generated automatically and keyboard was working.

---

