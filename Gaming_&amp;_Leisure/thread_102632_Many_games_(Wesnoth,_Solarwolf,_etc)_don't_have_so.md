---
title: "Many games (Wesnoth, Solarwolf, etc) don't have sounds (FIX)"
date: 2005-12-12
forum: Gaming &amp; Leisure
---

### Post by polpak on 2005-12-12
I was having some issues with a bunch of games in breezy on my new laptop which uses the AC97 onboard sound. No games (apart from the standard gnome ones) would output any sound at all.

I eventually discovered the fix, and thought I'd put it here for your edification.

I had to install libsdl1.2debian-esd from the universe repos. This removed libsdl1.2debian-oss but everything seemed to work fine after that.

I think the bigger issue is that OSS just doesn't work, but since I can't figure out how to solve that problem, I'll just have SDL use esd and point all my other apps to use ALSA or esd and try to avoid OSS when I can.

If anyone wants to help with the OSS problem the error I get when I select OSS in the multimedia systems selector is "Failed to construct pipeline".. I see the kernel modules loaded, but it just won't work.

---

