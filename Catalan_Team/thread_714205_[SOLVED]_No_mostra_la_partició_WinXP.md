---
title: "[SOLVED] No mostra la partició WinXP"
date: 2008-03-03
forum: Catalan Team
---

### Post by Joan Marc on 2008-03-03
Avui m'he trobat que volia obrir un document que tinc a la partició del Windows, i he anat a Llocs, i m'he trobat que no hi apareixia. He anat a Ordinador, i tampoc hi apareix. He reiniciat l'ordinador unes tres vegades, i he vist que a l'arrencada, mostra dos "Fail", un és més o menys "Activating Swap" i l'altre és "Setting sensors limits".
Són greus els errors?
Hi ténen alguna cosa a veure?
Puc entrar al Win desde el terminal i buscar un arxiu que està a endinsat a Documents and Seetings?

Perdoneu l'allau de preguntes.

Gràcies!

---

### Post by patrickfromspain on 2008-03-03
has probat a reiniciar a windows i tornar a entrar a l'ubuntu? Podries probar a muntar manualment la particio:

sudo mount -t ntfs-3g /dev/sda1 /media/windows

(suposant que /dev/sda1 sigui la particio de windows i /media/windows el seu punt de muntatge)

a veure quin error et dona.

salut!

---

### Post by Joan Marc on 2008-03-03
Patrick, he provat de reiniciar el Windows i iniciar amb Ubuntu i miraculosament, l'error "Activating Swap" ha quedat OK, i la partició de Windows (sda2) ja torna a aparèixer, moltges gràcies :)
Em pots explicar, així per sobre, què vol dir això de muntar una partició, i com saber el punt de muntatge?

---

### Post by patrickfromspain on 2008-03-03
muntar una particio es "activar-la" per poder veure-hi les dades. Si entres a la teva particio veuras a la barra de direccions /media/sda2 o algo semblant. Per saber el punt de muntatge ho pots fer mirant a /etc/fstab i veient on esta assignat. Per cert, es pot canviar fàcilment.

salut!

---

### Post by Joan Marc on 2008-03-03
Gràcies, ara ja sabré què he de fer si em torna a passar.

Salutacions.

---

