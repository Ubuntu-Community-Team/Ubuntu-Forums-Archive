---
title: "Nautilus to preview WMF files"
date: 2004-12-01
forum: Desktop Environments
---

### Post by David Cartwright on 2004-12-01
Wondering if Nautilus can preview WMF graphics files?

I've got the **libwmf0.2-7** package installed.

Is there something else needed for Nautilus to preview WMFs, or are they unsupported?

thanks ... david

---

### Post by SSamiK on 2005-07-28
Same question from me.... or a way to make gThumb to display them.. 
These WMF files are really beginning to annoy me! It's too mutch tumbling  around opening each and every file in The Gimp to preview them...  :-| 

Or if someone knows of a picture viewer who supports WMF, that would also help.

---

### Post by viniciusandre on 2008-07-07
Well, tired of looking for a intelligent solution, I gave up from trying to find a way to make Nautilus or other Ubuntu stuff to read all these Windows things.

Install the converters:
sudo apt-get install libwmf-bin

Convert everything (using wmf2fig, couldn't use any other one due to several errors):
for i in *.wmf;do wmf2fig $i;done
for i in *.eps;do convert $i $i.jpg;done

Rename JPGs (lazy enough not to put a 'cut'):
rename 's/\.eps\.jpg/\.jpg/g' *

Cleaning all the mess:
rm *.wmf *.eps

Hope this helps! :)

---

