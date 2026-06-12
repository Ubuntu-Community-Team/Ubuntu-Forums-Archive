---
title: "OpenOffice.org has ugly UI font"
date: 2005-11-21
forum: Desktop Environments
---

### Post by fourhead on 2005-11-21
Hello!

So here I am, having Kubuntu installed as my second OS besides Gentoo, and I like it so far. I've just noticed that in OpenOffice, the UI has a really ugly font, and it has a not very nice dark grey colour. For KDE, I'm using Bitstream Vera Sans as my font, and altough in OpenOffice the option "Use system font as UI font" is enabled, it uses this strange font. Any way around this?


Tom

---

### Post by blastus on 2005-11-21
Have you tried changing the "Screen font antialiasing" setting under Tools -> Options -> OpenOffice.org -> View? I have noticed that some applications in Linux render fonts a little differently than others.

---

### Post by fourhead on 2005-11-22
I tried this, but it didn't help. The thing is that the UI uses a completely different font than the rest of the system, although OOo is configured to use the system font. May this be an AMD64 issue since my whole system is amd64, but OOo is the only 32bit application.

Tom

---

### Post by cus on 2005-11-24
[QUOTE=fourhead]I tried this, but it didn't help. The thing is that the UI uses a completely different font than the rest of the system, although OOo is configured to use the system font. May this be an AMD64 issue since my whole system is amd64, but OOo is the only 32bit application.

Tom[/QUOTE]

Had the same problem with fonts - I wanted to get everything over to Tahoma. Turns out that OOo looks for the 'Andale Sans UI' font and if it can't find it, it goes for whatever it can find.

Try the following:

In OOo, go to Tools/Options/Fonts

Tick 'apply replacement table'
In the Font box type Andale Sans UI (I don't think it's part of the selectable dropdown). Replace it with Tahoma or whatever you want. See whether that works :)

---

### Post by fourhead on 2005-11-24
Thanks a lot, this solved it at least partly. I now have Bitstream Vera Sans as the OOo UI font, but it's REALLY big so I have to set OOo to scale down to 80% in Tools->View. Well, thats okay, but it still uses a pretty dark grey color for the UI not so nice, but I can live with that. Thanks a lot!


Tom

---

