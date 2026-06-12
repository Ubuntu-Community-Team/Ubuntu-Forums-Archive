---
title: "Bold font not displaying in any program"
date: 2005-02-10
forum: Desktop Environments
---

### Post by Monika on 2005-02-10
When I display a page in Firefox which has bold fonts, the bold fonts do not display (or rather I wonder whether possibly everything is in bold, but I'm not sure). Also in Open Office, bold font doesn not seem to display, even though "it's there". In Windows this is fine.
It's taken my a longer while to notice this... I mean initially I noticed this in Open Office, but it didn't annoy me at the time that much, so I never bothered to search for the problem and then finally I noticed this happens in Firefox as well - it's just that I never knew there were any bold fonts on some pages before...

What can I do about it?

---

### Post by Monika on 2005-02-13
Nobody else having this problem?

I've now discovered that is is only a problem with certain fonts. For example Helvetica does display both bold and normal text. But Nimbus Roman does not.

---

### Post by stoffe on 2005-02-13
Are you sure that you have a bold version of Nimbus Roman installed?

I just looked at the fonts on my system, with gfontview (there might be better programs) and I only have Medium and Regular, in [FONT=Courier New]/usr/share/fonts/type1/gsfonts[/FONT]. Now I have no idea if there is a bold version or on how/where to get it, but that may well be it. The Medium version is pretty boldish, maybe you can use that instead?

---

### Post by piedamaro on 2005-02-13
You miss the bold version for those fonts.

---

### Post by Monika on 2005-02-13
So how do I fix this problem (explanation for dummies please ;) )?

---

### Post by piedamaro on 2005-02-13
[QUOTE=Monika]So how do I fix this problem (explanation for dummies please ;) )?[/QUOTE]
You can configure firefox not to use those fonts, and the same with open office. However, on firefox, sometimes fonts are forced through the use of aliases, defined in your /etc/fonts.conf file (or /etc/fonts/fonts.conf).
Also you need some additional fonts, you can find them in the package: msttcorefonts
Is it possible to know which page on firefox renders w/o bold fonts?
Hope this helps ;)

---

