---
title: "[SOLVED] No puc entrar a Ubuntu. Ajuda, per favor"
date: 2008-11-26
forum: Catalan Team
---

### Post by Cento on 2008-11-26
No puc entrar a Ubuntu, quan el sistema s'inicia em surt una pantalla que diu:

Language es_AD does not exist; using System default

Quan faig OK a aquesta pantalla, se'm queda el fons de pantalla d'ubuntu però sense opció a fer res.

Açò m'ha ocorregut a partir d'eliminar una instal·lació de l'openoffice 3 en català que em donava problemes. Ho vaig fer des del synaptic i vaig seleccionar tot allò que feia referència a l'oo3. Probablement, vaig eliminar més coses del que calia perquè quan he reiniciat el sistema ja no ha respost.

He intentat reinstal·lar els paquets d'idioma en català a partir del reinici de l'ordinador amb l'opció recovery mode però després d'instal·lar-los, arribe al mateix lloc.

Algú em pot donar alguna idea? Moltes gràcies

---

### Post by TFX360 on 2008-11-26
I believe this is a English forum. I really have no idea what you just typed.

---

### Post by Sef on 2008-11-26
> I believe this is a English forum. I really have no idea what you just typed.


Since the OP's post is under International LoCo Teams > Catalan Team, it is fine for the OP to use Catalan.

---

### Post by TFX360 on 2008-11-26
Thanks, I'll keep that in mind!

---

### Post by TFX360 on 2008-11-26
If I understand correctly you want language support. If you start Synaptic System -> Administration -> Synaptec Package Manager and search for the language you are looking for and install that package I think you're good on your way!

---

### Post by papapep on 2008-11-26
Jo provaria passant a un tty (terminal) quan quedes amb la pantalla aquesta, fent Alt+F1 (per exemple, però podries fer-ho amb les tecles de funció fins a F5).
Un cop allà, entres com el teu usuari normal i fas:

```
sudo apt-get -f install
```

a veure si tens dependències trencades de paquets. 
Un cop hagi acabat el que sigui, reinicia l'ordinador a veure què fa.

---

### Post by Cento on 2008-11-26
Ja em pensava que m'havia equivocat de fòrum!


Papapep,

ja he fet això que em dius mitjançant el recovery mode, perquè una vegada em surt la pantalla, ja no hi ha forma de fer res (ni amb alt F1 ni amb cap tecla)

Tinc un portàtil amb la mateixa configuració i estic comparant què tinc de diferent que puga haver esborrat però no sé com copiar-ho al disc dur. Quan arrenco amb un Live, no em deixa gravar res al disc dur. Algú en sap?

---

### Post by Cento on 2008-11-26
Bé, ja he trobat com escriure al disc dur des de Live:

sudo nautilus

Però no sé quines coses hauria de restaurar (aprofitant el que tinc al portàtil) per solucinar el problema, que continua igual.

---

### Post by papapep on 2008-11-26
Fes un:

```
sudo aptitude update
```

i quan estigui

```
sudo aptitude safe-upgrade
```

Si així tampoc reacciona (després d'acabar el procés i reiniciar l'ordinador), pots agafar la llista de paquets del que et funciona correctament fent:

```
sudo dpkg --get-selections >selections.txt 
```

en el fitxer selections.txt tindràs la llista de paquets instal·lats, el copies al disc del que et porta problemes i fas:

```
sudo dpkg --set-selections < selections.txt 
```

un cop fet això, tornes a fer l'aptitude update i safe-upgrade del principi, reinicies de nou i a veure què.

---

### Post by Cento on 2008-11-27
Gràcies, papapep,ja he fet tot el que em dius, però em trobe al mateix lloc: l'ubuntu sembla que arrenca, apareix el rellotget durant unes mil·lèsimes de segon com que està a punt de sortir l'escriptori -fins i tot hi apareix el color de fons- i surt la punyetera finestra amb un senyal de prohibit que diu "La llengua ca_AD no existeix, s'emprarà Valor per defecte del sistema" (ja no sé ni com, però he aconseguit que em surta en català)

Quan li faig "D'acord", se'm queda el fons color salmó i sols hi puc fer una cosa: moure el ratolí o, si prem la tecla d'impressió de pantalla em permet desar la captura de pantalla a qualsevol lloc del disc: puc navegar pel disc dur o les usb sense problema. Però cap tecla ni combinació de tecles respon ni puc fer res més.

A veure si algú encara em pot donar alguna idea abans de decidir reinstal·lar.

---

### Post by papapep on 2008-11-27
Si fas un 

```
echo $LANG
```

i 

```
echo $LC_ALL
```

què et surt?

---

### Post by papapep on 2008-11-27
Si fas un 

```
echo $LANG
```

i 

```
echo $LC_ALL
```

i

```
cat /etc/environment
```

què et surt?

---

### Post by Diegstroyer on 2008-11-28
Proba de fer en terminal la reinstalació de l'openoffice amb aptitude en contes d'apt-get.

Salutacions.

---

### Post by Cento on 2008-12-02
Papapep,
en els dos primers casos que em suggereixes, no apareix cap resposta. Al tercer, surt açò:
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANGUAGE="ca_AD:ca"
LANG="ca_AD.UTF-8"

Diegstroyer,
no sé com es fa això que em dius: quina seria l'ordre exactament per a reinstal·lar l'openoffice amb aptitude?

Moltes gràcies a tots dos

---

### Post by papapep on 2008-12-02
Canvia el:

> LANGUAGE="ca_AD:ca"
LANG="ca_AD.UTF-8"

per:

```
LANGUAGE="ca_ES:ca:en_GB:en"
LANG="ca_ES.UTF-8"
```

la resta del fitxer deixa'l igual.

Ja és un clàssic del fòrum que el ca_AD porta problemes. Després reinicia i a veure què tal.

---

### Post by Cento on 2008-12-02
Amb el que em dius, he aconseguit que desaparega el missatge del ca_AD, i passe directament a la pantalla en blanc (en color salmó, més bé) sense accés a cap menú ni cap icona.
Fent CTRL-ALT-Retrocés (aprés en aquest fòrum!), puc arribar a la pantalla d'inici i, si li dic d'entrar amb GNOME a prova de fallades em diu 

"No s'ha trobat la instal·lació del GNOME, es provarà d'executar la sessió "xtrem a prova de fallades"

Aleshores apareix un terminal, que em permet, mitjançant nautilus, accedir al disc dur i veure el meu fons d'escriptori, però no els menús. Em permet navegar pel disc dur fins que finalment es bloqueja (només intente entrar a un usb)
Puc reinstal·lar el gnome sense perdre res? Hi ha una altra forma?

Moltes gràcies de nou!

---

### Post by papapep on 2008-12-02
Amb un:

```
sudo aptitude install ubuntu-desktop
```

què et diu?

---

### Post by Cento on 2008-12-02
Ara sí!
Ja he retornat al meu escriptori i crec que no s'ha produït cap pèrdua.

Moltíssimes gràcies

---

