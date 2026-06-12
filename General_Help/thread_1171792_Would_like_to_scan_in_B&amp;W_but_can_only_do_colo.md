---
title: "Would like to scan in B&amp;W but can only do color or greyscale"
date: 2009-05-27
forum: General Help
---

### Post by DocEsq on 2009-05-27
HI all,

I am running Ubuntu 8.04 LTS and would like to scan faxes and pdfs in Black and White.  When I try to scan using gscan2pdf or Xsane I am only given a choice of color or greyscale.  How do I scan in Black and White?

Thanks for any help you can give.

Docesq

---

### Post by CatKiller on 2009-05-28
Greyscale **is** black and white. If you need to increase the contrast between the black and the background, you can change XSane's image settings.

---

### Post by DocEsq on 2009-05-28
When I use my Microtek scanner in windows I am given the choice of color, greyscale or Black & White.  Each scan comes out differently so I was just wondering if there is a preset I can us in Ubuntu rather than going into Xsane.

Thanks.

---

### Post by CatKiller on 2009-05-28
When I use my scanner, there is a "Lineart" option that uses a high contrast setting meant for images that don't contain much grey. I understand that the options that are available are provided by the sane backend that you're using and so will be different for each type of scanner.

I have no idea what you mean about setting scanning options without using Xsane. Surely you'd just set it to high-contrast as part of your normal colour-correction step when you acquire the image? Any adjustments that you do will be saved for next time, and it's also possible to save those settings separately.

---

### Post by mbeach on 2009-05-28
> **CatKiller said:**
> Greyscale **is** black and white

Not sure I agree with that, but perhaps I'm missing something. In this context I think of black and white as what I get in my fax to email attachments. A binary type image where only 'pure' black on white background. Grayscale has many shades of gray, and would be what I think of in a black and white photograph. I think the op is looking for the line art setting, however, as you suggest.

edit:
@docesq - what type of scanner are you using. Noticed a bug filed at:
[https://bugs.launchpad.net/ubuntu/+source/sane-frontends/+bug/365064](https://bugs.launchpad.net/ubuntu/+source/sane-frontends/+bug/365064)

---

