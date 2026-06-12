---
title: "cedega WoW opengl stopped working :/ but works on other games"
date: 2005-05-11
forum: Gaming &amp; Leisure
---

### Post by equilibrium on 2005-05-11
I had a nice setup of cedega from transgaming.

I installed cedega using the .deb and all was well. WoW worked on both directx and opengl mode. So I left it on opengl mode. I booted up today and all I get in opengl is:

"World of Warcraft was unable to start 3D acceleration."

and in directx the game works but I have no mouse cursor :(. I tried re-installing all nvidia stuff including the base modules. Altho opengl hasn't stopped working on anything else :( (quake3 works on both cedega and native).
 Still the same error tho :( I've re-installed the .deb file by doing apt-get remove cedega and then dpkg -i cedega*.deb and I've tried removing the .transgaming folders from home user directory so it resets the .config but still the same.

I did find a bug report on transgaming mailing list thru google about the error but can't find a fix anywhere  :|

---

### Post by gil-galad on 2005-05-11
That is pretty strange.  Maybe try regular wine?

---

### Post by equilibrium on 2005-05-13
I got it working now :)

ended up installing a different version of cedega and that sorted out the problems. Got it running a bit faster now also  :grin:

---

