---
title: "Why on official website of MAME, there is no single word about Linux?"
date: 2008-12-22
forum: Gaming &amp; Leisure
---

### Post by frenchn00b on 2008-12-22
Mame:
 [http://mamedev.org/release.html](http://mamedev.org/release.html)
 
 Why mame hasnt released an official linux version on mameworld/mamedev.org?

---

### Post by etlpkby on 2009-01-05
Yeah, I'm disappointed by the mamedev.org team.

I downloaded the latest released mame.zip from their site (src code) and looked at the associated makefile. There's mentions of 'unix' and 'sdl' (within the makefile) but there only windows directory...

src/osd/windows/*

Which is used by the top level makefile :(

So you can't even override the 'OSD' in the top level makefile ('make OSD=unix') as there isn't a 'src/osd/unix/*' area.

I know people will say, "well you're supposed to use xmame-common and associated packages etc etc", but FFS... this is the mame development MASTER site!!! It should all flow from mamedev.org into the various platforms (win,mac,*nix).

Patrick/

---

### Post by DoktorSeven on 2009-01-06
Because mainline MAME is for Windows.  It's up to [others](http://rbelmont.mameworld.info/?page_id=163) to make other versions.

---

### Post by etlpkby on 2009-01-16
Fine, but it'd be nice if the mame devteam stated on their website, "We only develop for windows" or suchlike. Jeez.

---

### Post by disturbedite on 2009-01-16
> **DoktorSeven said:**
> Because mainline MAME is for Windows.  It's up to [others](http://rbelmont.mameworld.info/?page_id=163) to make other versions.
100% correct. that is why rbelmont's site exists.

although, the OP makes a valid statement. it would be nice to have a link to rbelmont's website on the front page. although there is a link to it (and others) buried in the FAQ:
[http://mamedev.org/devwiki/index.php/FAQ:About#What_platforms_does_MAME_run_on.3F](http://mamedev.org/devwiki/index.php/FAQ:About#What_platforms_does_MAME_run_on.3F)

---

### Post by hikaricore on 2009-01-16
Might this matter better be brought up with the MAME team themselves?

---

