---
title: "Getting `top` running as a screensaver"
date: 2013-04-11
forum: Desktop Environments
---

### Post by yizrahomme on 2013-04-11
Hi,
This probably exists somewhere, but for obvious reasons, the word 'top' seems to skew the results in search engines.

Does there exist the possibility of having a screensaver which displays the output of 'top' (or a similar command)?

Thanks.

---

### Post by zombifier25 on 2013-04-11
Open the file .xscreensaver (a hidden file in your home folder), scroll down the bottom of the screensaver list (lines that ends with \n\) then add this entry:
```
xterm -fullscreen top                       \n\
```
Then open xscreensaver's config and enable the screensaver "xterm".

This also works with any command.

---

