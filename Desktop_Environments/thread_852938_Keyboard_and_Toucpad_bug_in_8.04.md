---
title: "Keyboard and Toucpad bug in 8.04"
date: 2008-07-08
forum: Desktop Environments
---

### Post by brujoand on 2008-07-08
Hi, 
I have a few months old 8.04 install on a MSI laptop, standard 32-bit core duo.
Everything has been great, with, 7.10, 7,04 and 6.10.
But now something weird is going on..

The first thing i noticed, from when i install 8.04, is that if I'm viewing say a webpage in firefox, and use the down arrow key to scroll down. If i press it for more then a second, it will not stop scrolling down until i press some button on the keyboard. This would happen, in the Terminal, in OO and basically everywhere. Anyways it's not a major bug.. until now

Whenever this happens, now unlike before, my mousepointer will continue to go in the direction of which I scrolled. And it will not stop until X is restarted.. It renders my laptop pretty much useless.

I'm at work right now, and I need to complete a Python project by this week so its kind of urgent. Any help will do, comments, hints, advice?

Thank you

Anders

---

### Post by brujoand on 2008-07-08
I'm wondering if the bug kan have something to do with the key not being recogniced. This is from my syslog:

> 
Jul  8 09:05:02 tindheim kernel: [  888.714890] atkbd.c: Unknown key released (translated set 2, code 0xe0 on isa0060/serio0).
Jul  8 09:05:02 tindheim kernel: [  888.714901] atkbd.c: Use 'setkeycodes e060 <keycode>' to make it known.


Does this help?

---

### Post by brujoand on 2008-07-08
Ok, I really need some help here.. Basically it seems like I just need to set the keycodes.. how do I know what keycode to set for the down pointer?

---

### Post by brujoand on 2008-07-08
F*** it... ill do a fresh install

---

