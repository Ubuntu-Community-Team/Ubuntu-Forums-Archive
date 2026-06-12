---
title: "Comparison of terminal emulators"
date: 2008-06-09
forum: Desktop Environments
---

### Post by Inxsible on 2008-06-09
Could someone tell me what are the differences, if any, in the terminal emulators like 
1) rxvt
2) rxvt-unicode
3) mrxvt
4) eterm
5) aterm
6) xterm
7) xfce4-terminal

Why would you prefer one over the other? is one lighter than the other...more options in terms of transparency...some other features....etc

---

### Post by wootah on 2008-06-09
What's the one that GNOME uses?

EDIT: Rofl. It's gnome-terminal. I did a little digging--gnome-terminal is very similar to xterm (shares many of the same features) and provides colour support, mouse events, etc.

---

### Post by Nythain on 2008-06-09
rxvt-unicode here...
any of the rxvt's are cool and almost the same, mrxvt is multi rxvt, its basically rxvt with tabs

Eterm is slick as far as what it can do, Aterm is about the same really...

and Xterm is great except it doesnt support pseudo transparency

---

### Post by wootah on 2008-06-09
> **Inxsible said:**
> Could someone tell me what are the differences, if any, in the terminal emulators like 
1) rxvt
2) rxvt-unicode
3) mrxvt
4) eterm
5) aterm
6) xterm
7) xfce4-terminal

Why would you prefer one over the other? is one lighter than the other...more options in terms of transparency...some other features....etc

Ok, I got curious (:)):

**aterm**:
Also know as the AfterStep Terminal. It is an X based terminal emulator based off of the rxvt code and was forked in '99. It provides basic X style emulator features (colouring) along with pseudo transparency. It works best with the [After Step Window Manager]("http://www.afterstep.org/")  

**eterm**:
Another terminal emulator based on X. This one was designed around use with the Enlightenment Window Manager (hence 'e'term). This was also forked from the rxvt code base; but this time, development started in '98. Transparency and text colouring along with scrollbars and menus are included.

**Terminal (aka xfce4-terminal)**:
Built to replace xterm, but this terminal emulator was developed with use of xfce in mind. It supports true transparency and it was also designed to take full advantage of the composition effects the xfce provides. Menus, scrollbars, colouring and tabbing are included.

**xterm**:
The first terminal emulator (afaik). It was designed as a terminal emulator for the X Window System which allowed many different invocations of xterm to run on the same display (much like screen multiplexing that *screen* provides). This is basically the old school terminal emulator. Later it actually became XFree86.

**rxvt**:
Yate (Yet Another Terminal Emulator) for X, but this one was designed to replace xterm. It was originally designed to be a lighter version of xterm and it removed some features that were not often used. This terminal emulator emulates VT102 (which is what most of the new terminals emulate) instead of the VT220 (which is what xterm emulated).

**urxvt** (rxvt-unicode):
This is a fork from rxvt to provide extended character support (internationalization) for rxvt but still maintain a lean code base and fast execution.

**mrxvt**:
A big upgrade from rxvt. This provides multiple tabs and true transparency as well as a lack of dependency on a desktop environment (KDE, GNOME, etc). This version does not have unicode support like urxvt.


Alright. From this information I would say it would be safe to stick to a terminal that is best supported in your desktop environment (gnome, kde, xfce). This will probably get you the best operation along with a terminal that best suits your environment. mrxvt would probably be the next best replacement for a standard terminal emulator, but I don't really it's absolutely necessary to change it. It is isn't broke and already works fine, just leave it be :)

Hope that answers your questions. :popcorn:

EDIT: Obviously if you need unicode support, you will have to use a unicode based terminal emulator :)

---

### Post by Inxsible on 2008-06-09
Thanks for the great info wootah.

Well, I wasn't looking to change the default terminal...just that I build my own systems. I always install the core and then install whatever DE/WM I feel like at that time. I mostly tend to go with light weight WMs like Fluxbox, Openbox and Enlightenment E17. I keep Xfce only on one of my machines and that too has been built up on Debian business iso + Xfce4.

Anyway, since I always build systems from the ground up, I wanted to know which one would be a good terminal emulator. I still use xfce4-terminal in my xfce install. 

But I guess I will be going with mrxvt on my fluxbox and enlightenment.

Thanks.

---

### Post by wootah on 2008-06-09
> **Inxsible said:**
> Thanks for the great info wootah.

Well, I wasn't looking to change the default terminal...just that I build my own systems. I always install the core and then install whatever DE/WM I feel like at that time. I mostly tend to go with light weight WMs like Fluxbox, Openbox and Enlightenment E17. I keep Xfce only on one of my machines and that too has been built up on Debian business iso + Xfce4.

Anyway, since I always build systems from the ground up, I wanted to know which one would be a good terminal emulator. I still use xfce4-terminal in my xfce install. 

But I guess I will be going with mrxvt on my fluxbox and enlightenment.

Thanks.

Np! Good luck on your build-up :popcorn:

---

### Post by urukrama on 2008-06-09
I use xfce4-terminal, because it follows my Gtk theme, is easy to configure in looks (colours, transparency, etc.), has configurable shortcuts, has tabs and isn't too heavy.

Btw, you missed a few terminals: gnome-terminal, Sakura, Terminator, tilda, guake, yakuake, Konsole, and probably a few more :-)

---

### Post by Inxsible on 2008-06-09
> **urukrama said:**
> I use xfce4-terminal, because it follows my Gtk theme, is easy to configure in looks (colours, transparency, etc.), has configurable shortcuts, has tabs and isn't too heavy.

Btw, you missed a few terminals: gnome-terminal, Sakura, Terminator, tilda, guake, yakuake, Konsole, and probably a few more :-)I knew about all of 'em except Terminator. 

I didn't include gnome-terminal/guake  and Konsole/yakuake because I thought they would probably bring in Gnome and KDE dependencies respectively.

tilda requires compositor to enable the transparency and such..so I thought I'd keep away from it. and I am not sure how heavy/light Terminator is.

---

### Post by Nythain on 2008-06-10
terminator is nothing more than an enhancement to gnome-terminal... a good one ill give it that, but i dont know if it will even run without gnome-terminal

---

### Post by Chokkan on 2008-06-10
So how easy is it to change one's terminal emulator?
I'm off to find out what's so great about Terminator.

---

### Post by urukrama on 2008-06-10
> **Nythain said:**
> terminator is nothing more than an enhancement to gnome-terminal... a good one ill give it that, but i dont know if it will even run without gnome-terminal

The [latest version]("http://nvalcarcel.aureal.com.pe/?p=192") doesn't need gnome-terminal. From the announcement:

> Terminatorrc: Don&#8217;t like gnome environments? Now you don&#8217;t depend on gnome-terminal to configure your terminator, you can use ~/.terminatorrc to tune your terminal as you want it to be

---

### Post by phoony on 2009-03-27
First of all I would like to apologise for digging up old threads.  But I would like to know is there any other terminal emulator that supports RS232 connection through a USB to serial cable, other than Cutecom ?

---

