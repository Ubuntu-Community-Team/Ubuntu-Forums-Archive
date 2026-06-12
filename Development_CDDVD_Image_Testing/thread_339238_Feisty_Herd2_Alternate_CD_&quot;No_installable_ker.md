---
title: "Feisty Herd2 Alternate CD &quot;No installable kernel&quot;"
date: 2007-01-15
forum: Development CD/DVD Image Testing
---

### Post by cbozic on 2007-01-15
I get the following error during the "Install the base system" part of the alternate install CD: 

"No installable kernel was found in the defined APT sources. You may try to continue without a kernel, and manually install your own kernel later.  This is only recommended for experts, otherwise you will likely end up with a machine that doesn't boot."

I am installing on a Dell Latitude D820 laptop from the alternate install CD (not an OEM install).

Any thoughts or suggestions?

Thanks,
Chris Bozic

---

### Post by garybrlow on 2007-01-15
MIght be caused by a bad iso image. check the crc/MD5 of your iso image. I use Jigdo to download the image and its ok. Itried bittorent before but i get errors just like that. You can always download and intsall fiesty via repository but its been on maintenance updates right now its said to be ok on teusday or something. :)

---

### Post by Henrik on 2007-01-15
Or it might be that the daily build you downloaded has a broken kernel. What is the image ID?

---

### Post by darkninja on 2007-01-15
I'm having the same problem on my Toshiba Tecra A6 using the alternate install.

The disc passed validation, I don't know where to find the image ID but it's the one listed for Herd 2.

I downloaded it through HTTP.

---

### Post by ronacc on 2007-01-15
it is probably NOT your problem , 2.6.19 kernals have problems with ide cd/dvd drives on some mobo/chipset combos. sabayon 3.25/3.26 also with a 2.6.19 kernal also gives this problem , using a sata dvd drive cures the problem.

---

### Post by SqRt7744 on 2007-01-22
Huh, getting the same message here, MD5SUM is fine, burnt the image twice to be sure (once really slowly).  Herd 1 worked fine.  also, I don't think it's a 2.6.19 kernel problem since Herd2 uses 2.6.20 anyway.  The DVD drive in this thing *is* SATA.

Lenovo 3000 N100

Ah well, wait for herd 3 I guess.

---

### Post by cjwatson on 2007-01-24
This is [https://launchpad.net/bugs/79109](https://launchpad.net/bugs/79109), since fixed; Herd 3 will have the fix.

---

