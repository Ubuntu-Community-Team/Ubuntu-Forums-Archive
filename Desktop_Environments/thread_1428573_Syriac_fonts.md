---
title: "Syriac fonts"
date: 2010-03-12
forum: Desktop Environments
---

### Post by rcbinwi on 2010-03-12
I'm having a few issues with Syriac fonts.

1. The default font for Syriac does not connect letters correctly.  Syriac should have different initial, medial, and final forms.  This font only has final forms.  How do I get a font with the correct variations, and how do I get OpenOffice to know how to change them appropriately?  (I'm assuming OO can do it since Word can.)

2. Syriac has different scripts for east and west.  Does anyone know where I can get other Syriac fonts and how to install them?

3. Elsewhere a generous person told me that Pango will help me.  Can anyone give me more advice in this area?  I don't know how to run that.

---

### Post by simosx on 2010-03-13
Here is the relevant bug report for Syriac,
[https://bugzilla.gnome.org/show_bug.cgi?id=605870](https://bugzilla.gnome.org/show_bug.cgi?id=605870)

It appears that there is a regression in place (Syriac used to work but does not work now?).

In any case, the above Bugzilla report for 'pango' is the point of reference to solve the issue. You can 'subscribe' to the bug report and contribute/follow the progress.

Behdad is the maintainer of Pango and the new shaping engine HarfBuzz, so it might be good to read his relevant blog posts, [http://mces.blogspot.com/](http://mces.blogspot.com/)

---

