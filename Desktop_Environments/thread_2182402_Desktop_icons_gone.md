---
title: "Desktop icons gone"
date: 2013-10-21
forum: Desktop Environments
---

### Post by jimford on 2013-10-21
I'm running Xubuntu 13.04 ('ringtail'), with the xfce window manager.

After 'upgrading'(!) from 12.10 I'm having lots of problems, the latest of which is that the icons have disappeared from the desktop. They are actually in the Desktop directory, but are just not showing on the desktop.

I'd be grateful for any ideas, please!

Jim

---

### Post by slickymaster on 2013-10-21
Perhaps something is wrong with your session. You could try to delete the **~/.cache/sessions** folder, log out and log in, to see if that solves the problem.

---

### Post by jimford on 2013-10-21
Deleting the ~/.cache/sessions folder didn't make any difference.

I can't log out and then in again - it's another of my problems! What happens is that the desktop environment closes and I get an unresponsive terminal that hangs. I need to shutdown and then restart. I wish I'd never 'upgraded'(!) from 12.10, which was working fine.

Thanks for the reply 'slickymaster'.

Jim

---

### Post by slickymaster on 2013-10-21
Have you tried to look at the **.xsession-errors** file if there is anything there?

One other thing worth checking is your **.Xauthority** file to make sure your user is the its file owner.

---

### Post by apmcd47 on 2013-10-21
> **jimford said:**
> I'm running Xubuntu 13.04 ('ringtail'), with the xfce window manager.

After 'upgrading'(!) from 12.10 I'm having lots of problems, the latest of which is that the icons have disappeared from the desktop. They are actually in the Desktop directory, but are just not showing on the desktop.

I'd be grateful for any ideas, please!

Jim

It's a while since I played with Xubuntu or XFCE, but isn't the default setting to not have desktop icons? Perhaps the settings have to be reconfigured to turn them back on?

Andrew

---

### Post by Yellow Pasque on 2013-10-21
This happens at times in my Raring VM. I just pull up a terminal and run:
```
xfdesktop&
```
And then all is well.

---

### Post by jimford on 2013-10-22
> **Temüjin said:**
> This happens at times in my Raring VM. I just pull up a terminal and run:
```
xfdesktop&
```
And then all is well.

That did it!

Many thanks to all that responded.

Jim

---

### Post by DJonsson2008 on 2014-09-03
I'm finding this more than a little arcane with Xubuntu 14, I'm constantly loosing the desktop icons for no reason that I can trace.

The terminal commands above do not work for me, these though seem to...
# to quit 
xfdesktop -Q 
# to restart
xfdesktop -R

In any case I'm curious if...

1. Has this been reported as a bug?
2. Is there a screen desktop refresh script out there that could be mapped to a function key?

:mad:

---

### Post by DJonsson2008 on 2014-09-22
Try this at your own risk, for my purposes it works.
As well I'm assigning it to F5 to refresh the screen.

FYI: It takes about 90 seconds to refresh.


#!/bin/bash
# Abstract script 1.
pkill -HUP xfdesktop
xfdesktop -S
exit

---

