---
title: "Whitelist a font of a certain size and family"
date: 2007-11-03
forum: Desktop Effects &amp; Customization
---

### Post by RommeDeSerieux on 2007-11-03
I'm used to MiscFixed font i had in other distros, which is the same as Fixed, but not larger than 11. It's missing in Ubuntu, and additionally all bitmap fonts are blacklisted by default. I've been able to enable Fixed, which i need, but how do i restrict it to a certain size? Here's the contents of /etc/fonts/conf.d/80-misc-fixed.conf, which i had created myself:

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<!-- Accept the Fixed font of a certain size -->
 <selectfont>
  <acceptfont>
   <pattern>
     <patelt name="family"><string>Fixed</string></patelt>
     <patelt name="size"><double>11</double></patelt>
   </pattern>
  </acceptfont>
 </selectfont>
</fontconfig>
```

Unfortunately, the second <patelt> element seems to have no effect.

---

