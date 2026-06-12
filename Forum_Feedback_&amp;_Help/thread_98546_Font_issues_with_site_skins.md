---
title: "Font issues with site skins"
date: 2005-12-03
forum: Forum Feedback &amp; Help
---

### Post by tomchuk on 2005-12-03
The site skins aren't very friendly for people running at an increased screen dpi, or for people running Ubuntu. My Thinkpad has a real resolution of 125 dpi and running at 96 dpi isn't really an option as it makes of my favorite fonts unusable.

After looking at the Ubuntu Brown 3.5 CSS style for the forums, I noticed a few things:
1. Some fonts are specified in pixels - they look as expected.
2. Some fonts are specified in points - their size increases as dpi increases, and look horribly large at high dpi.
3. Font faces are Windows/Mac specific: I know that ```
verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif
``` will ultimately result in displaying Bitstream Vera Sans on a Ubuntu box, but why specify 6 fonts that Ubuntu users don't even have by default?

Here's what the [w3c says](http://www.w3.org/TR/CSS2/syndata.html#length-units) about using absolute sized untis:
> Absolute length units are only useful when the physical properties of the output medium are known. Since the resultant output looks like such ass on my screen, I'm pretty sure the skin designers can't make any claim to knowing anything about my screen or its resoultion.

It's generally accepted practice to *not* use point units on the web unless absolutely needed. If you'd like, I'd be more than happy to go through the site skins and fix the broken bits.

If you'd like to change your fonts from pt to px, here's the math:
72 pt = 1 in. ( css2 spec )
96 px = 1 in. ( default Ubuntu res. )
so 1 pt = 4/3 px
The 10pt font that appears all through the style would be more appropriately written as 13 px.

```
s/10pt/13px/g
s/14pt/19px/g
``` should fix everything.

---

