---
title: "Installation broken with update.. or something xgl-compiz"
date: 2006-06-27
forum: Desktop Environments
---

### Post by ububug on 2006-06-27
Hi,

I've had xgl & compiz running very well over the last couple weeks, however today there were several updates. I downloaded & installed those update.. I later rebooted and when it started up xgl didn't load. After a couple seconds the both menu bars disappear and I'm left with just the desktop, no keyboard shortcuts worked or anything. After that I created a icon for "metacity --replace". That brought the menu bars back, but still no xgl.. When I type "startcompiz in the terminal, the menu bars dissappear, and I get this message

> $ startcompiz
gnome-window-decorator: /home/lee/Applications/mono-1.1.13.8/lib/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
lee@lee-laptop:~$ compiz.real: /home/lee/Applications/mono-1.1.13.8/lib/libpng12.so.0: no version information available (required by compiz.real)
compiz.real: Support for non power of two textures missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :1.0



After that the only thing I can do is type "metacity --replace"

I think what may have caused this is a update to the fglrx driver.. but I'm not sure.

btw: My computer is running extremely slow all the sudden. Also, I have a ati radeon mobility 9600.


](*,)

---

### Post by ububug on 2006-07-02
[QUOTE=ububug]Hi,

I've had xgl & compiz running very well over the last couple weeks, however today there were several updates. I downloaded & installed those update.. I later rebooted and when it started up xgl didn't load. After a couple seconds the both menu bars disappear and I'm left with just the desktop, no keyboard shortcuts worked or anything. After that I created a icon for "metacity --replace". That brought the menu bars back, but still no xgl.. When I type "startcompiz in the terminal, the menu bars dissappear, and I get this message




After that the only thing I can do is type "metacity --replace"

I think what may have caused this is a update to the fglrx driver.. but I'm not sure.

btw: My computer is running extremely slow all the sudden. Also, I have a ati radeon mobility 9600.


](*,)[/QUOTE]


bump?

I think I'm just going to reformat.

---

### Post by lamego on 2006-07-02
XGL/Compz is still very BETA.
If you don't understand it enough to figure out if you are using a 3d hw accelerated driver for your card you shouldn't be using it.

---

