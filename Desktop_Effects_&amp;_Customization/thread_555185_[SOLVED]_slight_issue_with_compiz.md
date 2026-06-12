---
title: "[SOLVED] slight issue with compiz"
date: 2007-09-19
forum: Desktop Effects &amp; Customization
---

### Post by HokeyFry on 2007-09-19
hi, i just installed compiz on my laptop earlier today, had no problems, except i just tried to run conky alongside it and it crashed. i uninstalled conky, and everything loads fine again, except that i dont seem to have a window manager anymore? what i mean is, for example, that i can no longer drag windows by the top of them, because there is nothing to drag. is this a known bug or does anyone know how to fix it?

thanks in advance

---

### Post by HokeyFry on 2007-09-19
i fixed it, i guess when i start compiz next time i should start compiz and emerald in different lines haha


if anyone else has this same problem though heres the solution i used

```

compiz --replace
emerald --replace
```

my mistake was that i strung the two together with this : &&

apparently its not a good idea

hope this helps someone

rock on:guitar:

---

