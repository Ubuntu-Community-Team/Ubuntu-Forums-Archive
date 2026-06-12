---
title: "&quot;Swap left alt and left win&quot; keyboard layout works intermittently"
date: 2011-07-10
forum: Desktop Environments
---

### Post by Luke.Hoersten on 2011-07-10
When I swap my left alt with my left win key using the gnome keyboard layout options, the swap only works intermittently. I have an aluminum Apple keyboard with no numpad. No matter what layout options I choose, I can't seem to get it working.

I also have the same setup on my laptop and work desktop and it works without issue. I've ensured my .Xmodmap doesn't exist.

When I say "works intermittently" I mean when I'm trying to use "alt+b, alt+f" navigation in emacs or bash, it doesn't work but if I click around a bit then try again, it works. Also, I use alt+arrows to switch workspaces and that always works.

Any help would be greatly appreciated.

---

### Post by Luke.Hoersten on 2011-07-13
bump

---

### Post by DoubleClicker on 2011-07-13
The problem isn't that it works intermittently, it probably is working correctly.   The problem is that bash and emacs don't use the keyboard options, which you set in the keyboard preferences.  You  probably would get better help, posting  a thread called. " How do I  swap alt and left_win in bash and emacs", in the Main support forum

---

### Post by Luke.Hoersten on 2011-07-13
I'm not sure that's the problem. I have 3 Ubuntu computers with the same keyboard setup/layout and it works fine on the other 2.

---

### Post by DoubleClicker on 2011-07-13
Have you tried creating another user account?  That will help determine if the problem is a system problem or some problem in your home directory.

---

### Post by Luke.Hoersten on 2011-07-13
Great idea! When I logged into the guest account, the same keyboard layout worked exactly as expected (alt and win swapped just fine). That means it must be something with my user account. Any ideas?

---

### Post by DoubleClicker on 2011-07-13
rename .gconf to gconf.bak
log out and log in and see if it works (you should have a default ubuntu desktop)

if that works you can either redo your preferences, or try to find the corruption in the gconf.bak files.

if that doesn't work try the same thing with .gnome2

---

### Post by Luke.Hoersten on 2011-07-13
Removing ~/.gconf worked. Thanks a lot!

---

