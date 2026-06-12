---
title: "Aanmeld probleem, na wijziging wachtwoord via Grub (root terminal)"
date: 2018-08-07
forum: Desktop Environments
---

### Post by sudenna on 2018-08-07
Hey

Ik heb een probleem met mijn Ubuntu 14.04 installatie.
Ik was het paswoord vergeten.
En heb via verschillende site's gevonden, voor het wijzigen van dit via root terminal (via Grub bij het opstarten).
[https://youtu.be/qGpvCZO2oOc](https://youtu.be/qGpvCZO2oOc)
Opstarten in Recovery modus.
Dan "Root" kiezen in het verschenen venster.
En dan volgende in de terminal in voeren.

mount -n -o remount,rw /
passwd "login naam"
"Nieuw wachtwoord"
"Nieuw wachtwoord herhalen"
reboot

Dit werkte perfect.
Want bij het login scherm, aanziet die het nieuwe paswoord, als het juiste (elk ander geeft die aan als een verkeerd).
Maar een paar seconde verder vlieg ik terug op het aanmeldscherm.

Heb ik mss een verkeerde terminal handeling gedaan?

Vriendelijke groeten
Ruben

---

