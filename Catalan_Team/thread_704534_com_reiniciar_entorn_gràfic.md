---
title: "com reiniciar entorn gràfic?"
date: 2008-02-22
forum: Catalan Team
---

### Post by climent on 2008-02-22
Tinc un disc dur extern USB que sovint em fa la punyeta (estic esbrinant si és degut a que va a USB 2.0 i l'ordinador té USB 1.0). Però aquest no és el tema. La cosa és que de tant en tant no puc accedir-hi, ni a aquest disc ni al disc intern de l'ordinador (carpetes, documents, el meu /home, etc) i com que no puc ni desmuntar, he de reiniciar totalment l'ordinador per poder seguir treballant amb ell. He d'advertir que tot això és a nivell gràfic, doncs per terminal sí que puc accedir.
La pregunta seria: hi ha algun ordre o drecera de teclat que em permeti reiniciar l'entorn gràfic sense haver d'apagar-engegar?

---

### Post by papapep on 2008-02-22
La combinació Ctrl+Alt+Tecla enrera (normalment sobre l'Intro) fa aquesta funció.

---

### Post by guillemsola on 2008-02-22
Crec que si l'anterior no et serveix a mi a vegades em fa la feina 

killall nautilus

a10!

---

### Post by albert-I on 2008-02-23
Suposo que estem parlant d'Ubuntu?
amb Killall sols mates aquest programa. Jo i ara no en tinc ganes de reiniciar, pero es control+alt+ESC, n'hi ha un que serveix per matar programes i l'altre per reiniciar.

> **angrychai said:**
> Crec que si l'anterior no et serveix a mi a vegades em fa la feina 

killall nautilus

a10!

---

### Post by papapep on 2008-02-23
Ei! no emboliquem la troca que els novells entendran la "llé" per la "bé":

- les ordres de terminal kill, killall, etc., maten els processos (programes en execució) a diferents nivells, però no sempre és el recomanable.

- Ctrl+Alt+Esc: invoca el "matador" de processos (com el kill i killall) en entorn gràfic.

- Ctrl+Alt+Tecla enrera: reinicia el servidor, i sessió, gràfic.

---

### Post by patrickfromspain on 2008-02-23
sudo /etc/init.d/gdm restart també serveix

---

### Post by climent on 2008-02-25
Gràcies a tothom. Però ctrl + alt + tecla enrera em reinicia tota tota la màquina. Tanmateix, esperaré a comprar un adaptador pcmcia amb sortides USB 2.0 a veure si milloro l'accés a aquest disc dur USB.

---

### Post by papapep on 2008-02-25
Climent, o t'equivoques de tecla o el teu sistema funciona malament.

Reiniciar la màquina ho fa Alt+Ctrl+Supr, però Alt+Ctrl+Tecla Enrera _només_ ha de reiniciar el servidor gràfic.

---

### Post by climent on 2008-02-26
Ep, Papapep! Sí, estava confós. Amb les ctrl+alt+supr amb surt la finestra de diàleg per triar aturar, reiniciar, hivernar, etc, i amb les ctrl+alt+tecla enrere no em reinicia totalment, el que en sortir-me altra vegada l'inici de sessió (usuari i clau) doncs em feia la sensació que sí. Efectivament, el que faig és iniciar de nou l'entorn gràfic.

---

### Post by niculau on 2008-02-26
a mi la funció Ctrl+Alt+Esc no em fa res, tampoc Ctrl+Alt+Supr, però si em funciona el reinici de l'entorn gràfic, com pot ser?

---

### Post by cortsenc on 2008-02-28
Niculau, amb quin Supr ho fas?
Si apretes un que te dues opcions per apretar (Exemple, Bloq Num) assegurat que esta tot com ha d'estar.

---

### Post by niculau on 2008-02-28
no funciona cap dels 2 botons supr, el teclat numeric funciona i tampoc funciona el Ctrl+alt+esc i esc nomes n'hi ha un.

---

### Post by CarlesOriol on 2008-02-29
Ctrl + Alt + Esc es cosa de KDE.

Els usuaris de gnome no les fan aquestes coses.

---

### Post by papapep on 2008-02-29
Becs!!! Caca, caca!!!!

---

### Post by niculau on 2008-02-29
ara si que no entenc res, en quin moment em canviat d'entorn d'escriptori? m'he perdut.
be de totes maneres, sembla ser que per gnome nomes hi ha el reinici del entorn no? deixem-ho aquí.

---

