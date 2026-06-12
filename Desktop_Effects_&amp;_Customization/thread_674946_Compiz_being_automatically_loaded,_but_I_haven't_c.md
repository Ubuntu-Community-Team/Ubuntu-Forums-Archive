---
title: "Compiz being automatically loaded, but I haven't called it"
date: 2008-01-22
forum: Desktop Effects &amp; Customization
---

### Post by DMurray on 2008-01-22
Hello, all.

I've installed Gutsy like a week ago and got some strange lockups after changing Appearance/Visual Effects from Normal (the default) to Extra or Custom.
That is, these last options load some more effects from Compiz, but after changing it back to Normal and restarting the PC, I still see Compiz being loaded:

```

5192 ?        S      0:00 /bin/sh /usr/bin/compiz --sm-client-id default0
 5317 ?        SL     0:01 /usr/bin/compiz.real --ignore-desktop-hints --replace --loose-binding --sm-client-id default0 ccp

```

Is it because Normal already loads it with minimum effects, so I need to go None to not have it loaded in startup?
The random lockups I referred to happen with no special action. I just noticed them happening more when alt-tabbing the programs, but are completely random. The only change I made was the visual effects for the desktop, so I initially blame Compiz.

TIA

---

### Post by john.nicholls on 2008-01-23
Yes, Normal adds some effects. You need to select None so as to have no Compiz effects.

---

