---
title: "Compiz pygtk problems"
date: 2007-12-01
forum: Desktop Environments
---

### Post by tpariel on 2007-12-01
hi all,

I just upgraded to Gutsy and I was trying to install the Compiz. Every thing seems to be ok until I tried to run the ccsm and I got the following message:
 
talavera@talavera-laptop1:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 24, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
ImportError: /usr/lib/libcairo.so.2: symbol png_set_expand_gray_1_2_4_to_8, version PNG12_0 not defined in file libpng12.so.0 with link time reference

After some walking around the problem and by coincidence I ran the pygtk-demo command and I got exactly the same error.

Please, could you help me with this? I do not what else to do](*,)

---

### Post by liquid on 2007-12-30
are you still having this problem?

---

