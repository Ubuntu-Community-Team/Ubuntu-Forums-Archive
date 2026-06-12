---
title: "Switching to k7 kernel from 386"
date: 2005-04-18
forum: Desktop Environments
---

### Post by rejser on 2005-04-18
Hi.

Installed kubunto today, former fedora and slack-user.
Everything wen't smoothly except one thing.
Trying to install k7-kernel. (1,5 Gb of ram and amd XP cpu)

Ran apt-get install linux-k7 (as root)
(dkpg: trouble handling linux-image-k7 (--configure) dependency problem, leaves unconfigured) <-- says this in every file.

The whole process ends with Sub-process /usr/bin/dkpg returned an error code (1)

Tried searching the forum but did'nt get any smarter. (bet that there are a ton of threads answering this questing though)

---

### Post by soul_rebel on 2005-04-18
```
sudo apt-get -f install
```
fixes dependency problems

---

### Post by rejser on 2005-04-18
[QUOTE=soul_rebel]```
sudo apt-get -f install
```
fixes dependency problems[/QUOTE]


Already tried that. Didn't work.....

---

### Post by soul_rebel on 2005-04-18
in this case you didn't provide enough info.

---

### Post by rejser on 2005-04-18
[I]sudo apt-get -f install linux-k7
Läser paketlistor... Färdig
Bygger beroendeträd... Färdig
linux-k7 är redan den senaste versionen.
0 uppgraderade, 0 nyinstallerade, 0 att ta bort och 1 ej uppgraderade.
5 ej helt installerade eller borttagna.
Behöver hämta 0B arkiv.
Efter uppackning kommer 0B ytterligare diskutrymme användas.
Ställer in linux-image-2.6.10-5-k7 (2.6.10-34) ...
File descriptor 3 left open
File descriptor 4 left open
File descriptor 5 left open
File descriptor 6 left open
File descriptor 7 left open
    Finding all volume groups
  No volume groups found
/usr/sbin/mkinitrd: 254:0: Cannot find LVM device
Failed to create initrd image.
dpkg: fel vid hantering av linux-image-2.6.10-5-k7 (--configure):
 underprocess post-installation script gav felkod 2
dpkg: beroendeproblem förhindrar konfigurering av linux-image-k7:
 linux-image-k7 beror på linux-image-2.6.10-5-k7, men:
  Paket linux-image-2.6.10-5-k7 är ännu ej konfigurerat.
dpkg: fel vid hantering av linux-image-k7 (--configure):
 beroendeproblem - lämnar okonfigurerad
dpkg: beroendeproblem förhindrar konfigurering av linux-restricted-modules-2.6.10-5-k7:
 linux-restricted-modules-2.6.10-5-k7 beror på linux-image-2.6.10-5-k7, men:
  Paket linux-image-2.6.10-5-k7 är ännu ej konfigurerat.
dpkg: fel vid hantering av linux-restricted-modules-2.6.10-5-k7 (--configure):
 beroendeproblem - lämnar okonfigurerad
dpkg: beroendeproblem förhindrar konfigurering av linux-restricted-modules-k7:
 linux-restricted-modules-k7 beror på linux-restricted-modules-2.6.10-5-k7, men:
  Paket linux-restricted-modules-2.6.10-5-k7 är ännu ej konfigurerat.
dpkg: fel vid hantering av linux-restricted-modules-k7 (--configure):
 beroendeproblem - lämnar okonfigurerad
dpkg: beroendeproblem förhindrar konfigurering av linux-k7:
 linux-k7 beror på linux-image-k7, men:
  Paket linux-image-k7 är ännu ej konfigurerat.
 linux-k7 beror på linux-restricted-modules-k7, men:
  Paket linux-restricted-modules-k7 är ännu ej konfigurerat.
dpkg: fel vid hantering av linux-k7 (--configure):
 beroendeproblem - lämnar okonfigurerad
Fel uppstod vid hantering:
 linux-image-2.6.10-5-k7
 linux-image-k7
 linux-restricted-modules-2.6.10-5-k7
 linux-restricted-modules-k7
 linux-k7
E: Sub-process /usr/bin/dpkg returned an error code (1)[/I]


Is what it says

---

### Post by pcaddict on 2005-04-18
try one of these:

> sudo apt-get install linux-686    (for newer Intel/AthlonXP)
sudo apt-get install linux-k7                     (for any AMD Processors)
sudo apt-get install linux-686-smp          (for Dual Intel Processors)


---

### Post by soul_rebel on 2005-04-18
it's a INITRD creation problem! related somewhat to lvm. Does this info take you any further?

---

### Post by rejser on 2005-04-18
Figured the problem somewhat, but don't know how to go further. Will continue searching.

---

### Post by soul_rebel on 2005-04-18
[QUOTE=rejser]Figured the problem somewhat, but don't know how to go further. Will continue searching.[/QUOTE]
 are you using lvm or have modified mkinitrd configuration?

---

### Post by rejser on 2005-04-18
have not modified mkinitrd.conf, have lvm, 
lvmcreate_initrd /boot/? perhaps?

---

