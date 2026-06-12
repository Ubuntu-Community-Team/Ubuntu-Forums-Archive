---
title: "Xgl &amp; Beryl annoyances"
date: 2007-02-14
forum: Desktop Environments
---

### Post by jtapper on 2007-02-14
This thread lists the problems and annoyances I have been encountering with my new Beryl installation. To be complete I have included every relating issues because one thing leads to another..

[LIST][*]No possibility for multiple users with Xgl[*]Emerald themes won't change without reloading window decorator[*]Random non-working controls[*]'Taskbar' panel doesn't update in 'Cube'view[*]XMMS cannot be  moved to other side of the 'Cube'[*]nothing but gray screen + arrow cursor when logout.  Ctrl-alt-backspace takes me to gdm again.

[*]xserver hangs with: Fatal server error: Caught signal 11.  Server aborting when trying to use Gnome (other user has no problem)
[*]Slow compared to Gnome+Metacity

[/LIST]

What comes to problems with my setup.. fglrx was working just fine with dapper, but when upgraded to Edgy my graphics was either Mesa crap or terribly slow with fglrx (because of composite disabled I presume). However the direct rendering is on. With xgl glxgears show much better performance (Yeah I know, it is no good benchmarking proggy) but no direct rendering, which is normal I suppose.

Ok. that's about it. My Beryl experience is almost 2,5 hours long so I suppose this list will grow and on the other hand I hope these issues get fixed with time.

Solved issues: 
[LIST]
[*]Lost Alt-Gr functionality[/LIST]

---

### Post by jtapper on 2007-02-14
One down..
Alt-Gr functionality issue solved with the help of ubuntuforums.org - naturally.

Solution: 
xmodmap -e "keycode 22 = BackSpace"
xmodmap -e "keycode 113 = Mode_switch"

---

### Post by jtapper on 2007-02-15
Well, no eye candy for me anymore. Lack of multi-user support and hanging Gnome sessions made my fine Ubuntu useless. Let's try this one later.. much later.

---

### Post by simonn on 2007-02-18
> Lack of multi-user support

Not sure if this will work for gnome-screensaver as I am using Xubuntu which uses xscreensaver, but in Beryl Settings Manager -> General Options, Main tab, make sure "Sync To VBlank" is **not** checked.

I can now swap between multiple gdm sessions using gdmflexiserver with no wuzzas.

EDIT: Whoops! Noticed this is for XGL.... I'm using Beryl on top of the latest nvidia drivers. Still... might help?

---

### Post by jtapper on 2007-02-18
Thanks for the tip. I'll check it out.

---

### Post by NIT006.5 on 2007-06-30
> **simonn said:**
> Not sure if this will work for gnome-screensaver as I am using Xubuntu which uses xscreensaver, but in Beryl Settings Manager -> General Options, Main tab, make sure "Sync To VBlank" is **not** checked.


You're a genius! This worked for me on Feisty. Can now switch between user accounts with no probs, instead of getting the Great White Screen of Death I had before. Thanks :D

---

