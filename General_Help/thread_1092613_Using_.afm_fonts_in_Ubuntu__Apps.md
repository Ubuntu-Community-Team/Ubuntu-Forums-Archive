---
title: "Using .afm fonts in Ubuntu / Apps"
date: 2009-03-10
forum: General Help
---

### Post by dehuszar on 2009-03-10
I am working with some designers who need some typography work for which they have .afm files.  They are Mac users.  I've tried using the .afm files in my .fonts folder, but they do not show up in any font lists like the .ttf files I drop in there.  I've tried using some shareware conversion tools, but they only convert the .afm files to .pfm fonts which also don't work.

Has anyone done this?  I've seen a bit of chatter about .afm and latex, but I don't know anything about latex.  I just want to use some of these fonts in Inkscape for creating web elements.

Any help is appreciated.

---

### Post by hugmenot on 2009-03-11
[AFM files aren&#8217;t fonts.]("http://en.wikipedia.org/wiki/Adobe_Font_Metrics#Adobe_Font_Metrics.2C_Adobe_Composite_Font_Metrics.2C_Adobe_Multiple_Font_Metrics") They are text fiels containing font metrics. AFM = Adobe Font Metrics. They usually come with PostScript Type1 fonts but aren't necessary to use the font. The fonts themselves are in .pfb files, which are binary and contain the outlines. They usually are all that's needed. Copy the .pfb files into .fonts and you should see them get listed.

---

