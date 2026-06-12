---
title: "Openbox: keyboard repeat problem"
date: 2009-08-06
forum: Desktop Environments
---

### Post by matt_garman on 2009-08-06
I installed Openbox (via apt-get install openbox).  I then selected Openbox from the session menu ("vanilla" Openbox, i.e., no KDE or Gnome).

Openbox appears to start and work correctly, except for the keyboard.  Whenever I press a key, it randomly repeats from one to five times.  It's practically impossible to type, since the behavior also applies to the backspace key!  (E.g. say I want to type "ls", I type 'l', then 's', but I actually get "lssss", so I hit backspace, but it actually removes everything I typed, as though it registered five or more backspaces.)

This happens in both a terminal window and Firefox.

Other window managers don't display this behavior.

---

### Post by matt_garman on 2009-08-09
I somewhat figured out the problem.  I created a new account, logged into Openbox, and had no weird keyboard issues.  So I started copying dotfiles (files beginning with a period '.') from my old home directory into the new account's home directory.  I copied them one-by-one, copying, then logging out and back in.

Ultimately, it was the **.gconf** folder than contained something that screwed up the keyboard.

I noticed that this also affected GNOME.  Prior to trying Openbox, I was using Enlightenment DR17 (e17).  With a little digging, I found that Openbox by default loads the gnome config stuff (whereas e17 doesn't).  So, that's why the problem affected GNOME as well.

Anyway, I accidentally got sloppy and overwrote the offending .gconf folder, so I don't know exactly what setting caused the problem.  But if it comes up again, at least I know where to look.

Hopefully if anyone else runs across this keyboard repeat problem, they'll find this post useful.  :)

Thanks again!
Matt

---

