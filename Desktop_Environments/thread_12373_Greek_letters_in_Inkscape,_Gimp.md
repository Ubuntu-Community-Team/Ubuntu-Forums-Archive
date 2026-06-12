---
title: "Greek letters in Inkscape, Gimp?"
date: 2005-01-24
forum: Desktop Environments
---

### Post by malmjako on 2005-01-24
I can't seem to get Greek letters in Inkscape and Gimp. Using the font Standard Symbols gives me greek letters in OpenOffice.org, but not in Inkscape or Gimp. Why is this? How can I get greek letters?

---

### Post by EdSanville on 2007-04-06
I am also very interested in using Greek letters in Inkscape.  I notice that this post is over 2 years old, however, so I don't hold out much hope of ever being able to do this.  As the original poster says, using the Symbol font doesn't produce Greek letters like it should in Inkscape.

---

### Post by JudgeFudge on 2007-10-11
Not a perfect solution but I had some success with copying the greek letter .svg files from wikipedia , importing into inkscape and then manually connecting the letters to form words.

I converted the objects to paths in order to delete the roman character.

---

### Post by Namtabmai on 2007-10-11
Which SymbolGreek are you using? I assume it's a non-unicode font? Where I work we use Gentium for our display greek (ancient greek) on our websites, while people use a very old Mac only Symbolgreek font to actually type the greek (which a complicated conversion between the two).

I got a version of SymbolGreek from [here]("http://gainsford.tripod.com/fonts_nonunicode.htm#supergreek"), but it's incompatible with the version of SymbolGreek we use at work. And you can get Gentium from here, [http://www.sil.org/~gaultney/gentium/](http://www.sil.org/~gaultney/gentium/).

Both seem to work fine for me, see the attached screenshot. Gentium at the top and SymbolGreek at the bottom.

---

### Post by paskal on 2008-03-11
In Inkscape:
- Find the unicode number from [http://unicode.org/charts/PDF/U0370.pdf](http://unicode.org/charts/PDF/U0370.pdf) corresponding to the greek letter you want.

- In a text cell, type ctrl+u

- Type the unicode of your greek letter and press enter.

ref: [http://wiki.inkscape.org/wiki/index.php/FAQ#How_to_insert_math_symbols_or_other_special_symbols_in_the_drawing.3F](http://wiki.inkscape.org/wiki/index.php/FAQ#How_to_insert_math_symbols_or_other_special_symbols_in_the_drawing.3F)

Or check this out :[http://www.elisanet.fi/ptvirtan/software/textext/index.html](http://www.elisanet.fi/ptvirtan/software/textext/index.html)

---

### Post by simosx on 2008-03-16
If you want to type Greek, just setup the Greek keyboard layout in your system.

Right-click on the top panel and add the Keyboard Indicator applet. An applet appears on the panel. Right-click, go Preferences, then go to Layouts and add Greek. You can switch with a keyboard shortcut or simply by clicking on the new applet, The mapping of Greek and Latin is more or less the same, so it should not be difficult to type.

For more, see
[http://blogs.gnome.org/simos/2008/02/03/typing-squiggles-and-dots-in-gnome-and-gtk-applications/](http://blogs.gnome.org/simos/2008/02/03/typing-squiggles-and-dots-in-gnome-and-gtk-applications/)

---

