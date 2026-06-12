---
title: "Adding fonts causes apparent font table corruption"
date: 2009-08-24
forum: Desktop Environments
---

### Post by aloishammer on 2009-08-24
[Ubuntu Jaunty 9.04]

I'm not a complete newb when it comes to font usage in X, so I'm very puzzled just now.  I'm trying to pad out my total supported Unicode planes, so I've got a smallish font package put together that I'm trying to install.  Every time I-- this is apparent --exceed a certain number of total installed fonts, something in the font stack starts serving up incorrect fonts, making various apps unusable.

The present situation in /usr/share/fonts/truetype looks like this:

cleartype freefont  msttcorefonts  openoffice  stix  ttf-bitstream-vera  ttf-dejavu  ttf-liberation  ttf-lucida

The msttcorefonts directory is in fact empty-- the cleartype directory contains a fairly comprehensive package of all the fonts that've come with Windows 95 up through NT 6.1 and Office 6 up through 12 over the years, with all fonts at their most recent possible revisions (as bundled by Microsoft), plus Fixedsys Excelsior 3.01 and Psprog for good measure.

(The STIX fonts are from the Mozilla MathML page.)

Beyond this point, adding more than a handful of fonts (Or possibly characters or glyphs or blocks or planes?) starts to cause problems-- this includes installing jaunty-release ttf-sil-gentium, ttf-sil-doulos, any of the more recent Doulos or Charis (or other SIL fonts) direct from the source.  Even ttf-ubuntu-title appears to tip the scale.

I don't have enough information to be sure what's going on, but Segoe UI is being replaced through *most* of the interface with some serif font (I think Times New Roman or a near-equivalent), serif fonts are being replaced by different serif fonts, and so on.  The transformation happens immediately after install, and is visible in the toolbar clock, gcalc, Firefox, and anything else you like.  The only thing apparently unaffected is gnome-terminal (Consolas).

In addition to all of the current-release SIL fonts, the package I'm trying to install also includes gems like Junicode, Unicode Symbols, Code2000-2002, and so forth.  (Recommendations for additional or substitute fonts welcome, if I can ever get these installed.)

I'm really not sure where to even start looking.  I've performed basic maintenance steps like 'rm -rf ~/.font*' and re-running fc-cache as root and as my login user.

Even a starting point would be appreciated at this point.

---

