---
title: "Monitor hardware from command line?"
date: 2006-01-05
forum: General Help
---

### Post by joepotter on 2006-01-05
Hello all,

What would be the best way to check on the cpu's temperature from the command line?

Thanks.

---

### Post by lunatech on 2006-01-05
[QUOTE=joepotter]Hello all,

What would be the best way to check on the cpu's temperature from the command line?

Thanks.[/QUOTE]

lm-sensors - Utilities to read temperature/voltage/fan sensors

You should be able to install it using synaptic.  Though I have not used them myself

---

### Post by joepotter on 2006-01-06
[QUOTE=lunatech]lm-sensors - Utilities to read temperature/voltage/fan sensors

You should be able to install it using synaptic.  Though I have not used them myself[/QUOTE]

All that ever gives me is "no sensors found" for some reason. I have tried on three different boxes with no results.

Hmmm. Google on we do.

---

### Post by mo_x on 2006-01-06
lm-sensors need some configuration and kernel modules to be loaded. Try the command sensors-detect.

---

### Post by davinci on 2006-01-06
how about 

acpi -V

if acpi is working, of course

---

### Post by joepotter on 2006-01-07
[QUOTE=mo_x]lm-sensors need some configuration and kernel modules to be loaded. Try the command sensors-detect.[/QUOTE]



I tried all that, nothing seemed to work. I had given up; or at least put it on the back burner since I did not really care what temp the cpu was till the new one (and mb) gets here next week.

I was using Dapper at the time. I did a re-install to test the new installer and wham-o everything to do with lm-sensors started working just the way the instructions claimed they should work.

I have no idea if it was a bug, or perhaps something I had done over time.

Thanks to all for the advice.

---

