---
title: "not all input method shows up with update-alternative --config xinput-all_ALL"
date: 2009-10-14
forum: Desktop Environments
---

### Post by mathfeel on 2009-10-14
I want to switch on ibus for occational CJK input, but only default shows up:
```
$ sudo update-alternatives --config xinput-all_ALL

There are 3 alternatives which provide `xinput-all_ALL'.

  Selection    Alternative
-----------------------------------------------
*+        1    /etc/X11/xinit/xinput.d/default
          2    /etc/X11/xinit/xinput.d/default-xim
          3    /etc/X11/xinit/xinput.d/none

```
If I do this with zh_CN, sure:
```
$ sudo update-alternatives --config xinput-zh_CN

There are 5 alternatives which provide `xinput-zh_CN'.

  Selection    Alternative
-----------------------------------------------
*+        1    /etc/X11/xinit/xinput.d/scim-bridge
          2    /etc/X11/xinit/xinput.d/scim
          3    /etc/X11/xinit/xinput.d/scim-immodule
          4    /etc/X11/xinit/xinput.d/scim-pinyin
          5    /etc/X11/xinit/xinput.d/ibus

Press enter to keep the default[*], or type selection number: ^C
```

Does this means I have to switch my locale from en_US.utf8 to zh_CN.utf8. I certainly don't want my date format and menu show up in Chinese.

---

