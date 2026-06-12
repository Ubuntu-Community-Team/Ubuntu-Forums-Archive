---
title: "Actualització a 8.04 a mitges"
date: 2008-05-25
forum: Catalan Team
---

### Post by jutipiris on 2008-05-25
He començat el procés d'**actualització de la versió 7.10 d'Ubuntu a la 8.04**. L'ordinador s'ha penjat una vegada i quan l'he reiniciat ja s'havia baixat tots els paquets i els estava instal·lant o actualitzant. Li he dit que continués el procés, però s'ha tornat penjar.

Una vegada l'he tornat reiniciar l'escriptori **s'ha quedat en blanc** (sense icones ni barres; amb el color del fons d'escriptori), i per tant sense poder fer res.

L'he hagut de reiniciar en mode **GNOME a prova de fallades**. Es deu haver quedat instal·lant a mitges un paquet perquè tant el synaptic com el terminal em diuen que faci: **sudo dpkg --configure -a** però arriba un moment que diu el següent i l'ordinador es torna quedar penjat:

[B]S'està configurant scrollkeeper (0.3.14-15Ubuntu) ...
Rebuilding the database. This may take some time.
///usr/share/gnome/help/blackjack/el/blackjack.xml: 402: parser error : Entity 'B[/B]
i més coses en lletres gregues que ja no puc tanscriure

Crec que no he perdut les dades de l'ordinador, simplement em sembla que no tinc la interfície (desktop) per poder-hi accedir. Quan s'inicia l'ordinador encara puc escollir entre obrir l'Ubuntu 7.10 o el Windows (els tinc en discos durs diferents). Què puc fer? **Com puc tornar a la versió anterior? O com puc seguir endavant?**

---

### Post by RainCT on 2008-05-26
Encén l'ordinador i quant et surti la pantalla que demana la contrasenya prem Ctrl + Alt + F1; això et deixarà en una terminal des d'on amb una mica de sort pots mirar d'acabar l'actualització.

---

### Post by lFossil on 2008-05-26
Mira't [aquest]("http://ubuntuforums.org/showthread.php?t=783458") post per què crec que et servirà, a mí em va passar el mateix
;)

---

### Post by jutipiris on 2008-05-26
RainCT, el **terminal** el puc obrir des de la pantalla de la contrassenya perquè hi ha una sessió que ho permet, o també des de la sessió **Gnome a prova de fallades** perquè és de les coses que deixa fer. **Però, i desprès què faig?**

IFossil, he fet al que a tu et van recomanar:

per **cat /etc/apt/sources.list** m'apareix
1 [http://farm3.static.flickr.com/2100/2525307808_ed352bc6fa_b.jpg](http://farm3.static.flickr.com/2100/2525307808_ed352bc6fa_b.jpg)
2 [http://farm3.static.flickr.com/2113/2525308858_8daeea0ea0_b.jpg](http://farm3.static.flickr.com/2113/2525308858_8daeea0ea0_b.jpg)
3 [http://farm3.static.flickr.com/2290/2524485135_266ce2ae92_b.jpg](http://farm3.static.flickr.com/2290/2524485135_266ce2ae92_b.jpg)

per **sudo aptitude update** m'apareix
[http://farm4.static.flickr.com/3072/2525305706_c9f0dbb411_b.jpg](http://farm4.static.flickr.com/3072/2525305706_c9f0dbb411_b.jpg)

i per **sudo aptitude safe-upgrade** m'apareix
[http://farm4.static.flickr.com/3273/2525306024_925cffc5ac_b.jpg](http://farm4.static.flickr.com/3273/2525306024_925cffc5ac_b.jpg)

potser ara em podeu ajudar millor :-/

---

### Post by patrickfromspain on 2008-05-26
llegir... nomes s'ha de llegir...

hi diu "you must manually run 'dpkg --configure -a' to correct the problem"

sudo dpkg --configure -a i a correr.

salut!

---

### Post by jutipiris on 2008-05-26
patrickfromspain, llegir... ja fa dos dies que només llegeixo el mateix:
"you must manually run 'dpkg --configure -a' to correct the problem"
ja que aquesta frase en el terminal acaba amb les lletres gregues següents i l'ordinador penjat:
[http://farm4.static.flickr.com/3273/2525306024_925cffc5ac_b.jpg](http://farm4.static.flickr.com/3273/2525306024_925cffc5ac_b.jpg)

gràcies, sé que es difícil entendre's si no es veu directament

---

### Post by papapep on 2008-05-26
El tema de les lletres gregues em té ben al·lucinat...:-D

Entenc que les proves que fas són des d'un emulador de terminal a l'entorn gràfic, oi??

Podries provar a arrencar l'ordinador sense entorn gràfic (ara no recordo com es diu l'opció al grub) i a ficar-li el **dpkg --configure -a** allà, a veure si es comporta igual....és ben curiós el que et passa.

---

### Post by jutipiris on 2008-05-26
també puc obrir únicament un terminal i escriure el mateix, però acabo igual

estic estudiant Sòcrates, però no pensava que a l'Ubuntu l'afectés per a res... :confused: (per lo de les lletres gregues?

---

### Post by papapep on 2008-05-26
Bufff, doncs no queden molts mistos per cremar...
prova amb un:

```
sudo dpkg --configure --pending
```

Després fes un:

```
sudo dpkg -f install
```

a veure com va.

---

### Post by jutipiris on 2008-05-26
després de **sudo dpkg --configure --pending** quedo igual:
[http://farm4.static.flickr.com/3274/2526061440_66e7d34059_b.jpg](http://farm4.static.flickr.com/3274/2526061440_66e7d34059_b.jpg)

i el resultat de **sudo dpkg -f install** és:
[http://farm3.static.flickr.com/2041/2526092300_968b61e2b8_b.jpg](http://farm3.static.flickr.com/2041/2526092300_968b61e2b8_b.jpg)

:(

---

### Post by papapep on 2008-05-26
No crec que funcioni, però mira, per provar....

Per cert, mal que no et consoli, no estàs sól al món...:

[http://ubuntuforums.org/showthread.php?t=764847&page=108](http://ubuntuforums.org/showthread.php?t=764847&page=108)

no ets l'únic Socràtic (in)-voluntari :-D

com a mínim això indica que no és exclusiva teva, i que quanta més gent s'hi trobi més possibilitat hi ha de trobar el fil per estirar..

---

### Post by jutipiris on 2008-05-26
i creus que puc salvar les dades que hi ha dintre de l'ordinador?

---

### Post by lluisanunez on 2008-05-28
Hola
Si tenies la teva /home en una partició a part, ja les tens salvades.
Si no, igualment, abans de reinsta&#320;lar, pots engegar des del liveCD, buscar les dades i copiar-les a un altre disc.

---

