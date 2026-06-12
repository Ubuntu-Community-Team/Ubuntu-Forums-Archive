---
title: "Very quick and easy optical drive question..."
date: 2009-04-26
forum: General Help
---

### Post by DracoJesi on 2009-04-26
ok, I know this is really easy but, what's the command again to show info on the optical drives?

I want to know if the DVD player in my laptop is a burner so I can make a 9.04 live cd, back up the data, and wipe the corrupted XP install off my laptop... oh and try ext4 :) Very Drive Question..

I have an 8.04 live cd, but I cool as graphics issue as couldn't run Ubunto of the cd, somekind of graphics issue as far as I can tell...

and Knoppix won't even detect my wired ethernet connection :(

---

### Post by dagrump on 2009-04-26
If you have 9.04 installed or a live ubuntu cd you could just open a terminal & use sudo lshw, I think that will tell you if it's ROM or R/W.

---

### Post by DracoJesi on 2009-04-26
thanks :)

---

### Post by DracoJesi on 2009-04-26
```
 *-cdrom
                description: DVD-RAM writer
                product: DVD RW AW-G540A
                vendor: SONY
                physical id: 0.0.0
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.W0
                serial: [SONY    DVD RW AW-G540A 1.W0 Jul03,2007
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc

```

it labels the component as cdrom, but says dvd in the description :lolflag:

since I know it plays DVD's and I see the word writer, I'd say Im good to go :)

---

### Post by dagrump on 2009-04-26
Yeah, looks like you're good to go.

---

