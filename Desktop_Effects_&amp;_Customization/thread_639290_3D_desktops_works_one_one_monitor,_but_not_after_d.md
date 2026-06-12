---
title: "3D desktops works one one monitor, but not after dual monitors are selected"
date: 2007-12-13
forum: Desktop Effects &amp; Customization
---

### Post by iq62ut36 on 2007-12-13
I have a NVidia 7600 with the propriaty drivers. When I select the desktop candy with only one monitor (Samsung 203B) selected, it works but if I select the dual screen (a second Samsung 203B), then the desktop effects fail. Any suggestions?

---

### Post by drummingpariah on 2007-12-13
> **iq62ut36 said:**
> I have a NVidia 7600 with the propriaty drivers. When I select the desktop candy with only one monitor (Samsung 203B) selected, it works but if I select the dual screen (a second Samsung 203B), then the desktop effects fail. Any suggestions?

I'm using a 7600go with the same issue. Try using xinerama, not separate x sessions.

---

### Post by iq62ut36 on 2007-12-13
> **drummingpariah said:**
> I'm using a 7600go with the same issue. Try using xinerama, not separate x sessions.

Thanks for your quick answer. Is the 7600Go a mobile video card?

Is this a 'should work' or a 'please try'?

---

### Post by drummingpariah on 2007-12-13
> **iq62ut36 said:**
> Thanks for your quick answer. Is the 7600Go a mobile video card?

Is this a 'should work' or a 'please try'?

The go is a mobile card (burly for being mobile, but still clocked significantly lower than your desktop card).  This is a 'should work' as in it worked for me.  Which build of drivers are you using, and what version of compiz?

---

### Post by iq62ut36 on 2007-12-14
It was Xinerama but seperate X windows. Solved it using sudo nvidia-settings and changing it to twinview. Thanx for the help.

---

### Post by drummingpariah on 2007-12-14
> **iq62ut36 said:**
> It was Xinerama but seperate X windows. Solved it using sudo nvidia-settings and changing it to twinview. Thanx for the help.

Awesome, I'm glad I could help.  Just so the record is straight (for anyone reading this in the future) you may want to put up exactly what graphics card you're using (type lspci in the terminal, and it'll spit out all sorts of info that your hardware tells ubuntu).

---

