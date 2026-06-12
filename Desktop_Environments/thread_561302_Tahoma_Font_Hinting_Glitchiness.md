---
title: "Tahoma Font Hinting Glitchiness"
date: 2007-09-27
forum: Desktop Environments
---

### Post by BattlePanic on 2007-09-27
I have been using Ubuntu for about a week and am enjoying the learning process.  These forums have been an invaluable resource.  Thank you all.

I was unhappy with the default font configuration in Feisty.   I wanted smaller, legible font sizes without having to resort to anti-aliasing or any fancy smoothing algorithms at the smaller font sizes, which is just how standard font smoothing works in Windows.  So, I set out to bring the lovely Windows fonts that I'm used to over to GNOME.   I came across [[COLOR="Blue"]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=208396") which proved to be a huge help.  I now have Microsoft's Tahoma font at 8pt throughout most of the GNOME user interface.

After a few minutes I noticed some very subtle weirdness in how the font was rendered.  After a closer look I realized that Tahoma 8pt in GNOME is not the same as Tahoma 8pt in Windows.  A few of the characters have a stray pixel here or there.  I have noticed this on the lowercase 'v', uppercase 'Q','W', and the numerals '6' and '8'.  There are also a few differences in Tahoma's bold font.

I am not a font expert, but from the reading I've done, I've discovered that a font renderer sometimes relies on something called font hinting which is data that can be embedded in a TrueType font file.  This extra information helps nudge pixels into a visually pleasing alignment at specific point sizes.  Since this information is embedded within the font itself, shouldn't the font hinting provide consistent, pixel-perfect rendering even on Linux?

To review, My fontconfig setup has disabled font smoothing for the Tahoma font at 8pt and as far as I can tell the 'autohinting' algorithm is disabled as well.  Autohinting, appears to be an feature that allows the rendering to ignore a font's embedded hinting data and make things pretty without a font's explicit instructions.  I am also running the fonts at 96dpi which I believe is the GNOME default.

I've attached a screenshot so you can see what's going on here.  I've also enlarged the image for easy viewing.  On top, is a GNOME window displaying Tahoma 8pt.  On bottom, I've connected to Windows machine via Remote Desktop and displayed the same font.  Why would these subtle differences exist?   Is there a way to correct them? 

P.S.  I've noticed similar little differences with another MS font under GNOME but since I'm staring at Tahoma all day, I figured I'd start with there.

---

### Post by Aphorism on 2008-01-02
Indeed, it comes down to font hinting.  The following applies to the patent encumbered True Type fonts category.

Simply, the font hinting often comes down to a font hinting virtual machine(1).  Some of those techniques are patented(2).

In terms of an end user, unless the hinting engine is an exact verbatim 1:1 copy of the hinting engine on Platform X, we can assume you will encounter differences with TrueType rendering.  Perhaps a low level font library expert might be able to shed more light on the underlying issues.

Sincerely,
TJS

References:

1 Virtual Machines and Font Hinting:
[http://en.wikipedia.org/wiki/TrueType#Hinting_language](http://en.wikipedia.org/wiki/TrueType#Hinting_language)
2 TrueType Patent Issues:
[http://www.freetype.org/patents.html](http://www.freetype.org/patents.html)

---

### Post by BattlePanic on 2008-02-14
Thanks for sharing the links.  Since my original post I've upgraded to Ubuntu 7.10 Gutsy and I've noticed that the rendering of an unaliased Tahoma at 8pt looks like it has improved from the previous version of Ubuntu.  There are fewer glyphs with pixels in odd places.  Here's to progress.

I didn't realize that the hinting language was so complex.  I figured it was simply a matter of telling the renderer to nudge a pixel here or there but it sounds like there's more to it than that.  The complexity of the language makes it easier to understand why different implementations of the interpreter might make for some differences in the font rendering.  Nonetheless, I'd still be tempted to call these differences bugs.  I'm assuming, of course, that the hinting language is unambiguous in its instructions to the virtual machine.

I haven't really taken the time to figure out if the Freetype library used in Ubuntu 7.10 was compiled with the bytecode interpreter or if it's relying on the auto-hinter.  I never found a definitive answer but I think I came to the conclusion that the byte-code interpreter was being used in Ubuntu.  I'd be interested in seeing a side-by-side comparison of the interpreter vs. the auto-hinter.

I happened upon this [interview with David Turner]("http://www.osnews.com/story/18166/Interview_with_David_Turner_of_Freetype") of Freetype a while back and found that it helped shed some light on the subject.

---

