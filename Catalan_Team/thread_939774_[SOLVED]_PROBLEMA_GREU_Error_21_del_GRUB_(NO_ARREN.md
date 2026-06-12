---
title: "[SOLVED] PROBLEMA GREU: Error 21 del GRUB (NO ARRENCA)"
date: 2008-10-06
forum: Catalan Team
---

### Post by LitusMayol on 2008-10-06
Bones.

Escolteu, acabo d'encendre l'ordinador i no ha carregat. Mentre esta carregant arriba a una linia que diu una cosa així com "*Grub Stage 1.5*" (més o menys) i després em diu "*Error 21*". I prou. Premi el que premi, faci el que faci: allí es queda. 

He indagat una mica (vaja: "*error 21 ubuntu grub*" al Google, no us penseu). Tot el que he vist acaba reinstal·lant el GRUB. Per això prefereixo pregunatar-ho al LoCo, crec que tinc un bon anglès, però parlant d'una cosa greu passo d'arriscar-me si tinc una opció en català. (Sinó ja seria una altra cosa i m'arriscaria a perdre-ho tot)

Per a més curiositat, molts dels resultats de la cerca del buscador són relacionats amb el fet d'instal·lar **Ubuntu**  en un Pendrive (cosa que fa res que he fet jo -[veure el post]("http://ubuntuforums.org/showthread.php?t=937046")-). No descarto que sigui el cupable, doncs ahir a la nit vaig probar si anava, vaig experimentar el problema que exposo en el post #6 del fil, vaig reiniciar i vaig escriure el post #6. La següent vegada que l'he encés ja tenia el problema.



Crec que el que ha passat (ATENCIÓ AIXÒ TAMBÉ POT SER UNA PEDRADA) és que a l'instal·lar ** Ubuntu** al Pendrive vaig instal·lar el grub allà, fent que el grub que jo tenia a la partició quedés desautoritzat (com si hagues instal·lat **Ubuntu** a una tercera partició de l'ordinador i per tan ara fos la prioritaria). Per tan ara he de provar d'arrencar amb el pen a veure si arrenca (penjo el post i ho provo... es que se m'està acudint a mesura que escric i penso quin potser el problema)


Que faig?
Ara intento confirmar la meva teoria del pen.



(Sort que sempre tinc a mà alguna Live.)

---

### Post by LitusMayol on 2008-10-06
Comfirmat.


El problema (ERROR 21) vol dir que no té grub. He entrat desde un Live cd al *menu.list* del pendrive. He canviat el *timeout* a 10 segons (per tenir temps d'escollir) i en efecte: ara sóc a la meva sessió normal. (deunidó quin sistema de seguretat! Si en una instal·lació li dius que el */grub* el posi a un pendrive, l'ordinador no es pot arrencar sense aquest! Que boo!)

Per tan ara he de tornar-li ha dir que el grub que vull és el de la partició d'**UbuntuStudio** (em sembla que és sda2 o 3...)


Algú m'ajuda a reinstal·lar(redefinir on està) el GRUB?

Merci

---

### Post by kukat on 2008-10-06
has provat de fer servir el Super Grub Disk?????
A part de ocupar res i poder gravar-lo de seguida (si tens altra partició amb windows per exemple) està en Català!!!!
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

A mi sempre m'ha funcionat quan se m'ha espatllat el Grub
Salutacions!

---

### Post by LitusMayol on 2008-10-06
No no. Ja està.

He carregat l'**Ubuntu** de la partició *sda2* a través del pendrive i allí he executat:
```
sudo grub-install
``` 

I he seguit el manual que hi ha a: [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)


Ja està! ;) 

Merci de totes maneres

---

