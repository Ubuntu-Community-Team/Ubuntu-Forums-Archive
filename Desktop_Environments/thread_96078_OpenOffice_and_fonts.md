---
title: "OpenOffice and fonts"
date: 2005-11-28
forum: Desktop Environments
---

### Post by Kray on 2005-11-28
Hello

OpenOffice bundled with Breezy always use bytecode interpreter if possible - it means that even if u switch to autohinter (sudo dpkg-reconfigure fontconfig) OO will continue to use BI. Basic solution is to make own libfreetype package with bytecode interpreter disabled - [http://www.ubuntuforums.org/showthread.php?t=84359&highlight=openoffice+libfreetype]("http://www.ubuntuforums.org/showthread.php?t=84359&highlight=openoffice+libfreetype"). I did it and comparing screenshots before and after it looks that autohinter is now used. But... fonts looks little jagged in OO and in certain sizes specific letters are renderer in weird way. In generic Gnome apps fonts are *almost* perfect - just few minimal quirks here and there (DejaVuSans 8, 96 DPI). My first guess would be that OO don't care about system font settings like antialias type, hinting level etc, doesn't read ~/.fonts.conf etc,. So my question is simple - how to make OO fonts in pair with rest of my pretty, polished Ubuntu? :]

-- edit

After few experiments it's clear that changing font settings (System->Preferences->Fonts) doesn't affect OO fonts. My default settings is 'Subpixel antialiasing' (subpixel aa, full hinting), OO fonts are renderer just like 'Best shapes' scheme ('gray (? not sure about english term) aa, medium hinting).

Cheers, K.

---

