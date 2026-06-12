---
title: "Ubunutu Install on my laptop"
date: 2006-10-03
forum: Desktop Environments
---

### Post by raghav2999 on 2006-10-03
Hi,
Downloaded 680MB of ubuntu desktop version and burnt he iso image onto a CD. Now am not able to boot from the CD at all!!!

Laptop: Preasrio v3000
HDD - SATA (have disable SATA in the BIOS).
CD only has the iso image
Please help.

Regds,
Raghav

---

### Post by Schalken on 2006-10-03
A common mistake is to burn the actual iso file to the cd as a file. You need to make sure that you are telling your CD burning software to 'burn a cd using this iso'. An iso is an exact replication of a CD, and needs to be burnt as such.

Another problem could be that your BIOS isn't looking a boot CD. Check for evidence of the computer attempting to boot off the CD, such as it saying "Boot from CD/DVD:" before it starts your OS.

If not, go into your BIOS setup screen, normally by pressing <Del> or <F8> as the computer boots, and select 'Advanced BIOS configuration' and set the first boot device to 'Floppy', the second to 'CD/DVD' and the third to 'HDD'. Now it will look for a boot CD before reverting to the HDD.

Also, there is no need to enable/disable SATA to boot from the CD.

---

