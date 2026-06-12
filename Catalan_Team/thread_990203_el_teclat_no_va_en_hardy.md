---
title: "el teclat no va en hardy"
date: 2008-11-22
forum: Catalan Team
---

### Post by trinkus on 2008-11-22
Tinc un Laptop Asus amb 7.10 i l'he actualitzat a la Hardy pero ara no em deixa escriure res dins del Gnome. Puc escriure al GDM per iniciar sessio pero en entrar despres qualsevol tecla que premo pita el teclat (i no escriu). He canviat la disposicio de teclat pero no es aixo. Com que no puc escriure no ùc actialitzar cap paquet ni res. I no se de que ve...
Algu sap quin pot ser el problema i com solucionar-lo, siusplau? Es força urgent!

Roger

---

### Post by papapep on 2008-11-22
I no has tingut cap missatge d'error ni cap problema a l'actualització??? si no ens dónes ni la més mínima pista, poc podem fer.
Prova a fer Ctrl+Alt+F1 (abans d'autentificar-te al gdm, clar) per anar a un tty i actualitzar allà amb "sudo aptitude update" i "sudo aptitude safe-upgrade", a veure si et falta algun paquet, o tens algun conflicte.

També pots provar a fer un "sudo apt-get -f install" a veure si algun paquet ha quedat a mig instal·lar ....

---

### Post by trinkus on 2008-11-22
Merci Papapep,

Ho he executat pero segueix igual. La diferencia es que ara ja no pita (simplement no escriu res) Com si no tingues teclat.

No he vist cap missatge d'erro i el fet curios es que amb la 7.10 funcionava tot perfectament, es molt estrany i no tinc ni idea que pot ser...

---

### Post by papapep on 2008-11-22
I entrant en "mode gràfic segur", et passa el mateix? no sé trobar casos semblants al teu per a la 8.04...curiós.

---

### Post by trinkus on 2008-11-23
Quan entro en mode grafic segur tampoc va (tampoc pita).
He aconseguit actualitzar a Intrepid des de consola i estem exactament igual... Es com tenir un ordinador de botiga (es mira pero no es toca) ;-)

---

### Post by trinkus on 2008-11-23
Encara mes estrany. He aconseguit instalar KDE4.1 i en entrar sessio amb KDE si que tot funciona molt be (per cert que no l'havia provat pero fa molt bona pinta). Tanmateix, el Gnome segueix igual. M'agradaria que funciones perque l'ordinador no es meu i despres fer propaganda de Ubuntu es fa dificil...

Des del KDE puc instalar i mirar paquets amb tranquilitat. Que es el que hauria de comprovar?

---

### Post by papapep on 2008-11-23
Prova a crear un nou usuari i a entrar amb aquest nou a Gnome.
També pots reinstal·lar el ubuntu-desktop (que instal·la el gnome entre moltes altres coses).

---

### Post by PatrickVogeli on 2008-11-23
mira a veure si tens instal·lat el paquet xserver-input-kbd

salut

---

### Post by trinkus on 2008-11-23
Al final he reinstalat l'Intrepid de nou (formatejant la particio) i s'ha acabat. No m'agrada haver de fer-ho pero ara estic mes tranquil. Val a dir que havia reinstalat l'ubuntu-desktop i no ha canviat el tema.... que hi farem... pero m'ha estranyat. Perque les actualitzacions almenys les que jo he fet) no van tan be com instalar el sistema net? No hauria de ser igual o millor?

---

