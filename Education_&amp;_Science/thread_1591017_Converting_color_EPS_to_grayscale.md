---
title: "Converting color EPS to grayscale"
date: 2010-10-08
forum: Education &amp; Science
---

### Post by tzjin anthony ks on 2010-10-08
Hi, All!

I'm trying to convert, from the command line, a color EPS file to a grayscale EPS file.

So far, eps2eps, and convert haven't been up to snuff - eps2eps changes the bounding box, convert changes from vector to raster.

One workaround I found was 

1. convert EPS to PDF using epstopdf
2. convert PDF to grayscale using ghostscript
3. convert grayscale PDF back to EPS.

Just wondering if there's a smarter way to do it.

Cheers. Tzjin.

---

### Post by squaregoldfish on 2010-10-08
This question intrigued me, so I did a quick bit of Googling and found [pscol]("http://www.pa.op.dlr.de/%7EPatrickJoeckel/pscol/index.html"). Not had a chance to try it out, but it looks promising...

Steve.

---

### Post by tzjin anthony ks on 2010-10-08
Just tried it - It doesn't work for my xmgrace output EPS files. I guess they're one of the unsupported types.

-Tzjin.

---

### Post by anglican on 2010-10-12
> **tzjin anthony ks said:**
> Hi, All!

I'm trying to convert, from the command line, a color EPS file to a grayscale EPS file.

So far, eps2eps, and convert haven't been up to snuff - eps2eps changes the bounding box, convert changes from vector to raster.

One workaround I found was 

1. convert EPS to PDF using epstopdf
2. convert PDF to grayscale using ghostscript
3. convert grayscale PDF back to EPS.

Just wondering if there's a smarter way to do it.

Cheers. Tzjin.Does [this]("http://knol.google.com/k/carlo-caligaris/how-to-convert-a-vector-eps-color/1yx5vp4cwri6n/2#") help?

H

---

### Post by tzjin anthony ks on 2010-10-12
Yeah - that's the method I found in my googling too. I convert EPS->PDF in my first step to avoid the last PDFCrop step described in the knol.google link.

- Tzjin.

---

