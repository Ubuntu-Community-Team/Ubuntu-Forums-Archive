---
title: "[SOLVED] Afegir Plugins Compiz Fusion?"
date: 2008-06-22
forum: Catalan Team
---

### Post by kukat on 2008-06-22
Acabe de veure el plugin nou de Compiz: [http://dev.compiz-fusion.org/~onestone/blog/](http://dev.compiz-fusion.org/~onestone/blog/) , però no se com instal.lar-ho. Algú sap? 

Diuen: You can download it from Compiz Fusion git:
git clone git://anongit.compiz-fusion.org/fusion/plugins/stackswitch, però no se que hi ha que fer (no ho entenc...:confused:)

---

### Post by RainCT on 2008-06-23
Doncs això, escrius «git clone git://anongit.compiz-fusion.org/fusion/plugins/stackswitch» a la terminal.

---

### Post by kukat on 2008-06-23
mmm.....em diu "command not found". No se....ja ho vaig provar ahir, però....ni idea. He fet també "sudo apt-get install git" (per provar alguna cosa) però continua igual.:confused:

---

### Post by CarlesOriol on 2008-06-23
mmm... no diu sols [FONT="Courier New"]command not found[/FONT].

Exactament diu:

[FONT="Courier New"]
carles@asusx20sg:~$ git
El programa «git» no està instal·lat actualment.  [B]Podeu instal·lar-lo si escriviu:
sudo apt-get install git-core[/B]
bash: git: command not found[/FONT]

---

### Post by kukat on 2008-06-24
Ups! Doncs a mi no m'eixia això. Es que estic al Gutsy Gibbon, havia oblidat dir-ho. 
Ara mateix ho faig.

---

### Post by kukat on 2008-06-24
Gràcies, ja funciona el git. Però.....No se per què, ahir intentant instal.lar aquesta funció, vaig instalar uns quants plugins per al Compiz Fusion (vaig posar una adreça al Software Sources i després em demanava unes actualitzacions) , i ara no m'apareix la barra de tancar, maximitzar i minimitzar......QUe tinc que fer? 

No m'ix! [http://img401.imageshack.us/img401/5459/capturayd4.png](http://img401.imageshack.us/img401/5459/capturayd4.png).
I quan vaig a Sistema, Preferències,Finestres, em diu: "el gestor de finestres "compiz" no ha enregistrat cap eina de configuració". També tinc instalat el Emeral Theme Manager...però res.

Gràcies!

---

### Post by patrickfromspain on 2008-06-24
git, svn, cvs.. a vegades es jugar amb "foc". Son eines per treballar amb versions de desenvolupament del programari, i per tant hi pot haver versions que no funcionin. S'ha de tenir present.

Sobre el teu problema, prova a treure els sources que has afegit, borra tot lo de compiz i reinstal·la'l.

salut!

---

### Post by kukat on 2008-06-24
Ostres, doncs faré això. No pensava que seria perillós, però pel que veig....Estava el compiz tornant-se boig. De vegades es desactiva, o no es pot posar en mode "personalitzat"....això si, hi havia uns efectes flipants com el de les finestres en 3D..jejeje..

Gràcies! Jo crec que de moment ja podem posar SOLVED.

---

