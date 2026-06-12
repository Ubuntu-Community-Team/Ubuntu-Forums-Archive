---
title: "Unable to set slight font hinting"
date: 2009-02-01
forum: General Help
---

### Post by rdaysky on 2009-02-01
Greetings,

today’s upgrade of Kubuntu 8.10 to KDE 4.2 went great, but I can’t sort out one thing which is important for me—font hinting. I want slight hinting, but whatever I do I get a stronger level which causes ugly uneven letters.

My .fonts.conf was unchanged by the upgrade, and it does contain the “hintslight” entry, as well as subpixel aliasing. I ran dpkg-reconfigure fontconfig-config to no avail. The only entries in /etc/fonts/conf.d that look relevant are 10-hinting-slight.conf, 11-lcd-filter-lcddefault.conf, 53-monospace-lcd-filter.conf, but whatever I do with them, KDE (or Qt? or FreeType?) disregards my wishes and displays heavily hinted text. Are there any other files which control font rendering?

What do I do to be sure hinting is set to slight? If I run ftdiff from freetype2-demos and choose what it calls “light auto hinter”, then it displays text perfectly (for me).

-- 
TIA
Roman.

---

### Post by hugmenot on 2009-02-03
[https://bugs.launchpad.net/bugs/217729](https://bugs.launchpad.net/bugs/217729)

---

