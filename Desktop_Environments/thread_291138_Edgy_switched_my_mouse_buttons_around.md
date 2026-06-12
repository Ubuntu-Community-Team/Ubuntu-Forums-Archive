---
title: "Edgy switched my mouse buttons around"
date: 2006-11-02
forum: Desktop Environments
---

### Post by Kelnoky on 2006-11-02
After updating to edgy eft a few days ago suddenly my middle mouse button and the right mouse button switched their functions. So every time I do a middle click the context menu opens and the right mouse button does everything the middle mouse button did. o.O

Any solutions?

---

### Post by Kelnoky on 2006-11-03
No one got an idea?

---

### Post by Kelnoky on 2006-11-10
Still no one? -.-

---

### Post by Ezel on 2007-05-01
Yepp! This happened to me also today When I went the loooong way from 5.10 to 7.04!
ANYBODY got any hints how to bring normal behavior back?
I've checked what the application "xev" gives for information and it gives:
Left msb = button 1
right msb = button 2
middle msb = button 3
wheel up = button 4
wheel down = button 5

The wheel and left msb works, but when using the computer it has switched the behavior of middle and right msb.
Examples:
If I middleclick a link in Firefox it gives me a menu and if i rightclick the link it opens in a new tab.
If I rightclick on the Ubuntu-desktop nothing happens, but if I middleclick it brings up a menu (Create folder, Create Launcer, Change desktop bakground and such)

There must be a way to change that!! Please help us :-)

---

### Post by Ezel on 2007-05-01
Wow! Solved it myself.

Atleast this worked for me:

I added a row in my /etc/X11/xorg.conf
Under 
[INDENT]*Section "InputDevice" *[/INDENT]
where I have my mouse configured with
[INDENT][I]Identifier	"Configured Mouse"
Driver		"mouse"
.. . . and more
[/I]
[/INDENT]
I added the line
[INDENT]*Option          "ButtonMapping"         "1 3 2 4 5"*[/INDENT]
where I have thrown around the inputs for button 2 and 3.

This works (atleast sofar) for my crappy nonstandard mouse named "Elements SMART6000" which there is no info to be found about on the net. 

Hope this helps someone else!

---

