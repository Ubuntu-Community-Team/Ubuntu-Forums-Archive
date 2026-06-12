---
title: "Gparted Veersion 1.3  (capable of formating ExFAT)"
date: 2022-11-03
forum: Desktop Environments
---

### Post by lazlo-lebrun-q on 2022-11-03
[FONT=arial]Hi,

Gparted seems to exist in a version 1.3 that is capable of formatting ExFat.
Unfortunately [/FONT]
[FONT=system]sudo apt-get install gparted[/FONT]

[FONT=arial]installs only Version 1.0 that cannot format ExFat.

[/FONT][FONT=system]gparted.org[/FONT] [FONT=arial]lists only an iso, containing V1.3.[/FONT]

[FONT=arial]does someone have a link to a .deb that installs V1.3?
Thank you.[/FONT]

---

### Post by Bashing-om on 2022-11-03
lazlo-lebrun-q; Hello

gparted version 1.3 is available in our release 22.04
> 
sysop@x2204mini:~$ apt list gparted
Listing... Done
gparted/jammy 1.3.1-1ubuntu1 amd64
sysop@x2204mini:~$ 


As it is bad form to have the utility also on an installed system; May I suggest that you burn a 22.04 ISO and run gparted from the resulting live image ? - the live image contains the utility.

[INDENT]where there is a will --- there is a way
[/INDENT]

---

### Post by speartip on 2022-11-05
Alternatively GParted 1.4 has now been released. Burn to CD/USB & boot from it.
[https://distrowatch.com/?newsid=11663](https://distrowatch.com/?newsid=11663)

---

