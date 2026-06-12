---
title: "gnome borked"
date: 2007-06-14
forum: Desktop Environments
---

### Post by konungursvia on 2007-06-14
was fixing deluge now gnome justshows dark brown bg and arrow cursor; fluxbox works. help?

---

### Post by konungursvia on 2007-06-14
after login, brown screen only, i mean.

---

### Post by ynnhoj on 2007-06-14
if you do an "ls -a" in your home directory, you should find some hidden directories:
[list]
[*]~/.gnome
[*]~/.gnome2
[*]~/.gnome2_private
[*]etc..
[/list]
i've found in the past that the easiest way to fix a buggered up gnome was to wipe out some of this stuff (ie "rm -r .gnome2"), but you're bound to lose some of your settings.  you might want to poke through some of these files first!  do you have deluge set to start automatically when you log in to a gnome session?

---

