---
title: "TightVNC shows desktop when the &quot;D&quot; key is pressed"
date: 2012-10-24
forum: Desktop Environments
---

### Post by tckotb on 2012-10-24
Whenever I'm using tightvnc to remotely manage my Ubuntu 11.10 box, I am unable to press "D", unless I hold down shift. This is because the server (or possibly the client) is interpreting that as (I'm only guessing) Ctrl+Alt+D, which IIRC is the keyboard shortcut for showing the desktop.

---

### Post by ssam on 2013-07-10
i have seen something like this. I think it happens if I use alt+tab, which triggers the local window manager to switch away from the vnc viewer. then when you click back into the vnc viewer it saw the alt key going down, but not coming back up. tapping alt get it back in sync for me.

---

