---
title: "installed compiz - do i still need metacity?"
date: 2006-09-10
forum: Desktop Environments
---

### Post by gnudoc on 2006-09-10
Apologies if this question seems as horrendously noobish to you all as it does to me, but i've scratched my head, searched the fora, and ended doing a bit of this ](*,) 

i have recently taken the tentative step of putting xgl and compiz onto a production system, and the users are all very impressed. however, one thing confuses me. grepping metacity in the output of ps aux shows that it's not running - presumably because the compiz --replace command turns it off. yet gnome seems to insist on starting it, and uninstalling metacity makes the gnome startup process stall at the window manager stage.

why do i care? because presumably the bootup would become slightly faster, and running one window manager briefly, only to replace it with another seems a bit, well, quick-and-dirty to me, somehow.

so, is there a nice way to get rid of metacity and point gnome directly at compiz when it looks for a window manager?

thanks!
gnudoc

---

### Post by Snorri on 2006-09-10
I have the same/similar problem. XGl insists on using metacity, and when I try and switch to compiz using the compiz manager, it doesn't switch.

---

### Post by gnudoc on 2006-09-10
> **Snorri said:**
> I have the same/similar problem. XGl insists on using metacity, and when I try and switch to compiz using the compiz manager, it doesn't switch.

there should be a file at /usr/bin/compiz-start if your system is fairly standard (and you have reasonably recent debs). try doing Alt-F2 then typing that (/usr/bin/compiz-start). if this brings up compiz, great.

for this to happen automatically when gnome starts, do system -> preferences -> sessions. click on the startup programs tab, then click Add, and type in that same command (/usr/bin/compiz-start) into the dialog. click ok, then close. that should bring up compiz when gnome starts - assuming you've made the right changes to the config files.

my trouble is that i find this to be a bit messy - having to let metacity load, only to have it replaced by compiz in seconds. it would be much **cleaner** to have compiz loaded in the first place. ;) 

ta,
gnudoc

---

