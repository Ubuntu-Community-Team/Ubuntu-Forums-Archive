---
title: "how to increase X11 font size?"
date: 2009-09-22
forum: Desktop Environments
---

### Post by atezatez1 on 2009-09-22
Dear All,

I have a WUXGA+ resolution screen on 15.4' laptop, which makes the font very small.

I tried to increase DPI to compensate, but this seems only work for some applications

for example, if i run R with tcl/tk GUI, the window i got is in low quality and still very very small, it seems not controlled by those DPI stuff.

Can anyone tell me how to increase the font size in that case to make them more readable?

thank you!

---

### Post by Nordfjord on 2009-09-22
For the original DPI change you used the Fonts tab in the Appearance config thingy?

Try this:

```
sudo gedit /etc/X11/xinit/xserverrc
```

and find the line that looks something like

```
exec /usr/bin/X11/X -dpi 100 -nolisten tcp
```

See if changing the -dpi variable helps.

---

