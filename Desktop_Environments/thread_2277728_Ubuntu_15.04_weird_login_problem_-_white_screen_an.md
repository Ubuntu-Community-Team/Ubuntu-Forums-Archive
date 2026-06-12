---
title: "Ubuntu 15.04 weird login problem - white screen and low resolution"
date: 2015-05-11
forum: Desktop Environments
---

### Post by peter-a on 2015-05-11
Hi all,

I upgraded from 14.04 via 14.10 to 15.04. All is good.

Except a minor problem, but weird.

When Ubuntu has booted, I expect to be presented with the Gnome greeter on top of my chosen wallpaper.

Instead, I see a completely white screen with a large, low resolution cursor in the middle of it.

If I shake the mouse and left click a couple of times, I then see my chosen wallpaper in the correct high resolution, but a title bar and login box in low resolution on top.

I've attached three screenshots taken with my phone. I'm hoping that at least someone will recognise the source of the white login box and point me in a direction to start looking in.

thanks

Peter

---

### Post by dino99 on 2015-05-11
then the 'chosen wallpaper' might have some trouble displaying; go to System Settings to switch to an other one, and see if it help
> sudo journalctl might also show you some warning/error(s) to help you find the reason of that issue

---

### Post by peter-a on 2015-05-11
Erm... thanks, but the wallpaper is the ONLY thing that's at the correct resolution. That's the problem.

If everything was low res then I'd assume a display driver problem. The fact that my wallpaper is correct says it's not a display driver problem, it's a login/greeter problem. But how?

And I am sure that's not the correct login box for 15.04!!

Nothing in the journal that seems relevant:

May 11 09:04:52 peter dbus[865]: [system] Successfully activated service 'org.freedesktop.login1'
May 11 09:04:52 peter systemd-logind[762]: New seat seat0.
May 11 09:04:52 peter systemd[1]: Started Login Service.

---

### Post by olologin on 2015-05-15
Same problem in xubuntu, after upgrading from 14.10 to 15.04

---

### Post by peter-a on 2015-05-27
Well, at least I'm not alone.

The blank white screen doesn't go away with a key press, only with a mouse click.

---

