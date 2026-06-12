---
title: "Cannot switch windows in Gnome Shell or Unity"
date: 2012-03-09
forum: Desktop Environments
---

### Post by blurp on 2012-03-09
I'm using 11.10 with the latest update. After using an application in Gnome Shell for a while, I'm unable to switch to other windows or application: mouse-clicks outside the window do not respond, alt-tab or alt-` does not work (possibly other desktop-shortcuts too), and the hot-spot on the top-left corner does not work.

I mainly face this problem while in Firefox or in Gnome-terminal (tab-switching still works) but that could be because I'm using them most of the time. I should be able to get back to the original working state by quiting the current application but it's very annoying.

Initially I had the same problem in Unity desktop and that's why I switched to see if that's the issue. The same problem still persist.

I'm using restricted display drivers and the Graphic card is one of the older Nvidia GTS, maybe 8600. But I can't find out now because I can't switch windows...

Any suggestion what might be the solution?

---

### Post by brel on 2012-03-24
I'm having the same problem. My mouse continues to work but I can't click on anything. Alt-tab doesn't work, and the top left corner (indeed the whole top bar) doesn't respond to mouse movement. I've turned off all my gnome extensions.

I've nvidia video as well (Nvidia Geforce 7025) so it might be that. What's strange for me is that it just started happening yesterday and I've no recollection of updating the system or of doing anything unusual. All of a sudden the window manager just stopped working.

I suspected a memory problem but memtest didn't find anything wrong. I've tried gnome classic and xfce and I've the same problem in both. Are they all based on compiz?

Clicking with the right mouse button seems to temporarily unblock the situation (??).

It's very strange and very annoying.

---

### Post by brel on 2012-03-24
I've now tried using an older kernel (3.0.15 instead of 3.0.16) and I've tried using a different nvidia driver (I switched to the 'post-update' driver from the 'recommended' driver in gnome additional drivers setup).

Neither change has improved things...

---

### Post by brel on 2012-04-01
Everything's back to normal now. It's a mystery since I didn't really change anything. I had been using a vga switch box to connect my monitor and I took that away because on reboots (which I was doing a lot) I was getting a "Video out of range" message on my monitor instead of the login screen. I don't see how removing the box could have had an impact but maybe it did.

Unfortunately I can't give more info than that.

---

### Post by blurp on 2012-04-04
Thanks brel. I'm still having this problem despite all the updates although none of them have to do with gnome, x11 or unity.

The frequency of occurrence is less though - I'm also not sure why.

---

