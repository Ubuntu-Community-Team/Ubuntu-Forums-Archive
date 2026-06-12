---
title: "Compiz Fusion Confusion"
date: 2007-06-28
forum: Desktop Effects &amp; Customization
---

### Post by dwebb86 on 2007-06-28
OK, I have an Inspiron E1505 with a Nvidia 7300. 
Ordered it from Dell not too long ago with Ubuntu pre-installed so I can start to learn Linux (among other things).
I had the regular Desktop Effects going for a while, then visited these forums and found out about Compiz Fusion. 
I followed all the steps in the guides to install it, and it is successfully on my computer, along with Emerald.  (I see both of them on my System>Preferences menu)

My problem is I can't get Compiz to work. I can pull up the GUI for the program (CCSM) and look at or select any option I want, but nothing happens. 

I've tried **compiz --replace** and ** emerald --replace** separate from each other and together as **compiz --replace -c emerald &** 
No matter how many times I put these commands in, compiz doesn't do anything.
I know my window style and fonts change, so something is happening...
and occasionally, I exit out of the command shell after entering one of those commands and it nearly freezes my screen, I can't type or change windows, and my interface screws up. 
I get different errors sometimes, but just typing that last command into the shell returned these: 
     [B] Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Converting gconf plugin list: ''Checking for nVidia: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Warn: Unknown option '-c'

........
(emerald:9555): Wnck-WARNING **: Unhandled action type (nil)

(emerald:9555): Wnck-WARNING **: Unhandled action type (nil)
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'emerald'
Adding core settings (General Options)[/B]
..................
 **/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity**
...................

I've searched all over forums (these ones and the compiz ones) trying to find what to do...
I hope I'm just doing something stupid and it's an easy fix, any ideas?

D Webb

---

### Post by dwebb86 on 2007-06-29
Ok, I figured out part of what I was doing wrong. 
I spent all day yesterday screwing with this and must have just been tired.
I was typing **compiz --replace -c emerald &** and not **c-**

I was looking at posts and found this out, typed it in correctly, and NOW I see the compiz fusion effects enabled (i.e. my windows are wobbly)....
BUT, all my window borders disappeared, and I can't type or switch windows unless I push Alt+F2 and turn compiz back off with **compiz --replace**

any ideas?

---

