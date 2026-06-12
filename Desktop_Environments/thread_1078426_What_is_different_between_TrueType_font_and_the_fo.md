---
title: "What is different between TrueType font and the font shoing in xlsfonts?"
date: 2009-02-23
forum: Desktop Environments
---

### Post by Daniel Song on 2009-02-23
Hi, I am using Ubuntu 8.10.

When I download a ttf for a true-type font, I copied it into ~/.fonts so that I can use the font in ubuntu immediately.

However, when I type "xlsfonts", the font is not shown.

1. Does anybody know what is different between the Ubuntu Font and the font showing in xlsfonts?

2. Do you know how I can register the TrueType font into xlsfonts?

If somebody helps me above, it would be great.

Thanks,

---

### Post by compman25 on 2009-02-23
Did you do ```
sudo fc-cache -f -v
```

---

### Post by Daniel Song on 2009-02-23
Yes, I did, and it gave me
```
/home/[MYID]/.fonts: caching, new cache contents: 7 fonts, 0 dirs
```

However, still, xlsfonts does not show the font I want.

I am trying to use [http://www.fontsquirrel.com/fonts/Droid-Sans-Mono](http://www.fontsquirrel.com/fonts/Droid-Sans-Mono), Droid Sans Mono True Type Font.

How can I use the font using the font name in xlsfonts?

(Of course, I can use the font through GNOME, but some application does not use GNOME font. So, I need to use this kind of --family-font-....)

---

