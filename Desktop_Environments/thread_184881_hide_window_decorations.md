---
title: "hide window decorations?"
date: 2006-05-30
forum: Desktop Environments
---

### Post by zacbarton on 2006-05-30
Hey

Is it possible to hide window decorations for a window? I thought there might be a setting somewhere in gconf but I could not see one.

Anyone got any ideas?

Ta

Zac

---

### Post by Ramses de Norre on 2006-05-30
I'm not sure if this is what you mean but you can enable reduced resources for metacity in ```
gconf-editor /apps/metacity/general
```

---

### Post by llamakc on 2006-05-30
Zac,

What program's decorations do you want to hide?

---

### Post by 23meg on 2006-05-30
If you're looking to do it on a per window basis check out Devil's Pie and Alltray.

---

### Post by zacbarton on 2006-05-30
I was looking to hide the decorations for the "Terminal Server Client". Im running twinview and when I do full screen it spans both displays.

I will just use "rdesktop -5 -a 8 -g 1280x1024 -r sound:off -k en-us -P **-D**" instead.

Thanks everyone for your help

Zac

---

### Post by rado_london on 2006-05-30
<sarcasm>get broken xgl/compiz and you will end up with no borders and decorations:)</sarcasm>

---

