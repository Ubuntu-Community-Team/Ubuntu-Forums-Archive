---
title: "[SOLVED] Xubuntu+Openoofice+accents"
date: 2008-01-12
forum: Catalan Team
---

### Post by TotAmbA on 2008-01-12
Doncs bé, torno a tenir un altre petit problema amb el meu Xubuntu. No m'atrau la idea d'utilitzar l' "Abiword" i prefereixo instal.lar-me un openoffice.
He intentat instal.lar l'openoffice 2.3 mitjançant el synaptic i ho fa correctament.
L'únic problema, és que no escriu els accents.
He llegit varis post però no acabo de trobar la solució :(
No se si em falta algun paquet, és problema de configuració (tema UTF) o simplement és un bug.

A algú li ha passat?

Inicialment vaig instal.lar la versió catalana d'openoffice i els accents no s'escrivien. Vaig desintal.lar-lo i vaig buscar el paquet openoffice al synaptic, el vaig instal.lar i ara el tinc en anglès, la instal.lació tal com ve.... però tinc el mateix problema.

---

### Post by RainCT on 2008-01-13
Per tenir-lo en català n'hi ha prou amb insta&#320;lar el paquet «openoffice.org-l10n-ca» des del Synaptic.

---

### Post by TotAmbA on 2008-01-13
Si, ja ho vaig provar.
El vaig instal.lar inicialment en català i no funcionaven els accents. Vaig pensar que no fos per haver-lo instal.lat en català i llavors, vaig desintal.lar la versió catalana i vaig instal.lar la versió anglesa. El problema persisteix, però ja no se si pot ser problema de codificacio, d'idioma del xubuntu (xfce) o que em falta algun paquet important que em falta per instal.lar. 
El problema important és l'accentuació, l'idioma no em preocupa.

---

### Post by albert-I on 2008-01-13
Jo tinc el Xubuntu, natiu i tinc el Oppenoffice 2.3 amb català i no tinc aquest problema.
a suport d'idioma i tinc seleccionat *Catalan (Spain)* i tu pq hi ha catalan d'Andorra, França i fins i tot d'italia
I el problema general del Openoffice amb els accents? em ve al cap de que hi ha un error amb els accents
Me sona que es una cosa ja coneguda. Buscare una mica, em sembla que pels fils amb anglès es comentat.

I pq no t'agrada el Abiword?

---

### Post by TotAmbA on 2008-01-14
Ha costat però finalment he trobat el problema.
No em pregunteu perquè però funciona.

Procediment:
Aneu a: "aplicacions", "ajustaments", "paràmetres del teclat".
Us desplaceu fins la pestanya "Layouts".
Jo hi tinc model teclat: "Generic 105 Key".
A sota hi trobareu "keyboard Layouts".
Jo hi tenia Layout=es Variant=ca

i el que he fet és treure la variant, és a dir, que Layout=es i a Variant= "res" (sense variant).

Gràcies per les respostes.
M'he explicat molt malament, espero que s'entengui....

---

### Post by orestesmas on 2008-01-16
S'entén, però el problema és curios. Fes-me un favor: pots obrir un terminal i posar aquí la sortida de l'ordre:
```
echo $LANG
```

Gràcies.

P.D.: Vull comprovar que això dels accents no sigui una interacció rara entre una variable LANG=ca_AD i una variant del teclat "ca" (que l'única diferència que té amb el "sense ca" és la possibilitat d'obtenir mitja ela geminada amb Alt+L)

Com això: CA&#319;LIGRAFIA, ca&#320;ligrafia (observeu com la &#319;L són dos caràcters i no pas tres com en CAL·LIGRAFIA, cal·ligrafia

---

### Post by TotAmbA on 2008-01-18
A veure, el  resultat és:

ca_ES.UTF-8

Perdona el retard.... :(
Espero que et serveixi d'ajuda.

---

