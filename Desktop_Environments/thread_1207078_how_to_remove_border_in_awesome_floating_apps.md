---
title: "how to remove border in awesome floating apps"
date: 2009-07-07
forum: Desktop Environments
---

### Post by nephish on 2009-07-07
Hey all,
I am digging awesome window manager, but i cannot find the setting that will allow me to keep even the 1pixel border from being drawn around floating apps ( like term windows )

anyway, any help is appreciated.
thanks

---

### Post by demetriades on 2012-09-14
Hey there,

If you have a look in the config file for the Beautiful module (usually at /usr/share/awesome/themes/default/theme.lua), there's a setting called theme.border_width. If you set this to 0, Awesome shouldn't display any chrome surrounding your windows.

However, you many notice that there's a slight "crack" showing between windows, especially when tiled; this can be removed by adding the line "**size_hints_honor = false" **to your awful.rules.rules table in rc.lua. More info can be found at [http://awesome.naquadah.org/wiki/FAQ#How_to_remove_gaps_between_windows.3F](http://awesome.naquadah.org/wiki/FAQ#How_to_remove_gaps_between_windows.3F).

Hope this helps!

---

### Post by oldos2er on 2012-09-14
Please don't bump old threads. Closed.

---

