---
title: "[SOLVED] Amarok a Gnome"
date: 2008-05-20
forum: Catalan Team
---

### Post by LitusMayol on 2008-05-20
Bones familia!

Sóc fan de l'**Amarok**.Aleshores, jo voldria posar-me'l a l'Ubuntu (fins ara a funcionat prou bé). Però em vull posar l'**Amarok-Nightly** amb el *Project Neon*([http://amarok.kde.org/](http://amarok.kde.org/)). 

La meva pregunta és, necessito o seria recomanable posar-me KDE aleshores?

Faig primer
```
$ sudo apt-get install kde
```
I després afegeixo el repositori del web ([http://amarok.kde.org/](http://amarok.kde.org/)) a la llista?


Merci!

Salut i Rock!

---

### Post by papapep on 2008-05-20
Tens present això, oi?:

> Even though we try to keep your data secure, you should be aware that Neon is providing mostly unreleased and untested software, which might as well eat your system. Neon is intended to be used by everyone who wants to help us find bugs, keep track of development, join development or just wants to live on the bleeding edge. It is not intended to be used instead of a stable and full featured Amarok.

---

### Post by RafaelCarreras on 2008-05-20
Jo me'l vaig posar per a veure què i, efectivament, és una versió pre-alfa, on no funcionen moltes coses. El primer dia ni tan sols podia sentir música. :-)
S'actualitza cada dia, et baixes uns quants megues i realment per a res, a no ser que siguis un desenvolupador del programa.

Si, tot i la mala publicitat, encara el vols provar, hauràs de tenir algunes biblioteques del KDE4, però m'imagino que el Synaptic ja les instal·larà dels repositoris normals.

---

### Post by pespin on 2008-05-20
Et recomano que facis un cop d'ull al programa **Exaile**. A grans trets ve a ser un Amarok amb les llibrerires GTK (Gnome).

---

### Post by LitusMayol on 2008-05-20
> **pespin said:**
> Et recomano que facis un cop d'ull al programa **Exaile**. A grans trets ve a ser un Amarok amb les llibrerires GTK (Gnome).

Merci **pespin**. Suposo que serà qüestió de gustos, però l'**Exaile** no m'agrada tant com l'**Amarok**. Ja l'havia probat (és molt eficient i realment s'hi assembla) i merci per la recomanació (si no l'hagués probat abans suposo que m'hauria sorprès). 

De totes maneres, suposo que perquè vaig començar amb KDE, però estic molt més avessat a l'**Amarok** i a la seva configurabilitat. Per tan, seguint amb la meva *mania*, si vull tenir l'**Amarok** (sigui quin sigui dels dos), em recomaneu que instal·li KDE? O representa que si instal·lo l'**Amarok** ja se m'instal·laràn totes les llibreries necessàries? 

(Veien com tinc l'ordinador NO em posaré l'**Amarok-Nightly**, a tot cas m'esperaré si en surt una versió estable)

---

### Post by papapep on 2008-05-20
> O representa que si instal·lo l'Amarok ja se m'instal·laràn totes les llibreries necessàries?


El sistema de gestió de paquets de Debian (Ubuntu) és una meravella. No en dubtis mai ;-) Ell farà el que calgui fer (amb la teva colaboració, clar...)

```
sudo aptitude update && sudo aptitude install amarok
```

---

### Post by MorlanXaos on 2008-05-20
Faig servir el Amarok en Gnome, des de fa unes setmanes. Amb la anterior versió del Ubuntu, 7.10, tenia alguns problemes amb la interficie, però amb el 8.04 va molt bé. No, no tinc el KDE instal.lat.

Tindràs que instal.lar la base de dades mysql, si no la tens.

---

### Post by konungursvia on 2008-05-20
I use amarok in Gnome, and find there is no problem at all. Exaile is ok, but it's hard to get the keystroke shortcuts working. Love Catalonia, by the way.

---

### Post by oriolsbd on 2008-05-21
M'agrada moltíssim l'Amarok, però vaig llegir en un article de la revista Linux+ dedicat a Amarok (abril del 2008) que tenia problemes en Gnome. No problemes grans ni molt menys, sinó alguna petita coseta d'integració amb Gnome que no acabava d'anar.

Si comenteu que no hi ha cap problema, potser me l'instal·lo. Per cert, al Rythmbox hi ha l'opció de baixar-te la lletra de la cançó que estas escoltant. Sabeu si hi ha també aquesta opció a l'Amarok? La trobo molt útil.

---

### Post by LitusMayol on 2008-05-21
Merci a tots!

de moment he fet:
```
sudo aptitude update && sudo aptitude install amarok
```

I a veure si m'assabento quan treuen el nou **Amarok** en versió estable!


Merci de nou a tots!

---

### Post by RafaelCarreras on 2008-05-21
[Aquí]("http://ljubomir.simin.googlepages.com/awn") et pots anar assabentant de les notícies de l'Amarok (en anglès).

---

### Post by menut on 2008-05-21
> **oriolsbd said:**
> al Rythmbox hi ha l'opció de baixar-te la lletra de la cançó que estas escoltant. Sabeu si hi ha també aquesta opció a l'Amarok? La trobo molt útil.

Sí. Quan tinguis la cançó sel·leccionada, vas a la pestanya "Lletres",a la part esquerra del programa i segueix les indicacions.

---

### Post by LitusMayol on 2008-05-22
Bones,
*re-obro* aquest post perquè el títol d'aquest ja em serveix. 

Torno a ser jo, per variar!
Ara el problema que tinc amb l'**Amarok** és que no em surt en català. Estic convençudíssim de que està traduït al català, però no hi ha manera. El sistema el tinc tot en català. Algú sap perquè l'**Amarok** no?


Merci

---

### Post by papapep on 2008-05-22
Si us plau, obre un fil nou específic.

---

