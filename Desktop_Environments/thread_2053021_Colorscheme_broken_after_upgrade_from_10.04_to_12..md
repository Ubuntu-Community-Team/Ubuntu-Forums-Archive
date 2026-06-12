---
title: "Colorscheme broken after upgrade from 10.04 to 12.04"
date: 2012-09-04
forum: Desktop Environments
---

### Post by neobusy on 2012-09-04
Hello everyone,

I have recently upgraded from xubuntu 10.04 to 12.04, while my basic settings still seem to work I noticed something fishy with the colorscheme. I didn't like the scheme which came with 12.04 so I chose the 10.04 default again, which is called Albatross under Appearance in the Settings Manager.

However I keep getting these odd combinations of white text on white background, could anyone point me to a config file or a directory I either have to delete or check/fix the setting to get to this problem? 

Thank you very much, I have attached 2 samples of the problem.

---

### Post by mcduck on 2012-09-04
Most likely the theme you are using isn't compatible with the latest version of GTK used on 12.04, and that's causing your problems. In that case the only options would be switching to another theme, or trying to find if somebody has updated the old theme for new GTK version. (or third option, learn some GTK theming and see if you can make the necessary changes yourself ;))

---

### Post by neobusy on 2012-09-21
I solved the issue by downloading the current version of the theme which can be found at [https://github.com/shimmerproject/Albatross](https://github.com/shimmerproject/Albatross)

Then placing it into /usr/share/themes

:KS

---

