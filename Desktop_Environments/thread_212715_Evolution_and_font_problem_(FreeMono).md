---
title: "Evolution and font problem (FreeMono)"
date: 2006-07-10
forum: Desktop Environments
---

### Post by abelthorne on 2006-07-10
I have a strange problem with Evolution. In system settings (Gnome), I've set the default fonts to the "FreeFont" family (i.e. FreeSerif, FreeSans & FreeMono), which renders incredibly well on a screen.

Evolution is supposed to use the system fonts (well, it's configured this way), so I guess it's using FreeMono for fixed-width fonts.

My problem occurs when writing a plain text e-mail : the "st" string is displayed as "t". To explain better : if I write the letters of the word "test" e.g., it'll display "t", then "te", then "tes" and then... "tet". Every time a word contains "st", the "t" letter is displayed instead. This makes reading and writing e-mails quite confusing.

It seems to happen only in Evolution and only with this fonts (well, it doesn't happen with other mono fonts I've tried, like DejaVuMono) : if I create an OpenOffice Writer document, set the font to FreeMono and write a text, the "st" string is displayed as expected.

When writing or reading HTML e-mails, it uses the FreeSans font as expected and doesn't have this display bug.

It really is a display problem : the "s" letter isn't replaced by the "t" for real, only on screen in Evolution when managing a plain text e-mail.

Can someone reproduce/confirm this ? Is it a known bug ?

I'm using an up-to-date Ubuntu 6.06 (Dapper) system.

---

### Post by abelthorne on 2006-07-10
No one can reproduce this behaviour ?

---

### Post by abelthorne on 2006-07-11
In fact, the bug seems related to the FreeMono font (I've found a bug report on Launchpad). It's strange that it doesn't happen with OpenOffice.

---

