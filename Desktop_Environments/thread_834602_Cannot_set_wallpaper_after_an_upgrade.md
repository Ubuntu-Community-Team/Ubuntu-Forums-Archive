---
title: "Cannot set wallpaper after an upgrade?"
date: 2008-06-19
forum: Desktop Environments
---

### Post by impact on 2008-06-19
Hello,

I have started having a problem recently after a large (cca 150MB) upgrade, I can't set any image as a desktop bacground. I can select the image but it doesn't show on the desktop. Only the solid color/gradient seems to be working. Any ideas where to look/what to look for?

---

### Post by henriquemaia on 2008-06-19
I'm having this problem too. I can't figure out why.

---

### Post by henriquemaia on 2008-06-20
Bump

---

### Post by henriquemaia on 2008-06-20
> **impact said:**
> Hello,

I have started having a problem recently after a large (cca 150MB) upgrade, I can't set any image as a desktop bacground. I can select the image but it doesn't show on the desktop. Only the solid color/gradient seems to be working. Any ideas where to look/what to look for?

I think I have found the solution. At least in my case it worked:


[LIST]
[*]open gconf-editor
[*]then go to /desktop/gnome/background
[*]and tick the option draw_background.
[/LIST]

Hope this helps you.

---

### Post by impact on 2008-06-21
Indeed it did. Perfect! :)

---

### Post by rich_biker on 2008-08-16
I dind't have a draw_background key (?!) so I created one. And it worked. Thanks for the pointer to this.

---

