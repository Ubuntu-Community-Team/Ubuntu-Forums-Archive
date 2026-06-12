---
title: "geforce8600 GT - compiz fusion"
date: 2007-09-18
forum: Desktop Environments
---

### Post by polemical on 2007-09-18
Well I've run into more than a couple of problems during the installation of my graphic card. For some reason everything worked fine in x64 but in x32 I got api mismatch thingie during the same procedure installing the drivers. But I finally got them to work(as far as I know) using envy.

Now, to my problem, when typing in: compiz --replace I get the following:

Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Warn: SmcOpenConnection failed: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed

(gtk-window-decorator:5966): Wnck-WARNING **: Unhandled action type (nil)
(gtk-window-decorator:5966): Wnck-WARNING **: Unhandled action type (nil)
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (core) - Warn: pixmap 0x2a00630 can't be bound to texture
(gtk-window-decorator:5966): Wnck-WARNING **: Unhandled action type (nil)
(gtk-window-decorator:5966): Wnck-WARNING **: Unhandled action type (nil)
etc...

In the NVIDIA X server settings, OpenGL etc seemes to be installed, and everything is, as far as I know just as it was when I ran it on my x64(not using envy installing the drivers)

How do I solve this?

Ty, Loke Wilhelmsen

---

### Post by ivelasco on 2007-09-18
sorry,but are you sure Compiz ain't running?take a look at 

ps aux at console
or 
System &#8594; Adminstration &#8594; System Monitor &#8594; Processes

and check if compiz.real is listed

or try pressing alt and decrease the opacity of a window with the mousewheel.

Maybe it's a stupid question,but.....

---

### Post by polemical on 2007-09-18
Yes, its running :) If I try to run beryl the system crashes btw, same sort of error though..

---

### Post by saru411 on 2007-09-18
you have both beryl and compiz fusion installed????? um these are 2 different programs and having both installed surely will give you errors. not sure about that but they are very closely related. this is likely to be your issue. 

for those new to liunx...compiz/beryl are alpha software meaning they are not stable

---

