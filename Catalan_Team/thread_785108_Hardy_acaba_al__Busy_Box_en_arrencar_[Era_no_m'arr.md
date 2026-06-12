---
title: "Hardy acaba al  Busy Box en arrencar [Era: no m'arrenca ubuntu 8.04]"
date: 2008-05-07
forum: Catalan Team
---

### Post by jaumety on 2008-05-07
Hola bones,

  Al arrencar ubuntu 8.04 per primera vegada em trobo que després de tenir una bona estona la barra d'estat movent-se a dreta i esquerra, em queda la pantalla negre amb el següent missatge:

Busy Box V1.1.3 (Debian 1:1.1.3-5 ubuntu 12) Built in shell (ash)
....

(initramfs)

Gràcies.

---

### Post by menut on 2008-05-07
Sembla ser un bug:
[https://bugs.launchpad.net/ubuntu/+bug/203054]("https://bugs.launchpad.net/ubuntu/+bug/203054")

---

### Post by jaumety on 2008-05-08
I que hauria de fer?

gràcies.

---

### Post by papapep on 2008-05-08
Sembla que té bastant a veure amb els discs SATA i la seva configuració a la BIOS:[https://answers.launchpad.net/ubuntu/+question/17654](https://answers.launchpad.net/ubuntu/+question/17654)

Podries provar a canviar-ne la configuració de la BIOS, si és SATA, de AHCI a COMPATIBILITY, que sembla que hi ha una persona a la que li ha funcionat.

---

