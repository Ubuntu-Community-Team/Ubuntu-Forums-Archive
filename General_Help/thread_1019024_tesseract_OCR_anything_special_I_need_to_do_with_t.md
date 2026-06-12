---
title: "tesseract OCR: anything special I need to do with the riff files?"
date: 2008-12-22
forum: General Help
---

### Post by Cracauer on 2008-12-22
I'm trying to use tesseract.  Like some years back, even with the new packages on Ubuntu-8.04 I only get garbage out of it, and I mean garbage-garbage. There is not a single syllable that's correct. Since this has been going on for years I begin to think it's a pilot error (cough).

Is there anything special that I need to do with the tiff files?

Example: "your idiot, you need a monochrome tiff, not a greyscale", "dude, no compression, what are you thinking?" or similar advice would be very welcome.

---

### Post by Cracauer on 2008-12-22
Figures. I post, then I find the answer.

I have too high resolution. Anything above 2700 pixels vertical is garbage.

2700 doesn't deliver optimal results, the optimum is somewhere between 1300 and 2000 when downsizing with ImageMagick's convert.

---

