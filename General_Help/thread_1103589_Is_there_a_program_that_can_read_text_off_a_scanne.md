---
title: "Is there a program that can read text off a scanned document and make it editable?"
date: 2009-03-22
forum: General Help
---

### Post by jamieh on 2009-03-22
I've got a huge collection of scanned documents (see attachment for example) that I need converted to an editable format. Whats the easiest way I could accomplish this without *shudders* retyping everything?

I need this done by tonight, so a quick answer would be appreciated.

Thanks

---

### Post by issih on 2009-03-22
[https://help.ubuntu.com/community/OCR](https://help.ubuntu.com/community/OCR)

Not exactly a great selection, but its a starting point...

---

### Post by jamieh on 2009-03-22
> **issih said:**
> [https://help.ubuntu.com/community/OCR](https://help.ubuntu.com/community/OCR)

Not exactly a great selection, but its a starting point...

Hmm... my documents are multi-column :(

---

### Post by FluffyElmo on 2009-03-22
You could use the Gimp to slice each column into a separate image. As noted at the end of the link above you will probably have to use the Gimp to save them in an usable format anyways. Probably still lot faster than re-typing though I guess it depends how much you have to convert.

---

### Post by KeyserSoze93 on 2009-03-23
If you install gocr and imagemagick, then this script should cover the basics (w/ three colums):

```

#!/bin/bash

touch page.txt

mogrify -crop 34% page.jpg

for i in page-*.jpg; do
convert $i pbm:- | gocr - >> page.txt
done

rm page-*.jpg

```

---

### Post by 7@m3 G33k on 2009-04-11
I've been playing with a couple of OCR offerings today and in terms of what saves the most time overall tesseract (see the Ubuntu OCR link above) is by far the best. Kooka looks great but the OCR engines it uses are, in my limited experience, poor or worse with real-world scanned documents: ocrad achieves only about 60-70% accuracy and correction is clunky at best, gocr is utterly hopeless.

As noted above, if you have anything other than a single column document when using tesseract you will have to play around with it in GIMP but once you've done that it's quick and the results excellent (99%+ accuracy). I'm a GUI fan but when you have a CLI program like tesseract that is simple to use and works so well I can't complain.

---

