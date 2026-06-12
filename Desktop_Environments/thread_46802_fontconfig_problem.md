---
title: "fontconfig problem"
date: 2005-07-06
forum: Desktop Environments
---

### Post by soheil_has on 2005-07-06
Hi,

I have deleted my /etc/fonts/* by mistake. Then I copied the contents (fonts.conf, local.conf, conf.d, fonts.dtd) to my /etc/fonts.
But after fontconfig says: 
Fontconfig error: "conf.d", line 1: no element found

It is not even corrected using dpkg-reconfigure fontconfig

How can I solve this.

This is my /etc/fonts:

conf.d/  fonts.conf  fonts.dtd local.conf

conf.d:
30-debconf-no-bitmaps.conf  no-bitmaps.conf    sub-pixel.conf  yes-bitmaps.conf
autohint.conf               no-sub-pixel.conf  unhinted.conf

---

### Post by intangible on 2005-07-06
All I have in mine is "fonts.conf  fonts.dtd  local.conf", no conf.d, try moving that away and see what happens.

You can also try **sudo apt-get --reinstall install fontconfig**

---

### Post by andril on 2005-11-17
Whoa I got this too "Fontconfig error: "local.conf", line 1: syntax error" any help with this? The previous efforts don't work.

---

