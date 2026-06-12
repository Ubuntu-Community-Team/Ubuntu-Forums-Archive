---
title: "PulseAudio Removal: System F***up"
date: 2009-03-16
forum: General Help
---

### Post by change_mode on 2009-03-16
Using Ubuntu 8.04 Hardy.

What I did:

- apt-get remove pulseaudio
- apt-get install esound
- remove 'PulseAudio Session Management' from Sessions -> Startup
- reboot

After rebooting, I tried to open the sound preferences, to see if the pulseaudio entry was gone. It didn't open, but from that moment my GUI became unresponsive, even after a reboot. The bottom bar doesn't even load, the top bar is blank. Can't open anything (posting with Lynx). Compiz still works though, for whatever reason.

**How do I get the rest of the GUI back?!** Would post screenshots, but for obvious reasons I can't.

---

### Post by change_mode on 2009-03-16
*back to page 1*

There's nothing in the logs that would explain this.

edit:

apt-get remove esound
apt-get install pulseaudio

Works again, although not the solution I was looking for.

---

### Post by drummingpariah on 2009-03-16
I would say that PulseAudio was the worst thing to happen to Ubuntu in 8.04.  It never works, forces my mic to full playback volume all the time (nonstop, neverending feedback), and has completely destroyed my skype experience.  I might even say PulseAudio is the worst thing to happen to Ubuntu, period.

As you have now found out, it's extremely difficult to remove all of its grimy fingerprints from your system.  I've been trying to figure out how to go back to an older, simpler sound setup (that works) so if you do manage to get rid of it, let me know how.

---

### Post by akshunj on 2009-05-31
Had a similar experience.  I NEED to remove Pulseaudio.  Is this possible without killing the desktop as I did?

---

### Post by Soul-Sing on 2009-06-01
> **akshunj said:**
> Had a similar experience.  I NEED to remove Pulseaudio.  Is this possible without killing the desktop as I did?

Pulseaudio is part of the (gnome) desktop, you can safely disable it rather then uninstall it.

---

