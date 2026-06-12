---
title: "xbindkeys - Hold down Control-Button"
date: 2006-03-11
forum: Desktop Environments
---

### Post by teclis on 2006-03-11
Hello,

I got my Logitech MX Laser to work. Now I will bind the following to a mouse-Button:

When I press one Mouse-Button the Ctrl-Button should be pressed and released when releasing the Mouse-Button.

How must the line in the .xbindkeys look like? OK, I got the hint to use xmodmap below.

But how does this work in detail?

Thanks
Teclis

---

### Post by kabus on 2006-03-11
"Xbindkeys is a program that grab keys and mouse button events in X and starts associated shell commands."

I think for what you want to do you'll have to use xmodmap.

---

### Post by teclis on 2006-03-11
How does this with xmodmap work?

---

### Post by kobewan on 2007-05-02
I don't think this would work with xmodmap, or at least I don't know how to do it. However, it should be possible to do with a combination of xbindkeys and xautomation. Install xbindkeys and xautomation with ```
sudo apt-get install xbindkeys xautomation
``` After you do that, create a file in your home directory called .xbindkeys, and in it put something along these lines:

```
# Volume Up button
#
# Control button down
"xte 'keydown Control_R'"
   b:13

# Volume Up button
#
# Control button up
"xte 'keyup Control_R'"
   release+b:13
``` That *should* work.

---

