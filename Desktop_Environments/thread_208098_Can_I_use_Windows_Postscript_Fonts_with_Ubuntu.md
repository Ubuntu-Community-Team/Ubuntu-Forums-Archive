---
title: "Can I use Windows Postscript Fonts with Ubuntu?"
date: 2006-07-03
forum: Desktop Environments
---

### Post by sgarman on 2006-07-03
Hi all,

I know Xorg/Ubuntu supports TrueType fonts, but a specific font I'd like to use (Myriad Headline) is only available in Windows and Mac Postscript format:

[http://www.myfonts.com/fonts/linotype/myriad/headline/](http://www.myfonts.com/fonts/linotype/myriad/headline/)

Before I buy the font, I want to make sure I can use it with Ubuntu. Also, can I just download it to my ~/.fonts directory, or do I have to install it in another location?

Thanks,

Scott

---

### Post by deanjm1963 on 2006-07-03
Of course you can use windows ps fonts, even OpenType. I have nearly 2000 adobe fonts installed, 95% opentype and the rest type 1 ps fonts. If you're the only person using the computer, ~/.fonts is fine, if you're using the postscript version make sure you copy the *.afm *.pfm *.pfb files, opentype only have 1 file, the font itself.

---

### Post by aysiu on 2006-07-03
I can't give you a definitive answer, but a search in Synaptic for *postscript font* turned up some promising results: > Font data of Adobe Japanese fonts (futomin, futogo, jun101)
Virtual font and TFM files for Adobe postscript fonts:
 FutoMinA101-Bold-H, FutoGoB101-Bold-H, Jun101-Light-H
Also style file and fontdesc file for these fonts. from *dvi2ps-fontdata-three*.

Or > Font Editor for PS, TrueType and OpenType fonts
FontForge (formerly PfaEdit) allows you to edit outline and bitmap fonts.
You can create new ones or modify old ones.  It is also a font format
converter and can convert among PostScript (ASCII & binary Type 1,
some Type 3s, some Type 0s), TrueType, and OpenType (Type2). from *fontforge*

There may be others you find helpful.

---

### Post by sgarman on 2006-07-03
Thank you, I was just looking for that confirmation. The fonts are working great once I dumped them in ~/.fonts and ran fc-cache. 

Regards,

Scott

---

