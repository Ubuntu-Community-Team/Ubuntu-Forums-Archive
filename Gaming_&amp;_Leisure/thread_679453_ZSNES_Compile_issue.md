---
title: "ZSNES Compile issue"
date: 2008-01-27
forum: Gaming &amp; Leisure
---

### Post by AvengingAngel718 on 2008-01-27
i'm trying to compile ZSnes from source because i cant get snes9x to work with my gamepad and i hate using the keyboard to play :/

anyway, i did my ./configure and it went fine until i got this:

checking if you want the zsnes debugger... yes
checking for initscr in -lcurses... no
checking for initscr in -lncurses... no
checking for initscr in -lpdcurses... no
configure: error: A curses library is required to use the debugger

i really dont need or want the debugger, so i need to know either how to:

A) let it no i dont want the debugger or
B) install the curses library so i can install it

i installed Public Domain Curses from sourcefourge hoping this would fix the problem, but i didnt have any luck with that.

please help?

---

### Post by AvengingAngel718 on 2008-01-27
never mind, i just did an apt-get install

---

