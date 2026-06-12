---
title: "Help please, how can I set different hintstyle?"
date: 2007-10-31
forum: Desktop Environments
---

### Post by portis on 2007-10-31
I've searched in the forum, but get no results.

I use two kinds of fonts, the CJK fonts and the western fonts. For the CJK fonts, I want the hintstyle to be hintfull, but for the other fonts, I wish the hintstyle to be hintslight.
I've made changes to set different hintstyles for these two kinds of fonts through fontconfig. 

The problem is, all the qt programs work fine, but the gtk programs use hintfull for all the fonts. I've searched for quite a while. It seems that qt directly uses the configurations of fontconfig. However, gtk looks for the configs of xft first (I'm not sure).
xrdb -query shows that Xft.hintstyle is hintfull. I think this is affected by the settings of gnome environment.

So how can I set different hintstyles for these two sorts of fonts? Any help would be appreciated. Thank you all.

---

### Post by portis on 2007-10-31
I've solved!

It's a bug of libcairo.

apt-build source libcairo2, find the file cairo-ft-font.c and function _cairo_ft_options_merge, comment  if (options->base.hint_style == CAIRO_HINT_STYLE_DEFAULT)

rebuild and install. All the gtk programs now work fine.

---

