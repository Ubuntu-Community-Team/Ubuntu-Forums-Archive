---
title: "fluxbox and gnome terminal -storing settings problem"
date: 2009-07-30
forum: Desktop Environments
---

### Post by grzeslaw on 2009-07-30
Hello,

I've Ubuntu 9.04 and fluxbiox 1.1.1.1
I would like to store the position, size, and desktop of gnome-terminal, but when I mark all this settings it didn't work. For example for firefox and thunderbird it's works fine.

What can it be? Maby the problem is that is a generic gnome software?

Regards

---

### Post by kerry_s on 2009-07-30
thats because gnome-terminal doesn't remember that kind of stuff, you'll have to use the command line options. read "man gnome-terminal"

example: **gnome-terminal --geometry 100x40+0+0**

---

### Post by grzeslaw on 2009-08-03
Mmh ... but look, in KDE, I could save the window properities without any specific gnome-terminal options. Also I have the second laptop in my work. where fluxbox store window setting and I do not need any specific options to lunch it. Both systems are ubuntu, so I don't know where could be the problem about.

---

### Post by flux_user on 2009-08-21
> **grzeslaw said:**
> Mmh ... but look, in KDE, I could save the window properities without any specific gnome-terminal options. Also I have the second laptop in my work. where fluxbox store window setting and I do not need any specific options to lunch it. Both systems are ubuntu, so I don't know where could be the problem about.

With respect to Fluxbox and storing window settings; that is the functionality of Fluxbox) not the actual tool.  How do you do it in Gnome?  I don't know..  I use fluxbox.   :-)

---

### Post by grzeslaw on 2009-08-26
Yeah, I use flux too. Sorry, but what I wrote last post was wrong. all my fluxbox machines didn't store the gnome-terminal settings.

When I was using gnome, to store the window geometry settings I use devilspie, but it also didn't store the gnome-terminal geometry settings ;-) 

Now I set-up the command as kerry_s told, and start the command with -geometry argument.

---

