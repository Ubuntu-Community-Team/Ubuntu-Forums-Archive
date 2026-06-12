---
title: "Conky with AWN DesktopManager"
date: 2009-07-09
forum: Desktop Environments
---

### Post by sdlynx on 2009-07-09
Hello,

I want to run Conky, but if I choose "own_window yes" then I can't change the background with the DesktopManager plugin for AWN.  I also can't right click on the desktop, and there is sometimes a border around the conky stuff, only sometimes.  If I choose "own_window no" then if I click and drag on the screen it messes up the rendering of conky.  Any suggestions?

sdlynx

EDIT: sorry guys it seems when I borrowed some code from someone else's ~/.conkyrc they had spelled override wrong... problem solved.

---

### Post by wojox on 2009-07-09
Have you tried something like this?

own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

---

### Post by sdlynx on 2009-07-09
> **wojox said:**
> Have you tried something like this?

own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

yeah thanks, I accidentally had "own_window_type overide" instead of "own_window_type override" lol

---

