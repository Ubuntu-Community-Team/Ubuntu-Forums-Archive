---
title: "KDE keeps restoring session that caused system freeze -- can't use Kubuntu"
date: 2008-11-21
forum: Desktop Environments
---

### Post by utkjamie on 2008-11-21
I am using the ATI open source driver as recommended by Ubuntu and have a script that changes the video resolution for tv-out, switches to tv-out mode, etc. After upgrading to Intrepid, switching to tv-out mode causes the computer to freeze up. TV-out worked fine prior to upgrading to Intrepid and there appears to be an xrandr bug that causes lockups so it may be the problem if that bug made it into Intrepid.

The problem I have now is that switching to tv-out mode caused the screen to switch to a lower resolution and then freeze up the system. I had no choice but to kill the power. When I log back in, the screen resolution goes into low-resolution and freezes up again. I assume this is KDE restoring the previous session, but I don't know for sure. I've tried a few times but KDE keeps freezing up after logging me in. I tried logging in using fail-safe mode but that fails by just going back to the login prompt without explanation.

I'm having to boot into WinXP just to post this. If anyone can tell me how to get back into KDE, I'd be very appreciative.

As for the ATI drivers, people keep saying that the ATI binary drivers are the way to go. The problem is that the installation of those drivers is prevented by a segmentation fault. So we ATI users are sort of in a bind when it comes to using Intrepid.

---

### Post by jacksaff on 2008-11-22
Have you tried booting safe mode?

---

### Post by utkjamie on 2008-11-22
> **jacksaff said:**
> Have you tried booting safe mode?

I'm not sure what you mean by safe mode? I've tried logging into fail-safe mode from the KDE4 login box but that just takes me right back to a login prompt without explanation. 

Logging into recovery mode (command line) is possible but that isn't the problem. The problem is that KDE4 keeps restoring the previous session -- the session that locks up the computer. It's a video-related problem.

I think I can resolve the problem by disabling KDE's session restore but I need to be able to do that from the command line since logging into KDE causes the lockup before I can do anything. I don't know how to do it. I found instructions that suggested removing the ~/.kde/config/ksmserverrc file but I think that applies to KDE3. When I remove the file I can't get past the login prompt. Restoring the file allows me to log in but then I get right back to the lockup problem again.

---

### Post by utkjamie on 2008-11-22
I ended up moving ~/.kde/share/config/ksmserverrc and ~/.kde/share/config/session/* out of the .kde directory while in recovery mode and rebooting. That got me back in with a "clean" session. Not sure if that was the best possible fix but it's the best I could come up with.

---

