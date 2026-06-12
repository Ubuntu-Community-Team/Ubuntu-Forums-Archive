---
title: "Gcalctool strange results"
date: 2005-05-29
forum: Desktop Environments
---

### Post by jhardtone on 2005-05-29
So I was doing some maths problems studying for an exam and started getting some weird results from gcalctool, the GNOME calculator. Basically it comes down to this:

e^1=14

What? Did someone change the value of e? I checked all the settings on the program, but nothing seemed out of place. Just this strange thing. If anyone has any suggestions as to what I should do to get the correct value out of gcalctool, I'll appreciate it.

JHardtone

---

### Post by twisted_steel on 2005-05-29
I guess they are treating e as hex, rather than the constant, and with 0xE = 14, 14^1 = 14 :?

---

### Post by twisted_steel on 2005-05-29
Bug [submitted]("http://bugzilla.gnome.org/show_bug.cgi?id=305859").

---

### Post by jhardtone on 2005-05-30
Hmm it's true, hex E is dec 14. I just couldn't make that connection in my mind, since the constant and 0xE really don't have anything to do with each other, except the obvious... Heh, I guess that's what we get for using the Development version, although this kind of bug is a bit odd. Oh well, at least I have my 'normal' calculator.

JHardtone

---

### Post by twisted_steel on 2005-05-30
Looks like the bug has been [fixed]("http://bugzilla.gnome.org/show_bug.cgi?id=172150") in the next version.  You can use your 'regular' calculator in the meantime :)

---

