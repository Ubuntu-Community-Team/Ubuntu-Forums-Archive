---
title: "[SOLVED] Geforce 6200 nvidia"
date: 2008-02-05
forum: Catalan Team
---

### Post by Curial on 2008-02-05
Acabo d'instal·lar una Getforce 6200.Feia temps que volia solventar el dèficit que patia la meva pantalla de 19".

Algú fora tan amable d'orientar-me.

Un cop instal·lada la targeta al port AGP i iniciat l'ordinador
m'ha desaparegut el mode gràfic i se m'ha quedat a la línia de comandes i aquí és on em perdo.
No se si haig d'extreure la targeta i instal·lar algun driver o si es pot fer ja directament en mode no gràfic.

He vist alguna wed que en parla, però  no ho tinc gens clar.

Gràcies.

---

### Post by guillemsola on 2008-02-05
Hola

crec que podries posar un 
> sudo dpkg-reconfigure xserver-xorg
d'aquesta manera s'inicia un assistent en mode texte. Has de posar atenció quant parla de la tarja gràfica. Crec que hauries de seleccionar el driver "nv" que és el propietari de nvidia o el "nvidia" que és el lliure (xo no té acceleracions).

Si cap d'aquests drivers no t'arrenca selecciona un de vga generic i després ja et barallaras des del mode gràfic.

Després et demanara la resolució, el monitor...

Les altres coses que et pregunta per configurar com el teclat i el ratolí no fa falta que les canviis.

Salut!

---

### Post by Daerun on 2008-02-05
Aquestes instruccions servirien doncs, per a cualsevol tarja nova que ens instaléssim? (canviant el model dels drivers, és clar).

---

### Post by papapep on 2008-02-05
Si saps quin driver hi has de posar, la tarjeta està soportada, etc, etc. si :-D 
Sinó, com sempre, a manilla a buscar-se la vida.

Actualment hi ha una eina, que jo no he fet servir, que es diu [Envy]("http://www.albertomilone.com/nvidia_scripts1.html") de la qual he sentit parlar prou bé, la qual solventa bastants marrons d'aquests de targetes que donen mals de cap (no ho arregla tot, evidentment).

---

### Post by CarlesOriol on 2008-02-06
**Compte!!!!** ... en Hardy tot això canvia i força!

---

### Post by papapep on 2008-02-06
Ostres!! fes-nos-en cins cèntims, va... :-D

A banda dels canvis que esmentes, no crec que en Curial estigui amb Hardy, oi?

---

### Post by Curial on 2008-02-06
> **angrychai said:**
> Hola

crec que podries posar un 
d'aquesta manera s'inicia un assistent en mode texte. Has de posar atenció quant parla de la tarja gràfica. Crec que hauries de seleccionar el driver "nv" que és el propietari de nvidia o el "nvidia" que és el lliure (xo no té acceleracions).

Si cap d'aquests drivers no t'arrenca selecciona un de vga generic i després ja et barallaras des del mode gràfic.

Després et demanara la resolució, el monitor...

Les altres coses que et pregunta per configurar com el teclat i el ratolí no fa falta que les canviis.

Salut!

Gràcies angrychai però, no hauria d'instal·lar el driver d'nvidia abans?

Pep, Carles: tinc la 7.10, sóc massa novell per anar de pressa :)

---

### Post by CarlesOriol on 2008-02-06
Si engegues amb el controlador lliure nv com et diu en angrychal. Després pots fer la resta de la feina en mode gràfic que segur que t'hi sents més còmode.

**compte**

nv = lliure  
nvidia = privatiu

al revés de com t'han dit

---

### Post by Curial on 2008-02-06
Entro en mode recuperació.
Després d'entrar la contasenya,

He escrit  la línia:
sudo dpkg-reconfigure xserver-org

I m'ha dit que l'xserver-org no està instal·lat.

M'ha pasat pel cap fer un sudo apt-get install xserver-org
Ha semblat instal·lar-se però ha sortit el missatge que no pot trobar el paquet xserver-org

Potser es millor que desconnecti l'acceleradora i ho intenti des del l'entorn gràfic?

---

### Post by papapep on 2008-02-06
És que el paquet es diu **xserver-[COLOR="Red"]x[/COLOR]org**.

---

### Post by guillemsola on 2008-02-06
No t'hi capfiquis el paquet correcte és

> xserver-xorg

M'havia deixat la X.

Fes una cosa, quant hagis escrit xserv aleshores prem la tecla de tabulador. Veuràs que l'ubuntu et completa l'expressió si té "proutes pistes". Si no et mostra una llista amb les possibilitats que hi ha pq et defineixis.

Això ho pots fer amb tot el sistema, incloses les rutes dels directoris. És molt útil per no haver de recordar exactament com era l'ordre.

---

### Post by Curial on 2008-02-06
Perdoneu, l'errada de la X ha estat meva.

Ja el tinc en mode gràfic, encara que amb un controlador restringit.
La pega és que no puc anar més enllà de 1024x769 i a mi em cal 1440x900.

Respecte al l'xserver m'ha preguntat pel l'adreça del port PCI, no ho he sabut canviar: la meva és una placa per AGP.

Demà faré mes provatures.Gràcies.

---

### Post by guillemsola on 2008-02-07
Per l'adreça PCI no t'hi amoinis si ja estàs al mode gràfic.

Respecte als controladors restringits aquests son "els bons" per tenir acceleració gràfica.

També recordar-te que si ja estàs en mode gràfic potser et serà més senzill de canviar la resolució des del menú sistema-administració-pantalles i gràfics.

Jo crec que si no et deixa pujar la resolució de la gràfica potser és més aviat perquè el monitor no està detectat correctament.

Has provat a seleccionar el monitor plug'n'play per que el detecti automàticament?

Si no torna a re-configurar l'xserver i fixa't que hi ha un punt en el que t'ha de sortir una llista on marques amb una X els modes gràfics que penses fer servir.

---

### Post by Curial on 2008-02-08
Gràcies a tots especialment a n'angrychai.

Al final la qüestió ha quedat solucionada amb uns resultats excel·lents.
He executat per segona vegada "sudo dpkg-reconfigure xserver-xorg" i en aquesta segona vegada ja m'ha aparegut el driver nvidia, la primera em va sortir, a part d'altres, només l'nv. Amb aquest últim no se perquè no em donava la una resolució de 1440x900 malgrat que tant la seleccionava per sistema-administració-pantalles i gràfics o per preferències-resolució pantalla.
Suposo que quan he activat des del mode gràfic el controlador restringit es deu haver instal·lat i ja l'he tingut després disponible dins de la llista??
Bé no vull embolicar la troca escrivint més del que cal.

Salut!
:popcorn:

---

### Post by guillemsola on 2008-02-08
Me n'alegro!

Potser que abans no estigués disponible pq el driver nvidia no és lliure i no queda "elegant" instal·lar-lo però fa millor la feina que l'altre.

Ara pots anar a dalt de qualsevol pàgina i on diu "Thread Tools" selecciones l'opció "Mark this thread as solved" i així si algú veu el post sap que té un "final feliç" i que li pot interessar donar-li una ullada.

Salut!

---

