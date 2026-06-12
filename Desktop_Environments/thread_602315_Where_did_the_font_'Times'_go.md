---
title: "Where did the font 'Times' go?"
date: 2007-11-04
forum: Desktop Environments
---

### Post by blueturtl on 2007-11-04
I opened a document I created on the previous Ubuntu release (7.04).
Now when I view the document styles it says:
> This font has not been installed. The closest available font will be used.

The font in question is Times. I never installed any extra fonts, so it was bundled with the previous release. Why is this font no longer included in Gutsy and how can I install it?

I don't want to install the msttcorefonts package, the fonts in it look ugly.

---

### Post by ofb on 2007-11-04
Without the full name for the font, this is going to be difficult. I don't see anything with 'Times' in the name on my 7.10, or in Synaptic.

A quick check of /usr/share/fonts/truetype on this install shows 152 items, vs 202 items on the 7.04 LiveCD, but most of that seems to be languages, and again nothing with Times in the filename.

(Ubuntu desperately needs a proper font browser. And yes, the msttcorefonts are ghastly. They're for the web we had a few years back.)

Is it possible you got the font installed along with some application?

---

### Post by blueturtl on 2007-11-04
I am not aware of any application that would have installed fonts on my system. The only one that springs to mind is Cedega, but it does not install the fonts globally and AFAIK the fonts it downloads are the Microsoft fonts.

Searching the forums I came over someone claiming that 'Times' is a way to avoid copyright infringement and that it's bundled with OpenOffice. The person claimed to have lost 'Times' after installing the official Microsoft version of the font.

Very curious.

---

### Post by ofb on 2007-11-04
Font copyrights, trademarks, & patents tend to be a bit of a mess, with much argument and pounding on tables. I /think/ pure 'Times' is owned by Linotype. MS had a not-bad derivative called Times New Roman, which is what a lot of people mean by Times now. And of course there are many derivatives that do and do not have Times in the name.

Little bit of that,
[http://en.wikipedia.org/wiki/Times_Roman](http://en.wikipedia.org/wiki/Times_Roman)

Without an actual file name for what you used before, we may not figure this one out, & you'll just have to find an appropriate substitute.

---

### Post by Happy_Man on 2007-11-04
Actually, I had a font called Times too, before I installed msttcorefonts. Now it's been replaced by Times New Roman. Does that help?

---

### Post by blueturtl on 2007-11-05
> Actually, I had a font called Times too, before I installed msttcorefonts. Now it's been replaced by Times New Roman. Does that help?

It does. Now I know I'm not crazy. :)
I need to re-edit the document now because "the font closest to" causes some layout issues.

> Without an actual file name for what you used before, we may not figure this one out, & you'll just have to find an appropriate substitute.

I did not think to take a note of the file name for the font since they're displayed by name in OpenOffice. Can someone who still has the font 'Times' available in OpenOffice please help me find out the filename?

---

### Post by kakka256 on 2007-11-05
> **blueturtl said:**
> It does. Now I know I'm not crazy. :)
..Can someone who still has the font 'Times' available in OpenOffice please help me find out the filename?
Moi.
I'm not very familiar with OpenOffice, Here's what i got from a find though:
```

$ sudo find / -name 'Times*'
/usr/lib/openoffice/share/psprint/fontmetric/Times-Italic.afm
/usr/lib/openoffice/share/psprint/fontmetric/Times-Roman.afm
/usr/lib/openoffice/share/psprint/fontmetric/Times-Bold.afm
/usr/lib/openoffice/share/psprint/fontmetric/Times-BoldItalic.afm

```

Hope that helps!

---

### Post by maybeway36 on 2007-11-05
I thibk "Times" if probably just a fake font that redirects to something like DejaVu or Vera.

---

### Post by blueturtl on 2007-11-06
> I'm not very familiar with OpenOffice, Here's what i got from a find though:

/usr/lib/openoffice/share/psprint/fontmetric/Times-Italic.afm
/usr/lib/openoffice/share/psprint/fontmetric/Times-Roman.afm
/usr/lib/openoffice/share/psprint/fontmetric/Times-Bold.afm
/usr/lib/openoffice/share/psprint/fontmetric/Times-BoldItalic.afm

Hmm.. I have the exact same files, and yet Times is not available.

> I think "Times" if probably just a fake font that redirects to something like DejaVu or Vera.

If so why isn't it working anymore? I'm going to try setting DejaVu or Vera to see if I can make the document look the way it's supposed to. I have a PDF copy of it to use as reference.

---

