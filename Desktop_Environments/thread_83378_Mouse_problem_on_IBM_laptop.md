---
title: "Mouse problem on IBM laptop"
date: 2005-10-28
forum: Desktop Environments
---

### Post by anderss on 2005-10-28
Hey - just signed up

I have this problem with that little red joystick thingy on my IBM Thinkpad laptop. The mouse makes some pretty frequent (but not predictable) "spasms" where it moves all over the screen clicking random mousebuttons (and thereby crashing pretty much everything if it lasts over half a second)... The only thing that makes it stop is throwing your hands away from that little sucker - trying to get a hold of the mouse by moving the joystick only makes the problem continue on and on.

Typing dmesg gives me this little message at the bottom:

psmouse.c: Mouse at isa0060/serio4/input0 lost synchronization, throwing 1 bytes away.

(the amount of bytes it throws away is dependant on the time the spasm last (which means it is really just up to my reaction time since I stops when I remove my finger from the mouse).

This only happens with the red thingy (what is its real name anyway?), and it didn't happen back when I was still running Windows.

Thanks in advance

Oh yeah and sorry if my english is bad - correct me

---

### Post by N6546R on 2005-10-28
I've had three different models of Thinkpads under as many operating systems that would exhibit occasional mouse drift, although thankfully none of them ever started clicking on things. Usually it drifts diagonally for an inch or so and then stops. 

I've always assumed it was a hardware problem.

BTW you probably don't want to know what we call that little button here in the office...

Perry

---

### Post by anderss on 2005-10-28
Well it's not drifting - that I experience to, but that isn't nearly as anoying (and doesn't generate error message in dmesg) as when it freaks out. It get's totally wacky and jumps around the entire screen! 
Oh and yeah I think I can guess what you would call it then - I've thought about calling it that, but well.. Guess my teachers (and the girls in my class not the least) would get pretty upset if I walked around calling it that

---

### Post by mike_d on 2006-06-09
this is a bump to this old thread.  i have the same issue on a thinkpad.  when using the track point the mouse will randomly freakout and move over the screen and click.  the only way to get it to settle down it to quit touching it.  has anyone found a solution yet?

---

