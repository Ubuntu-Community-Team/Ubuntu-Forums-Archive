---
title: "Second Cursor is not triggering a screen refresh"
date: 2012-12-17
forum: Desktop Environments
---

### Post by am6465 on 2012-12-17
I previously posted about controlling two separate cursors in two xsessions. ([http://stackoverflow.com/questions/13714831/controlling-multiple-pointers-with-xlib-or-xinput-in-ubuntu-linux](http://stackoverflow.com/questions/13714831/controlling-multiple-pointers-with-xlib-or-xinput-in-ubuntu-linux))

That solution worked well. However, an odd thing occurs when I control the cursor. Instead of the cursor moving normally and the screen refreshing to adjust, the cursor leaves a trail because the screen doesn't refresh anything EXCEPT the cursor. This only happens when I move the newly created cursor in the second screen. Best I can guess is that when I move the cursor the xsession isn't getting any event notice or something and it never refreshes though I have no idea if that's the issue. I'm sorry I'm a bit vague I'm just having trouble describing the issue. It's like in the old days when the screen would freeze and you would drag the window and it would leave a trail. That's exactly what's happening with the cursor.

Might it have something to do with the fact that it's not in the xorg?

---

### Post by am6465 on 2013-01-05
Hey all, figured I would post the solution. 

It turns out that the reason that this was happening is that I was using gdm. Gdm doesn't have very good support for multiseating systems (multiple users/single computer). Initially, after the above failed, I tried configuring the xorg.conf to create multiple layout each with it's own input devices. This failed, again because of gdm. Once I switch to kdm I was able to set the xorg.conf so that each monitor started with it's own keyboard/mouse set.

---

