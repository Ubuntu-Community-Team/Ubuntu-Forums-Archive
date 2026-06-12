---
title: "ZSNES distorted Sound"
date: 2007-03-18
forum: Gaming &amp; Leisure
---

### Post by bigee1212 on 2007-03-18
Hey all,
  I'm having some trouble with my SNES emulators in Ubuntu. Specifically ZSNES. In Windows, version 1.51 works great. However, ZSNES 1.42 in Ubuntu (respitory version) has distorted sound. When I run ZSNES through sudo the sound seems to be a bit better, but still distorted. SNES9x sound works fine with the same rom. But I don't like snes9x compared to zsnes. anyone have any ideas how to fix this? 
  Also, has anyone compiled the new 1.51 version from their website and how has it performed?

PS (UBUNTU EDGY EFT)

---

### Post by encompass on 2007-03-18
Could you tell a little about your sound card.  Sounds like an issue with HOW the sounds are played... try this once before starting the program.
sudo killall esd
and see if the sound improves.

---

### Post by Lystrodom on 2007-03-18
I've got the same problem, and sudo killall esd didn't help.

Also, I compiled it from source from the website, it seems about the same to me. No improvement in sound, definitely. The only problem with it, though, was checkinstall failed to make it a .deb, so it will be harder to remove.

The games' sound work fine on Snes9x, but I can't get my gamepad to work with Snes9x...

---

### Post by Lystrodom on 2007-03-18
I fixed it. Try installing libsdl1.2debian-oss. It should be in the repositories.

---

### Post by fearpi on 2007-04-22
This helps greatly, but my sound still stutters. Anything else I can do?

---

