---
title: "No internet sound :("
date: 2006-09-30
forum: Desktop Environments
---

### Post by dudeness3 on 2006-09-30
I have system sounds, but no internet sounds, what can i do to fix this?
PS:
UBUNTU LINUX RAWKS

---

### Post by dudeness3 on 2006-09-30
Can anyone help?

---

### Post by blueturtl on 2006-09-30
What do you mean by "internet sound"?
Can you post a URL to a webpage that should have sound?

---

### Post by djRobbieF on 2006-09-30
No Internet sounds?  Do you mean, like no flash?  or what?

It's most likely either a plugin or codec that is missing, but it will be more specific than just "internet sounds".

Have you installed codecs and programs like flash plugin, etc?

Try [Needed Extras for Ubuntu Dapper]("http://ubuntulondon.wordpress.com/2006/08/21/needed-extras/")

---

### Post by dudeness3 on 2006-09-30
what i mean is, website that have sounds, like newgrounds, or homestarrunner.com, will play no sound whatsoever, i have installed the flash player plugin, but i get no sound on those sites, or others that play sounds, and that site kinda doesnt help, because i dont know anything about linux.

---

### Post by djRobbieF on 2006-09-30
Do you by any chance have two soundcards?  Perhaps one built-in, and one PCI card?

---

### Post by dudeness3 on 2006-09-30
Nope, just one built in, I never had this issue with windows, i think my computer just doesnt like linux :(

---

### Post by blueturtl on 2006-09-30
If your soundcard is properly detected and configured there's no reason for not having sound in all applications.

Have you right-clicked the little speaker in the top-right corner of the screen and checked that all the volume sliders are enabled? Mainly PCM, WAV and Main.

If the mixer is ok, what motherboard is it that you are using?

Also, are you certain the Flash plug-in is properly installed?

---

### Post by infol on 2006-09-30
hi dudeness;

this is probably due to flash using an old directory structure for esd;
try going into the console and type:

```
ln -s /tmp/.esd-1000 /tmp/.esd
```

(assuming your user account no is 1000 - it should be if your are using the [first] account created during the ubuntu installation)

restart your browser, and voilá!

---

### Post by Jose Catre-Vandis on 2006-09-30
Also try installing mplayer and the mplayer browser plugin, that takes care of most web enabled sound (Automatix will sort this out for you, along with most codecs.) Also, if the website has sounds embedded with the bgsound tag, firefox does not support this, however there is an extension that will sort this out for you.

---

