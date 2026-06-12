---
title: "GNOME session problems"
date: 2006-10-21
forum: Desktop Environments
---

### Post by d3v1ant_0n3 on 2006-10-21
I wasn't sure where to put this thread, but this seemed to be the right place...If it's not, mods please move it:) 

Right, so anyway. I'm running Ubuntu 6.10, with Kubuntu-desktop package installed (so basically Kubuntu). I still like to play in GNOME sometimes- I like them both for different reasons. So I decided to log into GNOME today, which I haven't done in a while. I selected 'GNOME' from the session menu, and 'Just for this session'. Log in started, got to the Ubuntu splash screen. And then nothing. No progress icons, nothing. I left it for 15 mins or so, just in case something was hanging the log in. But no. So I CTRL+ALT+backspaced back to the login screen, selected 'failsafe login'. It loads GNOME, with the following error:

"There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Unable to determine the address of the message bus (try 'man dbus-launch' and 'man dbus-daemon' for help)

GNOME will still try to restart the Settings Daemon next time you log in."

Now, what is the problem here? Can anyone help?

I have considered removing and then reinstalling ubuntu-desktop, but I'm not sure if this will screw with my KDE session in any way...

Specs in sig.

Thanks in advance for any help:D

---

### Post by taurus on 2006-10-21
Yeah, try to reinstall Gnome again after you remove it...

```

sudo aptitude update
sudo aptitude remove ubuntu-desktop
sudo aptitude install ubuntu-desktop

```

---

### Post by d3v1ant_0n3 on 2006-10-21
> **taurus said:**
> Yeah, try to reinstall Gnome again after you remove it...

```

sudo aptitude update
sudo aptitude remove ubuntu-desktop
sudo aptitude install ubuntu-desktop

```

No joy, unfortunately. When I reinstalled the ubuntu-desktop package, I noticed it was reinstalling the 2.6.17 headers package too, so I tried booting with the 2.6.17 kernel (thinking it might be an incompatibility problem with 2.6.18), but the same problem occurs.

Am I right in thinking 'sudo aptitude purge ubuntu-desktop' and then 'sudo aptitude install ubuntu-desktop' will remove all present settings in GNOME? 

Basically, at present, I want a fresh gnome desktop, with absolute default settings for startup programs/themes/icon sets, etc if at all possible.

*EDIT* Ok, I've tried purge/install of ubuntu-desktop, and the same with gdm (which took ubuntu-desktop with it due to dependencies), and still nothing. Bah. Although it DID restore KDM to it's defaults, and seems to have added a 'metacity' session. Which does nothing it would seem.  Anyone?

---

### Post by d3v1ant_0n3 on 2006-10-22
*Bump*

Anyone?

Ok, Seem to have solved it...In the bugtracker there was a report from Hoary, suggesting that using KDE theming on GTK apps in KDE messes with the GNOME session. So I disabled KDE theming of GTK stuff. And GNOME starts up again properly. Well, kinda. Beryl doesn't decorate in gnome...Ah well, I'll get there. FIXED!

---

