---
title: "ttf support in php5"
date: 2008-08-21
forum: Desktop Environments
---

### Post by rooster_fruit on 2008-08-21
i set up an apache2 server on my desktop ubuntu using synaptic (php5, php5-msql, phpmyadmin, apache2, php5-gd) and it works just fine, but when i want to use a truetype font with the
> imagettftext($image,21,0,0,0,$color,$font,$text);
function, i get a
**The image "http://localhost/image.php" cannot be displayed, because it contains errors.**

if i just replace imagettftext with
> imagestring($image,1,0,0,$text,$color);
it works (without the font)

i directly copied the script (and the font file) from my windows computer (where id does work), so in theory, this should work too, right?

there's one difference in the gd_info from my windows computer and my ubuntu desktop; the ubuntu says
> FreeType Support: Enabled
FreeType Linkage: with freetype
and my windows says
> TrueType Support: Enabled
TrueType Linkage: with freetype

---

