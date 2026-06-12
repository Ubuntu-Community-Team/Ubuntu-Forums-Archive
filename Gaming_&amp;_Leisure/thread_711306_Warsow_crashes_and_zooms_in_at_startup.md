---
title: "Warsow crashes and zooms in at startup"
date: 2008-02-29
forum: Gaming &amp; Leisure
---

### Post by coreyon on 2008-02-29
Hey guys, as the title says, Warsow will crash and the desktop will zoom in every time I try to play the game, by zoom in, I mean the desktop keeps it's resolution, but the screen is zoomed and only shows a part of the screen.

glxinfo | grep -i direct gives me this

corey@corey-desktop:~$ glxinfo | grep -i direct
direct rendering: Yes

I've noticed that it only says direct rendering, I remember it used to show something about opengl when I put that command, I dunno if that's related.


Graphics card: Geforce 8600 GT
Ubuntu: 7.10 Gusty

---

### Post by Blue Thunder on 2008-06-24
I've got the exact same problem...except I'm using Linux Mint :P
It crashes as soon as I click to start it. Might try a reinstall.

Oh and I also got "direct rendering: Yes".

ATI FireGL V5200
Linux Mint Elyssa
Warsow version 0.32-1/0.32dfsg-1

---

### Post by eragon100 on 2008-06-24
Have any of you got compiz running? disable it and try again.

---

### Post by Blue Thunder on 2008-06-24
I believe I do have compiz running. Not entirely sure how to disable it, although I did select "none" for desktop effects and de-selected all effects as well, just to make sure. How do you disable it in Ubuntu? - I could probably use it as a guideline :D

I then deleted the apt archive cache and redownloaded/reinstalled Warsow. Still no joy, same problem as above.

EDIT: Maybe I should update Warsow to the latest version (0.42)?

---

### Post by Blue Thunder on 2008-06-30
Decided to update my ATI drivers (apparently they've now got better support for the FireGL's) and also downloaded version 0.42 of Warsow. However it failed to run and had the exact same problems as above. So I took the same package and tried it on Windows XP - funnily enough it runs perfectly...

Regarding the "zooming in" issue, I just finished playing Alien Arena and when I exited it, it closed and left me with a zoomed in desktop. So the problem must be just a side effect of Warsow crashing and not being able to reset the desktop's "resolution". As for why Warsow is crashing, I've got no idea... say, anyone know where/how to get Warsow to output logs?

---

