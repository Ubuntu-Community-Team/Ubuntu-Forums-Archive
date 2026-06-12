---
title: "vncviewer shift-click not working"
date: 2009-10-21
forum: Desktop Environments
---

### Post by chaonis on 2009-10-21
using 9.04 desktop, When I try to use vncviewer to connect to a 9.04 server, the shift-click and ctrl-click don't work. 

run xev on the server side and I see the shift/ctrl key got released before the mouse click. However, shift-up/down arrow works. My other machines, including gentoo and winxp, don't exhibit this problem. 

I tried Real vncviewer and xtightvncviewer and both have the problem. 

Any idea? All software are up to day. Had this problem for a year and never bothered me until now, when I need to do some gimp editing.

Please help.

---

### Post by gregcorey@gmail.com on 2010-04-19
No idea how to fix this, but I do have a workaround that allows me to get stuff done. I enable Sticky Keys from the accessibility panel. That seems to allow me to use shift and ctrl - although in a different way than usual.

Greg

---

### Post by thefifthsetpin on 2010-05-18
I've noticed that this problem only seems to apply to what I'll call the "button depressed event."  In programs that wait for the "button released event" you can depress the shift key _after_ depressing the mouse button, and it seems to behave correctly.

The behavior is no different for me with any of {shift, ctrl, alt, meta}.  It also doesn't seem to matter whether I'm using a mouse button or another non-alphanumeric key (generally an arrow key or page up/down).  Interestingly, the alphanumeric keys respect the shift key.  Capitalization and the like must be handled by different logic.

Observed on a 10.04 remote machine viewing a 9.04 desktop, and on a 9.04 remote viewing the same 9.04 desktop.

---

### Post by atlantique on 2010-06-04
I had similar problem using vncviewer in conjunction with x11vnc. Actually my problem was somewhat worse, my "shift" key did not work, forcing me to use the "Caps Lock" key, which is very cumbersome, specially if one uses the "vi" or "vim" editors. To type a colon I needed three keystrokes 1) "Caps Lock" 2) ";"  and 3) "Caps Lock".

Not using the default option "modtweak" for x11vnc has solved the problem for me.

According to the manual page for x11vnc, the default option "-modtweak" automatically tries to  adjust  the  "Shift"  modifiers for differing language keyboards between client and host.   My problem was solved by cancelling the default behavior with "-nomodtweak"

*x11vnc -nomodtweak -display:0*

---

### Post by seattle vic on 2010-06-29
> **atlantique said:**
> I had similar problem using vncviewer in conjunction with x11vnc. Actually my problem was somewhat worse, my "shift" key did not work, forcing me to use the "Caps Lock" key, which is very cumbersome, specially if one uses the "vi" or "vim" editors. To type a colon I needed three keystrokes 1) "Caps Lock" 2) ";"  and 3) "Caps Lock".

Not using the default option "modtweak" for x11vnc has solved the problem for me.

According to the manual page for x11vnc, the default option "-modtweak" automatically tries to  adjust  the  "Shift"  modifiers for differing language keyboards between client and host.   My problem was solved by cancelling the default behavior with "-nomodtweak"

*x11vnc -nomodtweak -display:0*

I've been having this problem for months now, like something changed in the program.  Adding the -nomodtweak did the trick for me.

---

### Post by stolsvik on 2010-07-26
According to [this bug]("https://bugs.launchpad.net/ubuntu/+source/vnc4/+bug/275089"), vinagre and gvncviewer works. I tested the latter, it works.

```
sudo aptitude install gvncviewer
```
:KS

---

### Post by krunge on 2010-07-26
> **seattle vic said:**
> I've been having this problem for months now, like something changed in the program.  Adding the -nomodtweak did the trick for me.

Instead of using "-nomodtweak" do you find using "-xkb" solves it too?

In x11vnc 0.9.11 "-xkb" mode will be on by default.

---

### Post by bctechnzl on 2011-07-04
> **krunge said:**
> Instead of using "-nomodtweak" do you find using "-xkb" solves it too?

In x11vnc 0.9.11 "-xkb" mode will be on by default.

Awesome, thanks for this. I'd been getting the user at the other end to press and hold shift! (duh) but I'd been erroneously blaming xtightvncviewer.

---

