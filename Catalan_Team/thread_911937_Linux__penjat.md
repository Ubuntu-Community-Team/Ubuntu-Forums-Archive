---
title: "Linux  penjat"
date: 2008-09-06
forum: Catalan Team
---

### Post by Carolus67 on 2008-09-06
Hola a tothom.
Fa poc que trastejo aquest sistema opretiu i ja he tingut el prmer problema, Em passa que vareig fer una actualitzacio, bastant llarga per cert. I es va va quedar com penjat i jo sense saber que fer i despres de tocar-ho gaire be tot sense gaire coneixement vaig decidir ja l´unic que podia fer, apagarlo.
A partir d´aqui ja no funciona correctament, els icones queden en alta resolucio. Poso el pasword i l´usuari i la pantalla que da amb taronja amb nomes l´aspa del cursor amb alta resolucio i res mes.
Que puc fer??
Gracies per les vostres respostes

---

### Post by patrickfromspain on 2008-09-06
un cop arrancat, fins on arribis, apreta la combinacio de tecles control+alt+F1. Pasaras a una pantalla en mode text, en plan DOS, on hauras de posar el teu nom i la teva contrasenya (quan la posis, es igual que no faci res, tu posala i apreta enter).

Llavors, alla, poses:

sudo apt-get -f install

sudo apt-get safe-upgrade

sudo apt-get dist-upgrade

Si aixo et dona qualsevol error, posa'l aqui.

Reinicia i a veure que pasa

salut

---

### Post by Carolus67 on 2008-09-06
Hola patrickfromspain gracies per el teu consell, ara em passa que puc posar l´usuari pero no el password. Teclejo pero escriu res, no se que faig malament.
Salutacions

---

### Post by lluisanunez on 2008-09-06
Sí que l'escriu, però no veus res. Entra el password i tira endavant

---

### Post by Carolus67 on 2008-09-06
Hola a tothom.
He posat aixo que m´heu sugerit i em surt el seguent:
(sudo)password for usuario:
E:dpkg was interrumped, you must manually run´dpkg--
configure-a ´to correct the problem.
usuario@usario-desktop: $
A veure que m´en podeu dir, espero aver-ho fet correctament.

Una altre cosa despres de cada sudo etc... no s´ha de premer el enter, oi? 

Gracies

---

### Post by papapep on 2008-09-06
Mira, aquí t'ho diu, el que has de fer:

> E:dpkg was interrumped, you must manually run´[B][COLOR="Red"]dpkg--
configure-a[/COLOR][/B] ´to correct the problem.

o sigui, fes a un terminal:

```
sudo dpkg --configure -a
```

I sí, al final de qualsevol ordre has de prèmer Intro per a que l'ordinador entengui que ja has acabat i vols que s'executi.. L'ordinador té molta capacitat de càlcul, però intel·ligència gens ni mica :-)

---

### Post by Carolus67 on 2008-09-07
Bon dia, e fet aixo de posar sudo dpkg--configure-a i passat el seguent.
Han sortit molts Dpkg un help, deslect o aptitude, dhelp. etc.
He reiniciat apagant i encenent l´ordinador i ha  sortit un fail en vermell, a fet molts checking drive, pero a quedat igual amb la resolucio alta.
Ho he tornat a provar i em diu orden no encontrada i em demana usuario tota l´estona.
:( Ho sento pero es que no ho fet mai aixo

Per reiniciar en dos, es control+alt+supr ?

---

### Post by patrickfromspain on 2008-09-07
en DOS si, amb contro alt supr reinicies, pero en linux no.

A veure, torna a fer el mateix. Control+Alt+F1, poses el teu usuario, apretes enter, poses la contrasenya, apretes enter encara que aparentment no escrigui res i fas:

sudo dpkg --configure -a

sudo apt-get -f install

sudo apt-get update

sudo apt-get dist-upgrade

Com ja t'han dit, despres de cada ordre d'aquestes que et poso has de pitjar enter, no posarles totes juntes. Seria bo tambe, que despres de cada ordre, t'apuntessis si et surt un missatge d'error i que hi diu, així podrem saber mes o menys que passa i a en quin punt

salut

---

### Post by Carolus67 on 2008-09-07
Salutacions
A veure aixo es el que m´ha sortit:


To access official ubuntu documentation, please visit.
http.//help ubuntu com/
usuario@usuario-desktop-$ sudo apt-get -f install
(sudo)sudo password for usuario:
E: dpkg was interrupted, you must manually run ´dpkg --configure -a´ to correct
the problem.
usuario@usuario-desktop: $ sudo apt-get safe-upgrade
E: Operacion invalida: safe-upgrade
usuario@usuario-desktop: $ usuario
-bash: usuario orden no encontrada
usuario@usuario-desktop: $ usuario
-bash: usuario orden no encontrada
usuario@usuario-desktop: $ sudo apt-get dist-upgrade
E: dpkg was interrupted, you must manually run ´dpkg --configure -a ´ to correct
the problem.
usuario@usuario-desktop: $ usuario
-bash: usuario orden no encontrada
usuario@usuario-desktop: $ usuario
-bash: usuario orden no encontrada
usuario@usuario-desktop: $ usuario


Ja al final nomes em demanave el usuario un cop i un altre.

Gracies per el vostre paciencia i suport.

---

### Post by patrickfromspain on 2008-09-07
Sembla que no ens entenem. Cito el que t'he dit:
> **patrickfromspain said:**
> A veure, torna a fer el mateix. Control+Alt+F1, poses el teu usuario, apretes enter, poses la contrasenya, apretes enter encara que aparentment no escrigui res i fas:

sudo dpkg --configure -a

sudo apt-get -f install

sudo apt-get update

sudo apt-get dist-upgrade

NO has fet el sudo dpkg --reconfigure -a, que es el mes important.

Nomes has de posar el password quan t'el demana. Perque poses usuario com a ordre? No ho entenc. A més, et diu usuario orden no encontrada: no troba aquesta ordre, perque no existeix i, per tant, no sap ni que ha de fer ni que vols fer tu. Quan et diu orden no encontrada, ja ho pots repetir els cops que vulguis: seguira sense trobar-la.

salut

---

### Post by Carolus67 on 2008-09-08
Hola patrickfromspain, he fet exactament el que m´has dit i em surt aixo:

usuario@usuario- desktop: sudo dpkg --configure -a
-(sudo) password for usuario:
-configurando locales (2.7.9-4)---
-generating locales...
en_au.utf-8... sudo apt-get -f install
-sudo apt-get upgrade
-sudo apt-get dist-upgrade



Despres provo de reiniciar amb alt+control+supr i es queda mes penjat que un xorisso, surt la barra de progres d´ubuntu pero no fa res. No el puc ni apagar.

Per cert es sudo dpkg --configure -a ho sudo dpkg --reconfigure -a ??

Salutacions

---

### Post by Frealof on 2008-09-12
Iep! Molt bones a tothom!!

Tinc poca experiència amb el tema però deixo anar un parell de cosetes que se m'acudeixen...

Va la primera... (referent a com entres les ordres)

Hi poses el guió a davant? Si es així no li posis.

Va la segona... (referent a la última ordre)

Esperes una estona a què s'hagi carregat i et torni a sortir "usuario@usuario- desktop" (sense les ") o el re-inicies amb la combinació de tecles aquesta, just després de l'ordre?

Si es el segon cas... espera a què et surti lo de "usuario@usuario- desktop" (sense les "), això voldrà dir que ha acabat el procés d'actualització.

Salut!

---

### Post by torracastanyes on 2008-09-12
D'això vam parlar-ne no fa gaire aquí:

[http://ubuntuforums.org/showthread.php?t=892519](http://ubuntuforums.org/showthread.php?t=892519)

---

