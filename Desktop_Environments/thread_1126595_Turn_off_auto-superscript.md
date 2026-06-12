---
title: "Turn off auto-superscript"
date: 2009-04-15
forum: Desktop Environments
---

### Post by qrwe on 2009-04-15
Hello,

I've found a bug/feature I would like to have patched/turned off. When writing in gedit (or terminal) and I come to making of square roots (I use octave a lot), it always turn into a superscripted number. For example, when trying to write something like y=x^2, the letter "2" is automatically superscripted.
This is extremely annoying; if it's a feature, the SO smart author could not possibly be a programmer when all coding results in unnecessary text encoding bugs because of this..

Does anyone feel like me and has even found a way to get rid of it?

---

### Post by stderr on 2009-04-15
Hi

I have not encountered this on any of my Ubuntu/Kubuntu installations, and am unable to replicate. You say this occurs in gedit, but also gnome-terminal (very surprising)?? Does this even extend to a basic term such as xterm?

To clarify, the superscripting occurs immediately after typing a caret followed by a number (such as ^5)?

---

### Post by qrwe on 2009-04-15
> **stderr said:**
> Hi
To clarify, the superscripting occurs immediately after typing a caret followed by a number (such as ^5)?

To clarify myself then :-) : It occurs only for ^1, ^2 and ^3 cases, other numbers stay unchanged.
It's strange you haven't seen anything, I've done several basic installations of Ubuntu here and there and all of them comes with this issue.

---

### Post by The average internet guy on 2010-09-30
I'm having this issue too. How can you turn it off? Is it possible to print the "^" immediately each time I hit the key? Usually I have to hit another key to get it to show

---

### Post by mcduck on 2010-09-30
That pretty much be related to keyboard settings, as apps like Gedit and the Gnome-terminal definitely don't have any kind of automatic text correction (it wouldn't even make any sense on a plain text editor and a terminal).

Now that I tried it, it actually seems to work that way on my system as well. Pretty neat, to be honest. This will definitely make my life easier... :)

Anyway, if you don't regularly use special characters you could simply switch to a keyboard layout with no dead keys. That way typing a dead key like "^" would immediately print the character, instead of trying to pair it together with the next typed key.

..or simply press space after the caret before typing the number (you won't actually get a space, it's still a dead key, but since it can't be paired with space to create any special character you just get the caret)

---

