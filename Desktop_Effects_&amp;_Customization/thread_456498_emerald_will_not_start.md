---
title: "emerald will not start"
date: 2007-05-27
forum: Desktop Effects &amp; Customization
---

### Post by stickx911 on 2007-05-27
after searching, I found out how to get metacity to display (before I had no title bar).

I tried to just run "emerald" but I get :

stickx911@stickx911-laptop:~$ emerald
emerald: Could not acquire decoration manager selection on screen 0 display ":0.0"

Not sure what that meant, I tried to kill metacity first:
stickx911@stickx911-laptop:~$ killall metacity
metacity: no process killed

so that didn't do anything.

I tried to search around, but most people are just having trouble with nvidia drivers (I've got an intel chip btw). Searching solved some of the problem, but I still can't get emerald window decorator to show.

Thanks in advance if anyone can even point me in the right direction :D

---

### Post by Ateo on 2007-05-27
Just a shot in the dark, but try > $ emerald --replace

---

### Post by iceid on 2007-06-05
Thanks!!!
$ emerald --replace
did the trick!

---

