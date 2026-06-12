---
title: "Multimedia keyboard (again)"
date: 2006-08-03
forum: Desktop Environments
---

### Post by DiesIrae on 2006-08-03
Hi there,

I just bought a logitech MX3000 keyboard+mouse set.

Almost everything is working fine: some multimedia keys are being recognised but not all of them.

I spent the whole afternoon googling and trying every How To I cound find without much success.

The main problem is that some of the keys are not being recognised at all, not even by xev. And even I check dmessg, it doesn't tell me anything, where apparently I should see something like:
[FONT="Courier New"]atkbd.c: Unknown key pressed (translated set 2, code 0x9e on isa0060/serio0).
atkbd.c: Use 'setkeycodes e01e <keycode>' to make it known.
[/FONT]
But I don't!

Anyway, if anyone got any idea... 

Thanks! :)

Matt

---

### Post by gborzi on 2006-08-03
I have the same keyboard, or at least a keyboar whose commercial name in Italy is MX3000. I use keytouch [http://keytouch.sourceforge.net/index.html](http://keytouch.sourceforge.net/index.html) to have the multimedia keys working. The keyboard layout is available in the program under the name MX3100.

---

### Post by tsairox on 2007-08-26
I have the MX3000 keyboard and mouse also.  My mouse was recognized with no configuration needed.  How do I get the keyboard connected? 

Thanks,

t

---

### Post by RedSquirrel on 2007-08-27
> **DiesIrae said:**
> The main problem is that some of the keys are not being recognised at all, not even by xev. 

If xev doesn't see those keys, you can forget about using them in Linux.

---

### Post by Hexagrapher666 on 2007-09-29
> **RedSquirrel said:**
> If xev doesn't see those keys, you can forget about using them in Linux.

That is not necessarily true for all hardware/kernel combinations.  Before configuring my HP 6511-S multimedia keyboard, [COLOR="Navy"]**xev**[/COLOR] showed no response at all to certain extra keys, but the [COLOR="Navy"]**dmesg**[/COLOR] ring buffer did show the hex code and the scancode for all of the keys that [COLOR="Navy"]**xev**[/COLOR] missed.

The most comprehensive write-up I have encountered so far regarding [configuring multimedia keyboards in Linux]("http://gentoo-wiki.com/HOWTO_Use_Multimedia_Keys") was found in the Gentoo wiki.

---

