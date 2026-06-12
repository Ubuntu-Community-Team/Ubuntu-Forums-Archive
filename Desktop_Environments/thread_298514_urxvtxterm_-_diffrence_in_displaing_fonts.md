---
title: "urxvt/xterm - diffrence in displaing fonts"
date: 2006-11-12
forum: Desktop Environments
---

### Post by vermaden on 2006-11-12
Here is this strange diffrence: [http://toya.net.pl/~vermaden/gfx/urxvt-vs-xterm.png](http://toya.net.pl/~vermaden/gfx/urxvt-vs-xterm.png) 

font sections for urxvt/xterm in **~/.Xdefaults**:
```
xterm*faceName:         monofur 
xterm*faceSize:         10 

urxvt.font:             xft:monofur:size=10

```

Of course I would like to make **urxvt** to display fonts like **xterm**. 

Any hints?

---

### Post by abbeychase on 2006-11-13
try:
[http://www.chimeric.de/openuniverse/tatooine/xdefaults](http://www.chimeric.de/openuniverse/tatooine/xdefaults)

or, one could even use google (like i did).  it's your friend.

---

### Post by vermaden on 2006-11-13
Well the problem is that even when urxvt and xterm has the same font specified, they display them in diffrent ways.

I want to make urxvt to diplay the same font the way that xterm does.

Like on the screen from the link.

---

### Post by kerry_s on 2006-11-13
Well, looking at the man page, it looks like urxvt uses fonts a different way then xterm-> [http://www.die.net/doc/linux/man/man1/urxvt.1.html](http://www.die.net/doc/linux/man/man1/urxvt.1.html)

sorry, i can't help more i use the way smaller xvt termnial.

---

### Post by streeto on 2006-11-13
Here I use this:

XTerm.*.background: black
XTerm.*.foreground: white
XTerm.*.saveLines: 1000
XTerm.*.font: 6x13
XTerm.*.scrollBar: False

Rxvt.*.background: black
Rxvt.*.foreground: white
Rxvt.*.saveLines: 1000
Rxvt.*.font: 6x13
Rxvt.*.scrollBar: False

Sure, I use no fancy fonts, but xterm and urxvt look exactly the same. It's a shame urxvt does not accept the XTerm resource class, like rxvt.

---

### Post by bobstatesman on 2006-11-13
From the screenshot you posted, it looks like your xterm is using a lighter background color than urxvt.  It also looks like you're using anti-aliased fonts.

Anti-aliasing smoothens the text by blending the edges of the characters into the background color, so perhaps the reason urxvt is displaying fonts differently from xterm is because they are using different background colors.  Try changing the background color and see if it fixes your problem.

---

### Post by vermaden on 2006-11-13
The problem is not background color of terminal, I set background of xterm and urxvt diffrent to easier identify them.

Antyaliasing is enabled both for urxvt and xterm.

The problem is that xterm letter spacing is smaller then urxvt.

I would want to make urxvt to display fonts tighter like xterm does.

---

