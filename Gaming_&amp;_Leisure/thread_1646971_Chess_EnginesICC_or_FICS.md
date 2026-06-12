---
title: "Chess Engines/ICC or FICS"
date: 2010-12-16
forum: Gaming &amp; Leisure
---

### Post by nod3 on 2010-12-16
Does anyone have any experience with creating custom chess engines to use on ICC or FICS? Obviously not for cheating but to play other computers or adventurous players? I have some experience with this sort of thing with windows, but zero with Linux. Any help would be greatly appreciated. Thanks!

---

### Post by Migrus on 2010-12-17
Doesn't fics have a very simple chat interface, so you would basically connect to a socket and send over your moves as a "chat line"?

Haven't played online chess in more years than I want to remember :) but when I did I was using xboard. So you could take a look at the source for xboard (or whatever the cool client today is) and take the communication parts from that.

But if you have done something like that on windows you wouldn't need to ask this question... so I think my answer is probably really off.

---

### Post by DangerOnTheRanger on 2010-12-21
It's the same thing, but with XBoard (Winboard is the Win32 port of XBoard) instead of Winboard.

On the other hand, if you use a Windows-specific library (say, threading) then it's a *little* (okay, very) different. You would have to familiarize yourself with the POSIX API.

---

