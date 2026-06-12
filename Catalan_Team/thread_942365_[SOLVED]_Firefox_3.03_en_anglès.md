---
title: "[SOLVED] Firefox 3.03 en anglès"
date: 2008-10-09
forum: Catalan Team
---

### Post by Josep Maria on 2008-10-09
Hola, bon dia a tothom.
De cop i volta desprès de funcionar bé durant molt de temps, el firefox 3.03 se m'ha posat tot sol en anglès.
El fitxers locale.ca antics sembla que no funcionen.
He mirat el suport d'idioma i està actualitzat.
Sembla que ara hi ha uns fitxers anomenats Xulruner (ca) 1.9.0.3 però no els puc actualitzar.
Em passa només a mi o us passa també a vosaltres.
Teniu alguna idea de que puc fer per arreglar-lo?

Gràcies.

Josep Maria

---

### Post by lo gambusí on 2008-10-09
Has mirat pel synaptic si tens el paquet mozilla-firefox-locale-ca instal·lat?

---

### Post by Josep Maria on 2008-10-09
Si, ho vaig mirar i el tinc ben instal.lat.

---

### Post by jaume69 on 2008-10-09
Mira't això,**[releases.mozilla.org]("http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.3/linux-i686/xpi/")**
Si el vols en **català**,ja no ho sé...
A mi només em funciona el pack espanyol.

---

### Post by RainCT on 2008-10-09
És un problema conegut que ha aparegut fa poc...

[https://bugs.edge.launchpad.net/ubuntu/+source/firefox/+bug/280379](https://bugs.edge.launchpad.net/ubuntu/+source/firefox/+bug/280379)
[https://bugs.edge.launchpad.net/ubuntu/+source/language-pack-it/+bug/280063](https://bugs.edge.launchpad.net/ubuntu/+source/language-pack-it/+bug/280063)


------------------------

Respecte la solució que proposa en jaume69, el fitxer català està [aquí](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.3/linux-i686/xpi/ca.xpi).

---

### Post by Josep Maria on 2008-10-09
Gràcies a tots i especialment a en RainCT.
He baixat el fitxer i ara el Firefox 3.03 funciona de nou en català.
Vaig obrir aquest post perquè em pensava que no era un problema només meu. De fet crec que es va originar a la darrera actualització dels language pack que fa automàticament el sistema.
Ara hauria de marcar aquest post com resolt, però no veig com fer-ho..
Ja està!

---

### Post by slink on 2008-10-20
Hola, 

jo vaig tenir el mateix problema i ho he resolt tal com explica en RainCT, però ara m'apareixen dues extensions inhabilitades a Firefox: 'Firefox (ca) 3.0' i 'Firefox (en-GB) 3.0'. 

[Captura]("http://lh6.ggpht.com/felixzb/SPyhc2U2ePI/AAAAAAAAFLM/cPUK_hgLpFY/s640/Captura-Complements.png")

Cal que les elimini? Com? (Vull dir que, en principi, no tenen accés)

---

### Post by trinkus on 2008-10-20
Jo tambe em vaig trobar amb tot aixo. Gracies al RainCT ho he solucionat. Merci!
No obstant estic com l'Slink...

---

### Post by jaume69 on 2008-10-23
A mi tampoc em surt en català,tot i tenir-lo instal.lat.
Em surt en Spain.

O pot ser per poder tenir-lo en català has d'instal.lar el **pack-base-català-valencià** ??

Bé,jo no tinc Ubuntu en català més que res per problemes amb programes o aplicacions i "lius" de traducció,pels programes.
Ja sé que direu que si poses L'Ubuntu en Català queda perfectament traduït,però ves..

**P.D.**Si teniu **Hardy**,en els repositoris hi ha el **adobe-flashplugin** que funciona molt millor que el **non-free**,al menys a mi!!.

Salut.

---

### Post by jaff77 on 2008-12-11
Hola, sóc nou a l'Ubuntu i al linux. Estava intentant posar el firefox en català i al Synaptic no me surt el pack mozilla-firefox-locale-ca que comentau q s'ha d'instal·lar. Algú me pot indicar com fer-ho.
Gràcies

---

### Post by jaff77 on 2008-12-11
Disculpeu, ja està. Me faltava habilitar el suport d'idioma com expliqueu aquí

[http://ubuntuforums.org/showthread.php?t=712046&highlight=Suport+d%27idioma](http://ubuntuforums.org/showthread.php?t=712046&highlight=Suport+d%27idioma)

Sistema -> Administració -> Suport d'idioma

---

