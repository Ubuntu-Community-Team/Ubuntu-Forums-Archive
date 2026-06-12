---
title: "Wrong Keyboard Layout"
date: 2008-04-03
forum: Desktop Effects &amp; Customization
---

### Post by T21 on 2008-04-03
-Installed Hardy Heron, with en_us keyboard layout during install (cant remember if I had any other choice at the moment)

-entered my session, set keyboard layout to fr_ch, which is the actual layout of this laptop, works fine for my session.

BUT:
-keyboard layout is en_us before I login (@Ubuntu login/password GUI)

SO:
-tried editing xorg.conf, had NO impact
-tried reconfigure xserver procedure (which roughly did the same thing: change xorg.conf, correct?), had NO impact.

What am I supposed to do so that I can use consistent keyboard layout throughout utilization?

---

### Post by T21 on 2008-04-05
Right.
So noone on this forum knows of any solution that could help out this simple point.

By the way,
-Icons on desktop are added by the system (after inserting a DVD, for example) UNDER existing ones
-Totem video player is unable to play DVDs (even after downloading "ugly" plugins)
-Return from hibernate cant restore soundcard support
-Return from hibernate also kills the "hdparm -B 255 /dev/sda" command I added to boot, making the HD go "ploing" every 30 sec (which was the default behaviour!) and is so definitely unusable.

I really can imagine why people keep on using win...

---

### Post by vintermann on 2008-04-09
I have a similar problem to you. Keyboard layout used to be set to us?en at inconvenient points, and it has only gotten worse lately. Now every time I log in I have to

1. switch to US keyboard (it claims to be norwegian in Gnome, but is not)
2. switch tab in the Gnome keyboard app (else it ignores me)
3. close keyboard app
4. open keyboard app and switch back to norwegian keyboard
5. switch tabs again
6. then close it.

I am no Linux newbie, but what strange paths my keystokes go through on Ubuntu I have no idea. By the way it is messed up on my machine, it can not be simple.

---

### Post by seenxu on 2008-04-20
I got the same keyboard layout problem, too.

using gusty, setup keyboard model to "generic 104-key pc" with layout "de" variant "deadacute", after login all fine, but before login (username and password gui window) the keyboard layout will be setup back to englich layout, have no idea how to fixit.

or possibly the old time bug #9250 still haven't been fix.

"Ubuntu should have a better method of selecting the keyboard layout"

---

### Post by vintermann on 2008-04-23
There are some seriously race-ish keyboard issues in Ubuntu, it looks like. I  enter two passwords on starting my machine, one for login/disk encryption and another for ssh keys. The first is always norwegian keyboard layout. The second can be either - the most common is that the first popup uses en_us layout, and when it fails, it immediately pops up again with norwegian layout. But sometimes the second has US keyboard, too.
When I've finally logged in, I usually have to do the switching dance described earlier, but sometimes (maybe one in ten times) I actually have norwegian layout as I should, from the start.

I installed Ubuntu (Gutsy) on another machine, exact same problem there. I think I may have used english language in the installer, but definitively not english keyboard.

I'm not adverse to digging into config files, but I need to know where and when keyboard layouts are set in Ubuntu.

---

