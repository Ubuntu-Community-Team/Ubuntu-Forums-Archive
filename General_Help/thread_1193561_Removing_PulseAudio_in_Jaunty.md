---
title: "Removing PulseAudio in Jaunty"
date: 2009-06-21
forum: General Help
---

### Post by ShadowWraith on 2009-06-21
Pulseaudio has caused me endless headaches, and I wish to downgrade to esound and alsa. I tried removing the pulseaudio package with synaptic, but it informed me that uninstalling it, would also uninstall ubuntu-desktop, which is something I definitely don't want. Is there any way to remove pulseaudio and revert back to good old stable ALSA?

---

### Post by nmaster on 2009-06-21
[INDENT] I did this at the terminal. Hope it helps.


[LIST]
[*]killall pulseaudio
[*]sudo apt-get remove pulseaudio
[*]sudo apt-get install esound
[*]sudo rm /etc/X11/Xsession.d/70pulseaudio
[*]Reboot system
[/LIST]
 [/INDENT]

---

### Post by nmaster on 2009-06-21
> **neal.m.master said:**
> 
[INDENT]
[LIST]
[*]sudo rm /etc/X11/Xsession.d/70pulseaudio
[/LIST]
 [/INDENT]


Actually, keep a copy of this file just in case.  I never feel good about deleting things if I'm not sure that the solution will work.

---

### Post by ShadowWraith on 2009-06-21
I tried your command-line method, but the system still is sure that ubuntu-desktop depends on it, and apt-get wishes to remove ubuntu-desktop as well.
Upon further inspection, the package ubuntu-desktop is a pseudopackage that depends on all the core ubuntu packages. It is described as helping to ensure proper upgrades.

Is removing this package unwise?

---

### Post by lovinglinux on 2009-06-21
> **ShadowWraith said:**
> I tried your command-line method, but the system still is sure that ubuntu-desktop depends on it, and apt-get wishes to remove ubuntu-desktop as well.
Upon further inspection, the package ubuntu-desktop is a pseudopackage that depends on all the core ubuntu packages. It is described as helping to ensure proper upgrades.

Is removing this package unwise?

Just make sure you re-install ubuntu-desktop package before upgrading to a new release (Jaunty >>> Karmic for example). If you do clean installs only, then there is nothing to worry about.

Yesterday there was some updates that installed pulseaudio and ubuntu-desktop all over again, I guess because it asked for a "Partial Upgrade". There was a kernel update too. Nevertheless, I removed pulseaudio after the update and installed esound again. Everything is fine.

---

### Post by ShadowWraith on 2009-06-21
Thank you both so much for the help!

---

### Post by nmaster on 2009-06-24
I guess i never had the "ubuntu-desktop" issue, but thanks for the heads up.  Now i'll know what to expect if that happens on a different machine.

and you are very welcome!  it makes me feel good to finally know enough to help someone else, instead of just coming with questions lol.

---

### Post by coldReactive on 2009-07-30
ubuntu-desktop is a metapackage, removing it doesn't effect anything.

---

### Post by Spoonage on 2009-09-20
Hey thanks guys, this sorted all the sound issues I've been having with java and other applications.

I did really try to work with pulseaudio but guessing it just didn't like my external sound card.

---

### Post by Bramkaandorp on 2009-10-20
I keep getting the folder ".pulse" in my home folder.

Is this normal (after removing pulseaudio), or is there a solution to this?

---

