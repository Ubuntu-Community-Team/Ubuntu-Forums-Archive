---
title: "Computer crashes and dies till restart with some games."
date: 2009-03-29
forum: Gaming &amp; Leisure
---

### Post by MaximB on 2009-03-29
Hello

With some games like "Warzone2100" and "World of goo" my PC crashes at some point and no key is responding, no "ctrl+alt+backspace" no "crtl+alt+F*" not even the sysRq key, and the mouse is standing still as well.

I don't know what is the problem and the only thing I can do is to manually restart the machine (using the button).

Many other 3D games run fine.

I have Radeon 4870HD and I'm using the proprietary ATI drivers.
Quad Core with 4GB RAM, so hardware should not be the issue.

I can't even send an error via command line as I can't even get there (freeze).

I never thought such things could happen on Linux, but sadly I was proven wrong.

How can I find where is the problem ?

P.S
Warzone 2100 works perfectly with my netbook (Asus 1000H) but not with my PC for some reason.

---

### Post by rizzeh on 2009-03-29
send output to text file if it freezes then you'll be able to see the error.
In terminal:
yourcommand > errorlog.txt

After restarting X, look through errorlog.txt

---

