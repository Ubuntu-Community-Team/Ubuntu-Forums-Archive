---
title: "OpenType font features in KDE"
date: 2019-08-21
forum: Desktop Environments
---

### Post by CatKiller on 2019-08-21
I really like the font that I'm using (Source Sans Pro), but I'd prefer to not use things like the two-storey g. Happily, the OpenType format allows for glyph substitution for exactly that purpose with stylistic sets.

The font configuration tool in System Settings doesn't allow specifying those options. There are two other methods that I'm aware of for making use of that feature: as a global option with fontconfig in the fonts.conf file, or as part of the name such as **Source Sans Pro:ss02&ss03&ss04**.

Unfortunately, KDE seems to ignore fonts.conf entirely in favour of its own kdeglobals file, and amending the font entries in kdeglobals causes KDE to discard that file entirely. I am at a loss now for how to persuade KDE to display the correct glyphs. Perhaps KDE isn't capable of displaying the correct glyphs at all.

I would appreciate any assistance or insight.

---

### Post by CatKiller on 2019-08-26
Using all colons, like Source Sans Pro:ss02:ss03:ss04, doesn't work either. It doesn't make kde go crazy and generate a new one with defaults like using the ampersand does, but it just silently strips out those options.

---

