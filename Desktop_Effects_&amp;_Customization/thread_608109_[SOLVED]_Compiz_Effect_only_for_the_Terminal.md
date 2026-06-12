---
title: "[SOLVED] Compiz Effect only for the Terminal"
date: 2007-11-09
forum: Desktop Effects &amp; Customization
---

### Post by arigram on 2007-11-09
Considering you can specify in Compiz which window types will be affected, is there a way to restrict a certain effect (like Alpha Blur) only to the Terminal window?

---

### Post by jimerickso on 2007-11-09
you could try

[http://wiki.compiz-fusion.org/WindowMatching](http://wiki.compiz-fusion.org/WindowMatching)

---

### Post by arigram on 2007-11-09
Thank you jimerickso for your prompt reply!
The very first command from the page you gave me:
```
xprop|grep WINDOW_TYPE|cut -d_ -f10
```
after selecting with the crosshair the Terminal window gave it as Normal.
And it seems I can't use the other window definitions.
Which means that unfortunately I can't restrict any effect only to
that Window. Its a pity. Since its the only one with a semi-transparent
backdrop, blurring would help the readability of the text output.
Oh, well.

---

### Post by sergeanthikel on 2007-12-09
What I did was statically set the title of my terminal to 'Terminal', and put in blur's 'window type' field:

title=Terminal

---

### Post by arigram on 2007-12-09
> **sergeanthikel said:**
> What I did was statically set the title of my terminal to 'Terminal', and put in blur's 'window type' field:

title=Terminal

That did it!
Excellent!

---

