---
title: "GNOME won't start but KDE works! --Possible fix"
date: 2007-04-15
forum: Desktop Environments
---

### Post by panicbyte on 2007-04-15
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/77318](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/77318) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				OK, this basically sucked up my whole day trying to figure out...

Everything was running great before I turned off my laptop. A few hours later I start it up everything seems normal, I get to my login screen type in my username and password... and.....

I get nothing but a "ubuntu brown" background and it just sits there, not even a gnome splash screen, no error messages.... nothing....

so.. here are a few things I tried to fix the problem:

restart the computer (duhh)
tried using KDE instead (i have both KDE and GNOME installed) and KDE worked, but gnome still wouldn't work
I deleted my gnome settings in my home directory.. still won't work
I created a new user and tried to login with gnome... still wouldn't work
I updated all my packages, and reinstalled gnome and other packages... still wouldn't work

after about 2 hours of google searching and other trial and error methods I found this:
[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/77318](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/77318)

but I could ping myself, my loopback device was working....

the problem???

I was experimenting with a new firewall program called "kmyfirewall" (note: your exact problem may differ)

so I opened a virtual terminal as root and typed "/etc/init.d/kmyfirewall stop"

GNOME FINALLY STARTED!!!

this was such a frustrating issue...
I hope this post helps someone

who would have thought that a firewall would prevent gnome from starting?, not to mention GTK based programs in KDE were crashing as well

and as the bug report I found said, there should be an error message mentioning the loopback issue

---

