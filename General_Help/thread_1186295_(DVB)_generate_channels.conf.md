---
title: "(DVB) generate channels.conf"
date: 2009-06-13
forum: General Help
---

### Post by davidtuti on 2009-06-13
Hi,

I try to generate the file channels.conf but I can't

I do:

```

sudo apt-get install dvb-utils 

scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/es-ChosenDataFile > channels.conf
scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/es-ChosenDataFile
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
ERROR: cannot open '/usr/share/doc/dvb-utils/examples/scan/dvb-t/es-ChosenDataFile': 2 No such file or directory
ERROR: initial tuning failed
dumping lists (0 services)
Done.

```

Could youhelp me? 
Many thanks

---

### Post by Cheesemill on 2009-06-13
On my machine the data files are in a different place. I always do a:
```
scan /usr/share/dvb/dvb-t/uk-EmleyMoor > channels.conf
```

Try changing the path and see if that helps.

Cheesemill


Edit - If you hit TAB to autocomplete whilst typing in the path then you can be sure that the file exists. For example I type:
```
scan /us[TAB]sha[TAB]dv[TAB]dv[TAB]t[TAB]uk-Em[TAB] > channels.conf
```
(It looks alot more complicated that it seems)

---

### Post by lgnokia on 2009-06-13
nice information i have got from this forum thanksa lot.

---

