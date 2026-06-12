---
title: "new ubuntu install"
date: 2005-10-14
forum: Desktop Environments
---

### Post by Sh|fty on 2005-10-14
Ok i just got rid of Debian and put Ubuntu on, i must say so far i like it more but there are 2 things i cant sort out.

1. I cant get access to a term in x, i have looked Applications > system tools and its not there, i have looked in Add Apps and it says terminal is installed. But i cant seem to see it any ware. 

2. I have a mx518 mouse can i cant get the scroll button working or the 2 side buttons (MOUSE4 and MOUSE5)

Can anyone help me with these ?

** + Sh|fty**

---

### Post by WW on 2005-10-14
You can start a terminal with Applications->Accessories->Terminal.

I don't know about your second question.

---

### Post by Sh|fty on 2005-10-14
Thanks i had to restart x to see it :s

I still cant seem to get my mouse to work :(

---

### Post by Sh|fty on 2005-10-16
Now my post has been pushed back :(

---

### Post by grsing on 2005-10-16
Not that it's any help, but if you do figure out how to get your mouse working, please post how you did; I'm trying to figure it out myself, without much luck yet.

---

### Post by Aphorism on 2005-10-16
Compare your mouse scroller to these values.  Also, try the wiki, as I believe your question was already answered there...

/etc/X11/xorg.conf
<SNIP>
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
<SNIP>

Hope this helps...

---

