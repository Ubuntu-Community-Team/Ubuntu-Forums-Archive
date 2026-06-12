---
title: "problem with gnome-shell"
date: 2010-06-07
forum: Desktop Environments
---

### Post by angry_johnnie on 2010-06-07
i used gnome-shell on jaunty, and on karmic without a problem.

on lucid, however, i can't get it to work.

i've installed it, but when i run gnome-shell --replace, my desktop almost freezes.

it does run gnome-shell.  i mean, i do see the thing:  the panel shows up, and i get this blue desktop, but i can't really use it.  it is incredibly slow (a window might take up to 2 minutes to move).

if i switch to virtual terminal and run top i get mutter all the way up, eating up 100% of the cpu.

so, i kill mutter, and it, in turn, kills gnome-shell.

i installed the repository version and the ppa version, and none worked.  both do the same thing.

graphics card is 256 mb nvidia geforce fx 5200

---

### Post by Peter09 on 2010-06-10
As a first guess I would think you do not have the right graphics driver installed for you card, have you checked that the correct driver is installed?

---

### Post by angry_johnnie on 2010-06-11
:)
Actually, yes.

And, I tried driver 96, 173, and 185.
gnome-shell has behaved the same way with either one of these drivers.

Currently, I'm using driver 96.  Not the newest one, but my card isn't all that new either, and this is the one it works best with.  It is the same driver I used in jaunty and karmic, and then gnome-shell did work without a problem.

I'm guessing it's just gnome-shell.  I mean, it's not a final release yet.  Maybe it'll get better with time.

So far, the only thing i haven't tried is compiling it from source.  I might try that, and then if it doesn't work, I guess I'll just settle for good ol' metacity ;)

---

### Post by eznet on 2010-07-16
My lucid desktop is doing 'the same thing'...  When I kick off gnome-shell, the desktop locks up and I have to ssh in to reboot it... ctrl+alt+f1 doesn't work...  When I ssh in, nothing short of a reboot will allow me to recover (restart gdm, X, etc)... Log displays something about not being able to restart nVidia or something - I will post the error when I get back to the PC (tired of messing with it now).  I know that I have the correct drivers (dual nVidia 8500GTs) and use compiz as my regular windowing system.

Oddly enough, on my lucid eeePC 1000he, gnome-shell works fine.. Much slower than compiz, but functional...

---

