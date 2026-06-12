---
title: "Nou sistema operatiu"
date: 2008-09-04
forum: Catalan Team
---

### Post by lFossil on 2008-09-04
Bones, m'agradaria saber si podria instal·lar-hi un nou sistema operatiu al portàtil però compartint l'ubuntu clar.
La cosa és instal·lar-lo a un sistema on només existeix l'ubuntu.
M'han comentat que és una tasca difícil però que es pot fer,
algú em pot tirar un cable?
Merci per endavant!!
:lolflag:

---

### Post by tanreb20 on 2008-09-04
Home...

Jo crec que tots els SO?s porten el seu sistema de particionament i fan el procés de manera automatica. Sino fes servir el particionador de ubuntu.

$ sudo gparted

---

### Post by pespin on 2008-09-04
Instal·lar altres sistemes operatius en un ordinador que ja tens Ubuntu no és molt complicat (el que ho pot fer complicat és la instal·lació de l'altre sistema operatiu en si).

Jo el que faria segurament seria:
1- gparted -> crear una partició nova on posar el nou sistema operatiu
2- Instal·lar el nou sistema operatiu
3- LiveCD -> Si la instal·lació és carrega el grub i llavors no pots entrar a l'ubuntu, utilitza un LiveCD per tornar a instal·lar el grub.

---

### Post by LitusMayol on 2008-09-05
Jo vaig fer exactament el que diu en **pespin**. 

Tan el **Windows** com el **Leopard** donen per sentats que seran l'únic OS de l'equip i formategen tota la partició que els assignes. Amb el **Gparted** fas la partició on vols instal·lar l'altre OS i ja està! ;)



(De fet a mi no em va ni petar el grub)

---

### Post by lFossil on 2008-09-21
Però si faig això que diu amb el gparted només formatejarà el que li especifiqui no?
No li passarà res a l'ubuntu oi?

---

### Post by kukat on 2008-09-22
mmm....si ho fas bé no. I si et "desapareix" el grub, també pots utilitzar el Super Grub Disk (que està en català també!) per a recuperar el GRUB!! jo el gaste i em funciona!!!
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

