---
title: "Exceedingly odd desktop behavior"
date: 2006-06-17
forum: Desktop Environments
---

### Post by Mihara on 2006-06-17
On a Gnome Ubuntu 6.06 I installed for a friend *(I don't know much Gnome, and I generally use KDE in Gentoo anyway, this guy's new to Linux and isn't good with computers in general, so I wanted to set him up with something easier for a layman to maintain)* some really odd things happened after the last automated system update.

1. Keyboard layouts switch between Cyrillic and English without user intervention or in response to keys that shouldn't cause it.
2. Sometimes Enter key generates some 20-30 keypresses instead of the one it should. This only happens in Gaim.
3. Mouse buttons either refuse to press or get stuck as pressed. Instead of the selected menu item, the neighbouring ones activate.
4. Applications start randomly and the user can't close them afterwards.

All that makes the desktop essentially unusable, while from a remote terminal nothing looks out of place.

After I eliminated the possibility of a rootkit (rkhunter didn't find anything at all suspicious, the only remote logins are me SSHing in to see what's going on, etc) I'm about to blame the most recent update which did something wonky - unless there's a virus in one of the Windows machines on that hub, which can somehow hijack VNC, which I doubt.

1) Where should I look for the problem?
2) Is there a way to see which updates were installed recently and roll them back in the order they were installed in? Is there a way to do this from a remote terminal?

---

### Post by dpm on 2006-06-17
Before uninstalling / rolling back anything, I'd check the hardware. Do not assume that it si working flawlessly.

Is the keyboard ok? Does this happen if he uses another keyboard?

>1) Where should I look for the problem?
My first guess is hardware (keyboard?). Then software.

>2) Is there a way to see which updates were installed recently and roll them back in the order they were installed in? Is there a way to do this from a remote terminal?
Use apt. Read the man page and the apt HOWTO.

Cheers.

---

### Post by raptros-v76 on 2006-06-17
actually, use aptitude. its safer and you'll end up happier

---

### Post by Mihara on 2006-06-17
[QUOTE=desp]Before uninstalling / rolling back anything, I'd check the hardware. Do not assume that it si working flawlessly.[/quote]

Everything works just fine in Windows XP which it dualboots into. :)

[QUOTE=desp]Use apt. Read the man page and the apt HOWTO[/QUOTE]

That was my first guess. However, mans and HOWTO do not seem to say how do I find out what was actually installed in the last update and what came on the CD.

---

### Post by Mihara on 2006-06-18
What, no advice on that at all?...

---

### Post by disturbed1 on 2006-06-18
Open synaptic, click on file, choose history

---

