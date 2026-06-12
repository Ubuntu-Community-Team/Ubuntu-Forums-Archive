---
title: "CounterStrike Crashes"
date: 2007-05-13
forum: Gaming &amp; Leisure
---

### Post by PricklySponge on 2007-05-13
Hello.

I'm having a problem with counterstrike source. 

When I connect to the server, the game will run for a few seconds ( around 20-30 seconds if i'm lucky) and unexpectedly crash to desktop. How can I fix this?

---

### Post by buttons on 2007-05-14
> **PricklySponge said:**
> Hello.

I'm having a problem with counterstrike source. 

When I connect to the server, the game will run for a few seconds ( around 20-30 seconds if i'm lucky) and unexpectedly crash to desktop. How can I fix this?

Run wine from a terminal to get the error message.  It's not helpful to describe a crash without any messages.

---

### Post by misfitpierce on 2007-05-14
Yes display what terminal window says on crash

---

### Post by CM Xtasy on 2007-05-14
My counter-strike 1.6 freezes randomly while playing a game, leaving my whole laptop unusable unless I reboot.  Is there a fix for this?

---

### Post by Tumpster on 2007-05-23
THis happens to me, any ideaS?

---

### Post by adam0509 on 2007-05-23
I exactly know the problem, because I write lots of things about steam in french's wiki.



These crashes happens cause of sound (yes...), so :

1) In winecfg :

Tick OSS (only)

Tick "Emulate"

use "Basic" "8000Hz" "8 Bit"


2) Run the game, go to "audio", and set all option to low.

3) Verifiy it don't crash anymore

4) Eventually, adjust the audio value to better rates/option

Eventually, desativate ESD if you use GNOME




About the 30-40 fps if you use "fullscreen" mode (an other important thing to know...) :

This happens when you make ALT+TAB, so get all your programs closed, and desativated trayed programs like aMSN or Network System...


Enjoy !

---

### Post by CM Xtasy on 2007-05-25
> **adam0509 said:**
> I exactly know the problem, because I write lots of things about steam in french's wiki.



These crashes happens cause of sound (yes...), so :

1) In winecfg :

Tick OSS (only)

Tick "Emulate"

use "Basic" "8000Hz" "8 Bit"


2) Run the game, go to "audio", and set all option to low.

3) Verifiy it don't crash anymore

4) Eventually, adjust the audio value to better rates/option

Eventually, desativate ESD if you use GNOME




About the 30-40 fps if you use "fullscreen" mode (an other important thing to know...) :

This happens when you make ALT+TAB, so get all your programs closed, and desativated trayed programs like aMSN or Network System...


Enjoy !

The sound thing did not work.  However I do remember playing for a long time with no crash when I was using -nosound.  I'll try it again and see the results.

---

### Post by adam0509 on 2007-05-25
take the last wine *.deb ?

---

### Post by CM Xtasy on 2007-05-26
> **adam0509 said:**
> take the last wine *.deb ?

My wine is the latest wine

and -nosound changed nothing; it still froze everything.

---

### Post by adam0509 on 2007-05-31
Well, I just tested with "Low" in the audio thing (Options=>Audio in HL/CS/NS) and seems to work like a charm !! (While "High" sometimes crashes the computer)


Maybe you should try it, even with -nosound, we never know...



Remember : OSS (only) and case Ticked !!!

---

### Post by macabro22 on 2007-06-03
Hmm.. I am having this problem too. A Google search led me to this discussion in Bugzilla where this one guy observed that switching the emulated  Windows version from XP to 98 would kill the bug. I confirm it works.
This is a very short term solution though. I get a message from Steam warning that windows98 support will soon be interrupted.
=P

---

### Post by ubu-for on 2007-06-04
> **macabro22 said:**
> Hmm.. I am having this problem too. A Google search led me to this discussion in Bugzilla where this one guy observed that switching the emulated  Windows version from XP to 98 would kill the bug. I confirm it works.
This is a very short term solution though. I get a message from Steam warning that windows98 support will soon be interrupted.
=P

Works great!

Thank you very much!

---

### Post by ubu-for on 2007-06-22
> **macabro22 said:**
> This is a very short term solution though. I get a message from Steam warning that windows98 support will soon be interrupted.

You can use Vista since Wine 0.9.38 instead!

---

