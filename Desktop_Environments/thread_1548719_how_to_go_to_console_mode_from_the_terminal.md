---
title: "how to go to console mode from the terminal"
date: 2010-08-08
forum: Desktop Environments
---

### Post by Edgar09 on 2010-08-08
Hi Every body! 
Well it's me again :p

I gotta a weird question.....

How can i change the desktop grafic mode to console mode by using the terminal..???

I once saw i buddy of mine do it before

But......

He accidentally formated his computer(He had 4 diff distros)

So i cant get the code

& iam wondering if any of the ubuntu community knows how???

Thank you for your time:o

---

### Post by chopinhauer on 2010-08-08
> **Edgar09 said:**
> 
How can i change the desktop grafic mode to console mode by using the terminal..???


You are looking for a command line program to change to another virtual console? Then [chvt](http://manpages.ubuntu.com/manpages/lucid/en/man1/chvt.1.html) is what you are looking for, otherwise I don't understand your question.

---

### Post by hictio on 2010-08-08
You want to stop the graphical login? And have (temporarily) a CLI only system?

---

### Post by DaithiF on 2010-08-09
Hi,
ctrl-alt-F1 (or F2, F3, etc)
or use chvt as mentioned by chopinhauer
```
chvt 1  (or 2, 3, etc)
```ctrl-alt-F7 or chvt 7 to get back to graphical

---

### Post by Edgar09 on 2010-08-09
> **chopinhauer said:**
> You are looking for a command line program to change to another virtual console? Then [chvt](http://manpages.ubuntu.com/manpages/lucid/en/man1/chvt.1.html) is what you are looking for, otherwise I don't understand your question.

Nope. i want to change the gnome grafic to to black and white just like in console mode...
It's not really console mode cause i can do any normal stuff like use firefox

I hope u can understand:(

---

### Post by Edgar09 on 2010-08-09
> **hictio said:**
> You want to stop the graphical login? And have (temporarily) a CLI only system?

It has nothing to do with login 
In simple words it's just having fun with the terminal i just want to know how to do it

I asked my buddy again but he doesnt remember the code 
O and its temporarily
U can change back by puttung another code in the terminal

Hope u can help:)

---

### Post by Edgar09 on 2010-08-09
> **DaithiF said:**
> Hi,
ctrl-alt-F1 (or F2, F3, etc)
or use chvt as mentioned by chopinhauer
```
chvt 1  (or 2, 3, etc)
```ctrl-alt-F7 or chvt 7 to get back to graphical

It's not that DaithF:popcorn:

---

### Post by Spice Weasel on 2010-08-09
Wouldn't it be easier just to do ctrl alt f1-f7? I suppose you could kill X and disable GDM, but it's much easier and would do the exact same thing to use the ctrl alt function keys.

---

### Post by chopinhauer on 2010-08-09
> **Edgar09 said:**
> Nope. i want to change the gnome grafic to to black and white just like in console mode...


You can change the default foreground and default colour in gnome-terminal preferences. Otherwise you can change the color with [terminal control sequences](http://invisible-island.net/xterm/ctlseqs/ctlseqs.html), like:
```
echo -e '\e[37m\e[40m'
```

---

