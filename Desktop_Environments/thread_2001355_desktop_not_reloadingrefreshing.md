---
title: "desktop not reloading/refreshing"
date: 2012-06-10
forum: Desktop Environments
---

### Post by wabbalee on 2012-06-10
hello,

running xubuntu 11.04 natty on toshiba tecra m9 intel graphics, since a week or so the desktop image has dissapeared. my desktop and icons do not reload either. all apps seem to run fine as usual. I have been unable to find a fix for it. 

there is another problem with Xfce that removes the borders every once in a while upon boot, but that is easy 'fixed' with:

```
xfwm4 --replace

```

and not really a problem, I know that one has been around for ages (for me any how, regardless my system)

but if any one has bumped into this desktop-not-wanting-to-reload issue and found a fix or workaround, I am all 'ears'.

thank you

---

### Post by Toz on 2012-06-10
Double-check to see if xfdesktop is running. If not, fire it up with:
```
xfdesktop
```

---

### Post by wabbalee on 2012-06-10
Thanks mate, that fixed it! that's quick! now I will go search on how to make this thread get the [SOLVED] marking as I can't see it right here.

---

