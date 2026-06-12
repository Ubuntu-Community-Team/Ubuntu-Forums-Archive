---
title: "[SOLVED] DeVeDe"
date: 2008-06-06
forum: Catalan Team
---

### Post by canroca on 2008-06-06
Hola;

Fins fa poc utilitzava DeVeDe però des que vaig instal·lar Hardy no arrenca l'aplicació. He vist que les dependencies de DeVeDe inclouen **MKisofs **però fent una busqueda a Synaptic no trobo MKisofs i a la llista de dependències m'apareix en cursiva que suposo que vol dir que no està instal·lat.

Còm puc fer que Synaptic em trobi aquest paquet? O hi ha alguna altra altra aplicació semblant a DeVeDe que recomeneu?

Salutacions,

---

### Post by climent on 2008-06-06
Personalment no estic molt "posat" en creació de dvd, però ho vaig cercar fa temps per a un amic, i vaig trobar el mkisofs dintre una utilitat que es diu "cdrtools" que inclou aquesta aplicació.
D'altra banda, sé que hi ha un programa que es diu DVDAuthor que sembla rutllar força bé.

---

### Post by oriolsbd on 2008-06-06
Hola.

El programa DeVeDe té un bug conegut en la traducció al català. :-(
Ho sé perquè jo mateix m'hi vaig trobar. Realment, ja s'ha arreglat en una nova traducció, però el programador no pujarà aquesta nova traducció fins que no hi hagi una nova versió de DeVeDe. De tota manera, ens deixa disponible el fitxer correcte a Launchpad:
[http://launchpadlibrarian.net/13528317/ca.mo](http://launchpadlibrarian.net/13528317/ca.mo)

L'únic que has de fer és baixar-te'l i primer desar-lo a /tmp (per exemple). Quan el tinguis, obre un terminal i executa:
sudo cp /tmp/ca.mo /usr/share/locale/ca/LC_MESSAGES/devede.mo

I ja podràs obrir el DeVeDe.

Quant al paquet mkisofs que comentes, en Ubuntu Hardy ha canviat de nom. ara es diu "genisoimage". El que passa és que no han canviat les dependències del DeVeDe...

Salut!

---

### Post by canroca on 2008-06-09
Sííííííííííííííííííííííííííííííííííííííííííííí
Gràcies company, vaig de marró en marró. Ara tinc dos de nous dels que haig de posar nous threads o sigui que aviat tornareu a saber de mi.

Salutacions,

---

