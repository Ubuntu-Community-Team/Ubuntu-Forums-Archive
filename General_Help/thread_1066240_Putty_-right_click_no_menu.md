---
title: "Putty -right click no menu"
date: 2009-02-10
forum: General Help
---

### Post by likebikes on 2009-02-10
i am using ubuntu 8.04 with putty to an SSH server. when i fire putty up and log into my server i get a grey line when i right click the mouse button,no menu so i can paste. shift -ctrl-v dosen't work either.
all other apps work fine with copy/paste this way

---

### Post by TTFN on 2009-02-10
I haven't gotten around yet to installing PuTTY on my Kubuntu, so I'm speaking from my experience with PuTTY on Windows...

You do not get a menu when you right-click.  In order to copy/paste, you hightlight what you are wanting to copy as you normally would with the left mouse button.  In order to paste, you simple click the right couse button.  As soon has you hit the right button PuTTY should paste it right into the terminal.

I hope this helps.  If it does act differently in Linux, I hope someone will correct me.

---

### Post by TTFN on 2009-02-11
I want to correct myself.

This is from PuTTY's documentation ([http://the.earth.li/~sgtatham/putty/0.60/puttydoc.txt](http://the.earth.li/~sgtatham/putty/0.60/puttydoc.txt))

> PuTTY's copy and paste mechanism is by default modelled on the Unix `xterm' application. The X Window System uses a three-button mouse, and the convention is that the left button selects, the right button extends an existing selection, and the middle button pastes.


---

### Post by geirha on 2009-02-11
Any particular reason why you don't just use openssh's client? It is installed by default, just open a terminal and type ```
ssh *user*@*host*
``` You'll be able to use the terminal's copy/paste features.

---

### Post by likebikes on 2009-02-13
> **geirha said:**
> Any particular reason why you don't just use openssh's client? It is installed by default, just open a terminal and type ```
ssh *user*@*host*
``` You'll be able to use the terminal's copy/paste features.

Geirha - wow thanks i can now copy and paste!! i think it was a display issue when i run putty on this machine.

you have helped this Newbie alot.

---

