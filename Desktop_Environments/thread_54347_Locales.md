---
title: "Locales"
date: 2005-08-04
forum: Desktop Environments
---

### Post by BanskuZ on 2005-08-04
I will get "Missing fi.FI_UTF8, using system default" message when GNOME starts. It's pretty annoying.  :-x 

Do I have to reinstall Ubuntu?

(Using Ubuntu 5.04)

Edit: I reinstalled Ubuntu.

---

### Post by heimo on 2005-08-04
Try reconfiguring locales:
sudo dpkg-reconfigure locales

I'm not sure if that's going to help - personally I use en_US.UTF-8, but Finnish keyboard layout.

---

