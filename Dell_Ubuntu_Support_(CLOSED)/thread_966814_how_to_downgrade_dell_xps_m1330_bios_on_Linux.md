---
title: "how to downgrade dell xps m1330 bios on Linux"
date: 2008-11-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bigbrovar on 2008-11-01
my dell m1330 xps came with ubuntu preinstalled .. everything worked just fine .. even when i installed a the normal ubuntu .. the dell was also very quiet. then i upgraded to hardy (clean install) and i noticed that the dell's fan was always running i little googling suggested that the problem would be solved if i upgraded my bios so i followed this guide [http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate](http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate) and downloaded the latest dell bios for my laptop which is A13 . i installed it and i noticed that i still had the fan problem .. so i swiped out ibex and installed hardy .. but to my surprise the fan problem still persisted. so now i want to downgrade my bios to A12 since that version worked fine on hardy heron. i searched everywhere but am yet to find how this can be done on ubuntu .. most post i see online says it can only be done via windows .. but my laptop didnt come with windows what can i do :(

---

### Post by bigbrovar on 2008-11-02
i was able to downgrade my bios version on ubuntu using this command string  ```
dellBiosUpdate --override_bios_version  -u -f ./bios.hdr 
``` but even then the fan just stopped for like 5 min then continued spinning non stop again. then i switched it off and took out the battery .. same thing happened .. fan was normal for a few minute when i switched it on but it started running non stop again. am running hardy on bios version A12 .. am starting to think this is a hardware problem. maybe i should sednd it back to dell ?

---

