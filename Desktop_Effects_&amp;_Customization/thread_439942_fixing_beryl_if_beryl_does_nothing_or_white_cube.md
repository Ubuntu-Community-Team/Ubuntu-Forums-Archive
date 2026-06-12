---
title: "fixing beryl if beryl does nothing or white cube"
date: 2007-05-11
forum: Desktop Effects &amp; Customization
---

### Post by emodro on 2007-05-11
hey i've been trying to use Ubuntu for a while mainly for beryl, ive had to reinstall several times as beryl breaks every now and then (especially on updates when i forget to not let beryl update) here's how i finally got everything working.
first I'm running edgy
I installed everything according to this guide
[http://ubuntuforums.org/showthread.php?t=399643&highlight=beryl+xgl+ati](http://ubuntuforums.org/showthread.php?t=399643&highlight=beryl+xgl+ati)

it all worked fine for a while, if you find that nothing works anymore on beryl... try typing

gksudo nautilus ~/
press ctrl+h and delete .beryl and .emerald (this will delete all of your settings)
check to see if it works now.
if not try going into synaptic manager search beryl, remove everything do the above step again
reinstall beryl (restarting wouldn't hurt)

if you get it working but get the whiteCube (press ctrl-alt-backspace to restart your session)
try running this in the command
beryl-manager --no-force-window-manager
you should see the beryl icon on the top right,
 right click->advanced beryl options>rendering path  set it to copy
should be up and running now.
you can also try, if you havn't already
LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa beryl --replace &
 if that works for you try my method of deleting the settings folders and running copy... if those commands do not work make sure you have the right beryl version installed, and not the one from the universe repository.
i'll edit this post when i find more issues i run into.

---

