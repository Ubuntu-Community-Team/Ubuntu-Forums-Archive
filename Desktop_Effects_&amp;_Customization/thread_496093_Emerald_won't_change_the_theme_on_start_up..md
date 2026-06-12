---
title: "Emerald won't change the theme on start up."
date: 2007-07-08
forum: Desktop Effects &amp; Customization
---

### Post by spaceship.rodeo on 2007-07-08
Just like the title says, Emerald won't change my theme when I boot my computer.  Sometimes it's just the regular metacity theme, but other times there just isn't any window borders.  It is being used in conjunction with Compiz Fusion, if that makes any difference.

I can change the theme by opening the terminal and entering ```
compiz --replace -c emerald &
``` and it will change the theme like I needed.  However the terminal will freeze and if I try to close it, the theme will go back to metacity or the borders will go away.  If I hit alt+F2 and type in ```
Emerald --replace
``` while the terminal is still open, I can then close it and the theme stays normal.

If there is any way around it, I would love to know, because it's kind of annoying to have to do this every time I boot my computer.

---

### Post by chuckyp on 2007-07-08
You have to have two sperate commands in your session startup.   One for fusion one for emerald ex:

Name: Compiz
Command: compiz --replace

Name: Emerald
Command: emerald --replace

Just add those two and all will be fine.

---

### Post by spaceship.rodeo on 2007-07-09
Oh, right.

How would I go about doing this?  I'm still pretty new to Linux.

---

### Post by edwin.e.johnson on 2007-07-09
on your task bar click on <SYSTEM>  then scroll to <PREFERENCES>   now click on <SESSIONS>

now just click the new button

it will ask you for a 

"NAME"

and 

"COMMAND"

just use the ones he told you.

---

### Post by spaceship.rodeo on 2007-07-09
Thanks a whole lot, guys.

---

