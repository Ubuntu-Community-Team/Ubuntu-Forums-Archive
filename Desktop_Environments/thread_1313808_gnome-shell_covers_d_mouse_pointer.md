---
title: "gnome-shell covers d mouse pointer"
date: 2009-11-04
forum: Desktop Environments
---

### Post by madmax1735 on 2009-11-04
i am using gnome-shell, earlier gnome-shell was covering the mouse, as in mouse pointer was under the gnome-shell instead of top 


this got fixed by switching to metacity from mutter ,

**now i can c the mouse but i still cant click on the gnome-shell** , 

hover thing works though for the main activites menu

i did c this error 

```
Clutter-CRITICAL **: clutter_id_pool_lookup: assertion `id < id_pool->array->len' failed
```

when i ran the ```
gnome-shell --replace
``` command

---

### Post by madmax1735 on 2009-11-04
bump

someone... help

---

### Post by madmax1735 on 2009-11-06
okey these are the errors i get when i try to click on something which is part of the gnome-shell, and ya i can use the tray icons put in by pidgin, sound, etc. 

```
(mutter:8848): Clutter-CRITICAL **: clutter_id_pool_lookup: assertion `id < id_pool->array->len' failed

(mutter:8848): Clutter-CRITICAL **: clutter_id_pool_lookup: assertion `id < id_pool->array->len' failed
Window manager warning: Log level 16: Error converting selection
Window manager warning: Log level 16: Error converting selection
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2400003 (Authentica)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2400003 (Authentica)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

(mutter:8848): Clutter-CRITICAL **: clutter_id_pool_lookup: assertion `id < id_pool->array->len' failed

(mutter:8848): Clutter-CRITICAL **: clutter_id_pool_lookup: assertion `id < id_pool->array->len' failed

(mutter:8848): Clutter-CRITICAL **: clutter_id_pool_lookup: assertion `id < id_pool->array->len' failed
Window manager warning: Log level 16: Error converting selection
Window manager warning: Log level 16: Error converting selection
      JS LOG: conforming method: IntrospectRemote for org.freedesktop.DBus.Introspectable
      JS LOG: Loading tweener.js
      JS LOG: Loading tweenlist.js
      JS LOG: Done loading tweenlist.js
      JS LOG: Done loading tweener.js
      JS LOG: Loading equations.js
      JS LOG: Done loading equations.js
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!

(mutter:8848): Clutter-CRITICAL **: clutter_id_pool_lookup: assertion `id < id_pool->array->len' failed
```

---

### Post by madmax1735 on 2009-11-07
bump.

---

### Post by madmax1735 on 2009-11-15
bump agn.

noone know abt clutter & mutter & gnome-shell

help!

---

### Post by Sov on 2009-11-16
I have a similar problem here... I can click on icons, screens and menues in the overview but only if the pointer is on odd (or even, not sure) orizontal lines.

If I move the pointer down by a line the screen is no longer sensitive to clicks moving down one more line make it work again!

Ubuntu Karmic with gnome-shell from the official repository on Intel GMA, I have another computer with the same software version but an nvida gfx borad not showing the same problem.

I suspect it has something to do with the glx driver.

---

### Post by madmax1735 on 2009-11-17
humm.... i was just wondering... did u make d install from a "pen-drive/thumb-drive" ??????

also i dont have a xorg.conf file. supposed to b default for new xorg since jaunty.


i tried tweeking around with my xorg.conf.... it didnt turn out well cause i couldnt get much abt it.


also i think our issue is related to this 

 > Bug 503251 -  Clutter picking is corrupted with Intel 965GM   [NEEDINFO]


filed at 

[https://bugzilla.redhat.com/show_bug.cgi?id=503251](https://bugzilla.redhat.com/show_bug.cgi?id=503251)

which goes like,

> On my machine, which has an Intel 965GM chipset the pick colors are sometimes
read back in incorrectly. They end up being the actual actor colors. This
happens randomly, as in I'd mouse over a simple clutter actor such as a
rectangle and some reads will come back correct and some won't. This problem
only started occurring after the following Clutter commit that introduced
clipping the pick area to a single pixel before repainting it in the pick color
and reading the pick color value:
[http://git.clutter-project.org/cgit.cgi?url=clutter/commit/&id=d1fa83039d12f8501075d3e9f7fd17a42cbdd7c8](http://git.clutter-project.org/cgit.cgi?url=clutter/commit/&id=d1fa83039d12f8501075d3e9f7fd17a42cbdd7c8)


again i couldnt understand much from the commit, hope someone can figure this out.

---

### Post by Sov on 2009-11-22
Just tried Ubuntu 9.10 network remix and found the same problem as in gnome-shell. Again, the remix frontend uses clutter.

---

### Post by madmax1735 on 2009-11-22
i was just wondering if there is a way of making gnome-shell use something else instead of clutter/mutter , mostly because all the appellets (eg. rhythmbox, deluge, thunderbird, etc) seamed to work fine even while using gnome-shell

also a work around must exist for users who want to use UNR, an have problem with clutter/mutter

btw way i also tried ubuntu UNR from a pen drive and yes it dint work out for me, faced same problem as gnome-shell

:(

---

### Post by broomfighter on 2009-11-24
I can confirm this.
I've got an Intel GMA, too.

---

### Post by madmax1735 on 2009-11-25
i think our problem is related to  > Bug 521714 -  Clutter picking broken on Intel 855GME   at

[HTML]https://bugzilla.redhat.com/show_bug.cgi?id=521714[/HTML]


because i faced the problem with Ubuntu 9.10 UNR and ubuntu 9.10 (Desktop edition), when using mutter/clutter

beacuse of this issue its not possible to run UBUNTU UNR on intel 855GM

---

### Post by twkonefal on 2009-11-29
i don't think it's related to the intel driver since i'm having the same problem using the latest (beta) nvidia driver: NVIDIA-Linux-x86_64-195.22. i'll try the last stable driver and see how it goes.

nope, that didn't help.  i can still see my pointer until i move my mouse near or onto the black top bar with the "Activities" label.  when i click there, the shell appears, but my mouse pointer is invisible, though usable across the whole screen until i hit ESC and exit the activities shell. boo.

found this thread:  [http://ubuntuforums.org/showthread.php?t=1294059](http://ubuntuforums.org/showthread.php?t=1294059)

ALT-F2 -> "restart"

that fixes it. w00t :)

---

### Post by Kareeser on 2010-02-07
Another one here, although I can't report it since I'm using a PPA, instead of from repositories.

855GM, so I guess I'm out of luck for using gnome-shell, eh?

```
(mutter:3933): Clutter-CRITICAL **: clutter_id_pool_lookup: assertion `id < id_pool->array->len' failed
```

---

### Post by Bubbel on 2010-02-21
Same problem here.
I put gnome-shell in startup applications (of course with the --replace options).
When I started a terminal and killed gnome-shell and mutter, and afterwards restarted gnome-shell the problem was resolved.
I also have an Intel Chipset in my laptop, but I don't know if this is an option.

Whe I know more, I'll get back.

Greets, Bubbel

---

### Post by xerman on 2010-02-26
Hello there:

I have similar issue also on a Sony Vaio that uses Intel GMA. Can use the mouse on the desktop, but not on the top bar nor the side bar, nor the Activities window.

Typing "Alt+F2" and then "restart" solves the issue for the session. Next time log in need to redo the "Alt+F2" and then "restart" again.

Also most times need to click twice or three times or even more to get response from the Gnome-Shell.

Also the Maximize button on windows does not respond to middle click nor right click, just left click. Maybe is a feature of the Gnome-Shell.

By the way, I have no battery indication on the top bar for the laptop, so this should be solved too.

Anyway, once it is finished can be good, now is promising, and still alpha, for what i am experiencing.

Regards to all.
Xermán

---

