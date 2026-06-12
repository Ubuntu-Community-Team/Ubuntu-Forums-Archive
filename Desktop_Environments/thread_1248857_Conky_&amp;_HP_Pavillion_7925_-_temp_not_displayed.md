---
title: "Conky &amp; HP Pavillion 7925 - temp not displayed"
date: 2009-08-24
forum: Desktop Environments
---

### Post by SuaSwe on 2009-08-24
Hello all!

I've been trying to set up Conky for a mate and managed almost completely, however I've fallen over on the issue of core temp.

On my Packard Bell laptop, the relevant line looks like this:

$alignr temp: ${color #FFFFFF}${acpitemp}${color0}°C 

... and works fine. On his, it simply displays '0°C'. Online tips seem to be suggesting {acpitemp}, but I assume something different is required for this particular machine? It's on an Intel Celeron 1.2 GHz processor.

---

### Post by SuaSwe on 2009-08-25
B to the U to the M to the P, y'all!

---

### Post by tgeer43 on 2009-08-25
Yeah, acpitemp doesn't work on my HP notebook either. Instead I used:
```
CPU Core Temperature: ${hwmon tempf 1}°F
```But to get that working you must have lm-sensors installed and properly configured. See this link for instructions:

[http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

It looks like a lot of work but it's actually quite simple and takes only a few minutes to do.

Good luck,

tgeer

---

### Post by SuaSwe on 2009-08-26
Good tip! Will it still apply with a desktop, I wonder? Either way, I'll definitely have a go of it.

---

