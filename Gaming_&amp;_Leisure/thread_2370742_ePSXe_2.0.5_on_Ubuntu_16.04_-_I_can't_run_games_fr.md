---
title: "ePSXe 2.0.5 on Ubuntu 16.04 - I can't run games from CD"
date: 2017-09-06
forum: Gaming &amp; Leisure
---

### Post by tziulm on 2017-09-06
Hi,
I've installed ePSXe 2.0.5 on my pc some time ago (using this script, because it wasn't working before: [https://github.com/brandleesee/ePSXe64Ubuntu](https://github.com/brandleesee/ePSXe64Ubuntu) ), but if I try to run a game from a CD absolutely nothing happens. I've tried  to see if there was an option to change, but If I try to open the plugin  configuration page I get a message telling me that there's nothing to  configure. If I use ISO files it works fine.                 

Trying to run it from a terminal, that's what I get:

```
~/Scrivania/ePSXe205linux_x64$ ./epsxe_x64
* ePSXe change dir to /home/luca/.epsxe/
* Running ePSXe emulator version 2.0.5.

(epsxe_x64:5854): Gtk-CRITICAL **: gtk_widget_get_preferred_width_for_height: assertion 'height >= 0' failed

(epsxe_x64:5854): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width 1 and height -5

```

If I try to make a game run from CD nothing happens or changes.

I tried to ask for help on their forum as well (thread: [http://ngemu.com/threads/epsxe-2-0-5-on-ubuntu-16-04-i-cant-run-games-from-cd.200441/](http://ngemu.com/threads/epsxe-2-0-5-on-ubuntu-16-04-i-cant-run-games-from-cd.200441/) ), but they told me to ask here, saying that "
(epsxe_x64:5854): Gtk-CRITICAL **" could be a problem.

---

