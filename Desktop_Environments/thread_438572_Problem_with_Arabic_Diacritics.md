---
title: "Problem with Arabic Diacritics"
date: 2007-05-09
forum: Desktop Environments
---

### Post by falt004 on 2007-05-09
Hi,

Was wondering if anyone is having trouble with the way diacritics in Arabic appear. I'm using Kubuntu 7.04, with all the relevant font packages installed (ttf-arabeyes xfonts-intl-arabic ttf-kacst msttcorefonts). Arabic text appears fine, but if there are any diacritics, they look funny: either splitting the word, too far from it, superimposed on a letter, etc...

For example, (this is copied from [http://alghad.dot.jo/index.php?news=172890](http://alghad.dot.jo/index.php?news=172890))

&#1593;&#1605;&#1617;&#1575;&#1606;

On my system,  the "shadda" divided the "meem" and the "alef".

Any ideas?

Cheers,
/Fuad

---

### Post by falt004 on 2007-05-17
Just wanted to add that this problem seems to be only in Firefox, Konquerer renders Arabic fonts and diacritics without any problems...

---

### Post by sethmahoney on 2007-05-18
I would guess that this is a font issue.  Try changing the default font in Firefox and see what happens.  I have similar problems with Cyrillic fonts, and this is an effective workaround for me.

---

### Post by falt004 on 2007-06-20
Finally found a solution to this problem. In Ubuntu by default disables Pango support - all I had to do was enable it by running firefox the following way:

```
MOZ_DISABLE_PANGO=0 firefox
```

---

