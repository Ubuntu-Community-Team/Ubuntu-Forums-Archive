---
title: "keyboard doesn't work with games in Dosbox"
date: 2009-06-22
forum: Gaming &amp; Leisure
---

### Post by jaredbuck on 2009-06-22
Hi all, I installed DosBox and the keyboard does not work with any game I try.  I can type in the Dos command line just fine but when I play a game, the keyboard will not respond.  the only key that seems to work is the Escape key.  

I tried using the keyb.com program, that did not work.  

Can anyone give me some help?  I want to use DosBox in Ubuntu because it responds better and works faster than it does in Windoze.

Jared

---

### Post by plinydogg on 2009-06-22
Try this:

Create a dosbox.conf file (assuming you don't have one already) by doing the following:

(1) Start DosBox;
(2) type:

[HTML]config -writeconf dosbox.conf[/HTML]

This will create the dosbox.conf file in your home directory.

(3) Open the dosbox.conf file you just created; and
(4) In the [SDL] section of the file, change the "usecancodes" to FALSE

Good luck!

---

### Post by CharmyBee on 2009-06-22
Or you could also update to DOSBox 0.73 which fixes this issue.

---

### Post by jaredbuck on 2009-06-22
I did, i followed the dosbox 0.73 tutorial elsewhere on here to download all depedencies and compile the software from source.  And now I can use the keyboard, mouse, joystick, whatever I want :-p

---

### Post by tommado on 2009-06-23
Hi ,  
Post your gamer griefs and rants on the **[Griefster]("http://griefster.com").**

---

### Post by Grishka on 2009-06-23
> **jaredbuck said:**
> I did, i followed the dosbox 0.73 tutorial elsewhere on here to download all depedencies and compile the software from source.  And now I can use the keyboard, mouse, joystick, whatever I want :-p

there was no need for that. new DOSBox is bundled with [DBGL](http://members.quicknet.nl/blankendaalr/dbgl/), a fine DOSBox frontend. but they only have a 32-bit version, so I keep 64-bit DOSBox in [ my PPA](https://launchpad.net/~thir/+archive/ppa).

---

