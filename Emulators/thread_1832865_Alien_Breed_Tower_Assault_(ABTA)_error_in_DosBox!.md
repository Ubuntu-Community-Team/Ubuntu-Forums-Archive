---
title: "Alien Breed: Tower Assault (ABTA) error in DosBox!"
date: 2011-08-25
forum: Emulators
---

### Post by Rytron on 2011-08-25
Hi.

I get this error in Alien Breed: Tower Assault [image attached].
How can I solve this? Other games work fine in DosBox.

---

### Post by 8bitBloat on 2012-01-12
Sorry for necroing, but it can help to change reported version to 6.00 ("ver 6.00" command in DOSbox itself), AND disable sound in install.exe
... I just discovered Alien Breed. Running Windows 7 myself.

---

### Post by Rytron on 2012-01-12
> **8bitBloat said:**
> Sorry for necroing, but it can help to change reported version to 6.00 ("ver 6.00" command in DOSbox itself), AND disable sound in install.exe
... I just discovered Alien Breed. Running Windows 7 myself.

No apology needed. Thanks for the tip. ;-)

Could you elaborate on "...**but it can help to change reported version to 6.00 ("ver 6.00" command in DOSbox itself)**..."

---

### Post by zirkoni on 2012-01-16
> **Rytron said:**
> How can I solve this?
Only way I can re-produce the error is to set xms to false in dosbox configuration.
Check that xms=true in dosbox.conf (or run mem command in dosbox command prompt).

Also, the game seems to crash dosbox-0.74 but it runs without problems in older releases. Use dosbox-0.73 to play this game.

---

