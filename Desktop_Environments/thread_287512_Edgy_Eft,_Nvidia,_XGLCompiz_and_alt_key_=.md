---
title: "Edgy Eft, Nvidia, XGL/Compiz and alt key = ??"
date: 2006-10-28
forum: Desktop Environments
---

### Post by spydirweb on 2006-10-28
I just setup XGL and Compiz on my machine.  I really dig it, except for one VERY annoying problem: if I have a window selected and hit alt compiz is moving the window to the next window, right.  If a window isn't selected it works as expect.  It's annoying because windows keep getting thrown around to multiple desktops and become hard to follow.  I basicly have to revert to not using my alt key.

I ASSUME this is not normal behavior, but I'm not sure how to fix it.  I'm not even sure what exactly it means hitting alt is actually doing...  I've searched and it seems alt has been a problem with compiz but I haven't seen anything similar to my problem.  Anyone seen this or have suggestions?

---

### Post by rdunnam on 2006-10-29
I am having the same issue.
I have nvidia graphics card on a d620
It is a fresh install of 6.10

---

### Post by robstar on 2006-11-01
I'm also seeing this... anyone figure it out yet?

Is there some place where the ALT key is being mapped to move window???

rob

---

### Post by rdunnam on 2006-11-01
Okay, I did find a fix for mine...
I used the [http://ubuntuguide.org/wiki/Ubuntu_Edgy]("http://ubuntuguide.org/wiki/Ubuntu_Edgy") to install beryl and that fixed it.  I do realize that it is technically different, but it accomplished everything I wanted.  And looks nicer, imho.
Anyways, it seems to be a much better application.

Hope it helps... and btw- I did not undo the compiz stuff.

Rick

---

### Post by angstmachine on 2006-11-05
I had the same problem, but didn't need to re-install. just change the keybindings for the 'put' commands in gconf-editor.

go to apps--> compiz--> plugins--> put--> allscreens--> options-->

The problem is with the last option: put_viewport_right_key, but i went ahead and changed them all.

hope that helps!

---

### Post by phinn on 2006-11-12
Thanks angstmachine this fixed the problem for me that was driving me nuts all morning :D

---

### Post by ndroberts77 on 2006-11-19
I have the same problem. On fresh install of 6.10

I successfully installed & configured Nvidia drivers (for GeForce 6200), XGL, & Compiz.  I started all the EyeCandy and all the window animations worked. (shook like jello).  I could rotate the cube by clicking on the desktop selector down by the recycle bin, but as soon as I hit the <Alt> key the current window would be sent 1 desktop to the right.

If there was no window open hitting <Ctrl><Alt><left cklic> or any key combo requiring <Alt>, <Shift>, or <super> would have no effect.

I tried changing the keybindings for the 'put' commands in gconf-editor.
apps--> compiz--> plugins--> put--> allscreens--> options-->
option: put_viewport_right_key, but that did not help.

I then went to Preferences--> Keyboard--> Layouts and changed the Keyboard model from Generic104...  to Dell and **everything** started to work.
(Layout is set as U.S.English and Default is checked)

It was great until I restarted the computer and nothing worked again.  I went back to the Keyboard Preferences--> Layouts and the Keyboard model was still set as Dell.  I changed it to Dell USB Multimedia Keyboard and again everything started working.

Every time I restart the computer I have to change the keyboard model before any key combos work.  I don't think it matters what model I choose.

Any Ideas?

---

### Post by ndroberts77 on 2006-11-20
> **ndroberts77 said:**
> I have the same problem. On fresh install of 6.10

I successfully installed & configured Nvidia drivers (for GeForce 6200), XGL, & Compiz.  I started all the EyeCandy and all the window animations worked. (shook like jello).  I could rotate the cube by clicking on the desktop selector down by the recycle bin, but as soon as I hit the <Alt> key the current window would be sent 1 desktop to the right.

If there was no window open hitting <Ctrl><Alt><left cklic> or any key combo requiring <Alt>, <Shift>, or <super> would have no effect.

I tried changing the keybindings for the 'put' commands in gconf-editor.
apps--> compiz--> plugins--> put--> allscreens--> options-->
option: put_viewport_right_key, but that did not help.

I then went to Preferences--> Keyboard--> Layouts and changed the Keyboard model from Generic104...  to Dell and **everything** started to work.
(Layout is set as U.S.English and Default is checked)

It was great until I restarted the computer and nothing worked again.  I went back to the Keyboard Preferences--> Layouts and the Keyboard model was still set as Dell.  I changed it to Dell USB Multimedia Keyboard and again everything started working.

Every time I restart the computer I have to change the keyboard model before any key combos work.  I don't think it matters what model I choose.

Any Ideas?

Update--  I solved this keyboard model problem by adding the following line to the script that I use to start compiz-
*setxkbmap -model Dell*

The entire script looks like-
[I]#!/bin/bash
gnome-window-decorator &  compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher &
xmodmap /usr/share/xmodmap/xmodmap.us

setxkbmap -model Dell[/I]

This may not be the right way to go about getting combo keys to work with compiz.  Please let me know if there is a better way.

---

