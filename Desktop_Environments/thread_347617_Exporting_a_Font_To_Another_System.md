---
title: "Exporting a Font To Another System?"
date: 2007-01-27
forum: Desktop Environments
---

### Post by CarlosinFL on 2007-01-27
I am using Ubuntu 6.10 right now which has a font called "Purisa" and I would like to also use this font on my Debian boxes as well. Does anyone know where I can find the .ttf files for Purisa on this Ubuntu machine so I can import it to another Debian box?

Thanks for any info!

---

### Post by andreas64 on 2007-01-28
Hi,

Fonts are normally saved in /usr/share/fonts.

Andreas

---

### Post by CarlosinFL on 2007-01-29
Thanks - I am unable to find this particular font. Anyone know exactly where this file would be?

---

### Post by gatiba on 2007-01-29
try this:
```

sudo updatedb

```

and then:
```

locate Purisa

```

---

### Post by 3rdalbum on 2007-01-29
Fonts can also be stored in /usr/share/X11/fonts.

---

### Post by CarlosinFL on 2007-01-29
I actually found it the hard way by going directory to directory.

```
carlos@lptp:/usr/share/fonts/truetype/thai$ ls
fonts.cache-1           Loma.ttf                TlwgMono-BoldOblique.ttf
Garuda-BoldOblique.ttf  Norasi-BoldItalic.ttf   TlwgMono-Bold.ttf
Garuda-Bold.ttf         Norasi-BoldOblique.ttf  TlwgMono-Oblique.ttf
Garuda-Oblique.ttf      Norasi-Bold.ttf         TlwgMono.ttf
Garuda.ttf              Norasi-Italic.ttf       TlwgTypewriter-BoldOblique.ttf
Loma-BoldOblique.ttf    Norasi-Oblique.ttf      TlwgTypewriter-Bold.ttf
Loma-Bold.ttf           Norasi.ttf              TlwgTypewriter-Oblique.ttf
Loma-Oblique.ttf        Purisa.ttf              TlwgTypewriter.ttf

```

---

