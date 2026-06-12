---
title: "openoffice and hinting (rough luxi fonts)"
date: 2005-07-16
forum: Desktop Environments
---

### Post by burlap on 2005-07-16
Recently I have decided to change appearance of my Hoary a bit (well, under some influence of Fedora...), what included enabling autohinting (system wide) and picking Luxi Sans as the interface font. 

First impressions with autohinting: some fonts look better, some worse (I know I can make separate rules for every font, it is irrelevant), Best results are finally readable, LCD-specific font options make them look worse (at least on my cheap 2-year old panel). 

Second impression: openoffice (standard 1.1.3, I don't want to use 2.0 yet) is in big trouble. 

First of all Luxi Sans as an interface font is not hinted at all. Many other fonts are (I've tried a few, like Arial, Verdana, Bistream Vera Sans, etc.).

Also Luxi fonts (all three) don't appear properly in openoffice fonts dropdown menu (are visibly smaller and it reads "Luxi Sans ·‰',&#539;&#378;&#368;"). 

I have tried different combinations of antialiasing on and off and different setting in font properties without much effect. I've also tried "sudo f-cache -v", reconfiguring font packages and other tricks. 

Any suggestions?

(I do want to stick with luxi sans as my interface font. I can set different font for openoffice but I want to have a consistent UI).

Attachment shows openoffice and abiword with luxi sans.

---

### Post by burlap on 2005-08-26
Luxi quest continues...

I have noticed that luxi comes in two packages: as t1 and ttf font. As hinting problems (Apple patents) concern ttf fonts (as far as I understand it at all), I decided to remove ttf luxi package. I disabled autohinting and now luxi looks the same in gnome interface and openoffice (however, hinted luxi is a bit better). 

The problem is that in openoffice 1.1.3 luxi lost Polish characters (I get "Narz dzia" instead of "Narz&#281;dzia"). Some characters are there, but look as if they came from a different font. 

Also, other problems with Luxi in openoffice were not solved. 

Openoffice 1.9.121 has no problems.

---

