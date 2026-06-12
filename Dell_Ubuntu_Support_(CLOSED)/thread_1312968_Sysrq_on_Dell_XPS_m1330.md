---
title: "Sysrq on Dell XPS m1330"
date: 2009-11-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by x C0MMAND0 x on 2009-11-03
Okay, I am tired of getting Kernel Panics (all the lights caps lock/num lock etc keep flashing) and the system is TOTALLY unresponsive.

Supposedly, there is supposed to be a way to use the SYSRQ button to recover or reboot from this error.  It is done by holding "Fn-Prnt Scrn" and then pressing some magic keys.

1. How do I get this to work/ be enabled

2. Do I just hold "Fn-Prnt Scrn" and then hit the keys?

3. What are the different key combinations to use?

4. Has anybody gotten this to work?

---

### Post by mdmarmer on 2009-11-03
Press <Alt> <Sys Rq> at the same time (in your case <Alt> <Fn> <PrtScr> ) and hold down those keys while pressing 
R S E I U B in sequence, waiting a second or two between key presses. See here  [http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

Mike

---

### Post by x C0MMAND0 x on 2009-11-03
Okay, first I had to change my keyboard shortcuts to that prnt does not take screenshots because I had about 100 of them pop up over and over.

Second, I made sure that /etc/sysctl.conf had kernel.sysrq = 1.

Third, I tried it and nothing happened.  Should it only do something if I am in a kernel panic?  Shouldn't it do something either way?

Last, how come I need to hold ALT?  Shouldn't it just be "Fn + Prnt Scrn"?

Thanks for helping.  Hopefully I'll get this figured out soon...

---

### Post by x C0MMAND0 x on 2009-11-04
This is pretty urgent so I'm going to bump it...

---

### Post by x C0MMAND0 x on 2009-11-19
Bump

---

### Post by teward on 2009-11-19
you keep bumping, and the admins shall bring doom upon you.

ATTN: Better Techs:  HELP HIM

---

### Post by x C0MMAND0 x on 2009-11-19
2 bumps in 2 weeks?  Hardly anything compared to many threads.  Did you have any useful information regarding sysrq?  If so, please share.

---

### Post by seeker5528 on 2009-11-19
If the color coding on the keyboard indicates you have to hit 'Fn' to get the 'SysRQ' function you do:

'Fn'+'SysRq'+'some other key'

Othwerwise (more commonly) it should be:

'Alt'+'SysRq'+'some other key'

Either the 'Alt' key or the 'Fn' key, not both, at least based on the keyboards I have to look at.

It should work any time, more or less, but I wouldn't expect it to do anything for you after you've had a kernel panic.

Later, Seeker

---

