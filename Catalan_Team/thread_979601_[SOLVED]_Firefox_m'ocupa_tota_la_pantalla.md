---
title: "[SOLVED] Firefox m'ocupa tota la pantalla"
date: 2008-11-12
forum: Catalan Team
---

### Post by SiscoGarcia on 2008-11-12
Hola,

No sé què he fet però firefox m'ocupa tota la pantalla, he perdut l'accés al quadre superior (on tinc les diverses aplicacions) i tampoc no tinc accés al menú de l'AWN. L'única manera d'accedir-hi que he trobat és desplegant en menú "Fitxer" i allà seleccionant "Configuració de la pàgina..."; llavors fent qualsevol cosa torno a tenir els quadres accessibles. El que no tinc en cap moment és la barra superior de la finestra de firefox (la de color marró per defecte amb les possibilitats de minimitzar, redimensionar i tancar, a dalt a la dreta). No sé si m'explico, ja direu.

---

### Post by Nac.eol on 2008-11-12
Hola,

Has provat a apretar F11? No fos cas que ho tinguis a pantalla complerta.

Salutacions.
Nac.

---

### Post by xoldy on 2008-11-12
Hola a tots, a mi també em passava quan tenia activats els efectes d'escriptori, i com bé diu Nac.eol amb l'f11 aconseguia tornar a la normalitat. Com que era un tema que cansava vaig optar per treure tots els efectes d'escriptori, i ja no m'ha tornat a passar.
No se les causes, però com que no son imprescindibles els efectes...

Salutacions

---

### Post by SiscoGarcia on 2008-11-12
Nac i xoldy, merci però no és això. Us adjunto 2 captures que he fet, una corresponent al que explicava a l'entrada anterior i la segona la que m'he trobat en reiniciar, que tampoc no puc modificar. Potser així queda més clar el que em passa.

---

### Post by papapep on 2008-11-12
Recordo que a la llista info ha aparegut vàries vegades aquest tema Sisco, [crec que seria bo que fessis una repassada a l'arxiu]("http://search.gmane.org/?query=firefox+pantalla&author=&group=gmane.linux.ubuntu.user.catalan&sort=date&DEFAULTOP=and&xP=Zfirefox&xFILTERS=Glinux.ubuntu.user.catalan---A").

---

### Post by trinkus on 2008-11-12
Es exactament el que em passa mi i se soluciona traient els efectes d'escriptori. Evidenment, et quedes sense efectes, que tampoc fa gracia...
Aixo passa des que he actualitzat a la Intrepid.

El que m'ha quedat clar en aquestes dues setmanes es que la Hardy, a mi almenys, em rendeix molt millor quant a que les coses funcionin, diguem la wifi, els efectes, els usb... etc...

---

### Post by xoldy on 2008-11-12
A mi ja em passava amb la Hardy. Deu ser cosa de la targeta ATI.

---

### Post by PatrickVogeli on 2008-11-12
sudo apt-get install compizconfig-settings-manager per instal·lar un programa per configurar el compiz; el trobareu a Sistema -> Preferencies -> Editor de la configuracio del compiz

Alla busqueu el plugin Window decoration i a Decoration Windows hi heu de posar (any) | class=Firefox

Despres tanqueu el firefox, desactiveu el aquest plugin, torneu-lo a activar i proveu, us segueix passant?

salut

---

### Post by SiscoGarcia on 2008-11-13
Sí senyor Patrick, l'has clavada, =D> així se solventa el tema de la barra superior; però ara em trobo amb què no m'ocupa tota la pantalla com caldria (adjunto captura). Val a dir que ja tenia instal·lat el compizconfig-settings-manager, no sé si hi té a veure.

EDITO: Acabo de veure que això m'afecta també a l'OOo, per exemple.

---

### Post by SiscoGarcia on 2008-11-13
Em replico a mi mateix perquè no havia adjuntat la captura del FF :oops:

Allà va.

---

### Post by PatrickVogeli on 2008-11-14
es curios... juraria que no hi té cap relació, ja que de fet el que es fa amb aquesta linia es activar la decoració de finestra per a qualsevol finestra o el firefox. No entenc la relació amb l'openoffice.

Per curiositat, has entrat i sortit de la teva sessió despres de fer-ho? Si tornes a deixar any i reinicies la sessió, torna tot a la normalitat?

---

### Post by ffp on 2008-11-14
> **PatrickVogeli said:**
> sudo apt-get install compizconfig-settings-manager per instal·lar un programa per configurar el compiz; el trobareu a Sistema -> Preferencies -> Editor de la configuracio del compiz

Alla busqueu el plugin Window decoration i a Decoration Windows hi heu de posar (any) | class=Firefox

Despres tanqueu el firefox, desactiveu el aquest plugin, torneu-lo a activar i proveu, us segueix passant?

salut

Doncs així a mi també em funciona.

---

### Post by SiscoGarcia on 2008-11-14
> **PatrickVogeli said:**
> es curios... juraria que no hi té cap relació, ja que de fet el que es fa amb aquesta linia es activar la decoració de finestra per a qualsevol finestra o el firefox. No entenc la relació amb l'openoffice.

Per curiositat, has entrat i sortit de la teva sessió despres de fer-ho? Si tornes a deixar any i reinicies la sessió, torna tot a la normalitat?

Tampoc no sé si té cap relació, només he observat que ara s'obren així.

Pel que fa a la suggerència de reiniciar sessió, ja ho havia fet i és així com queda, i si ho torno a deixar any i reinicio també es queda igual, és a dir, sense ocupar tota la pantalla (per sota queda una part buida).:confused:

EDITO: El "problema" de deixar una zona inferior sense cobrir em passa amb totes les aplicacions; ara mateix m'acaba de passar amb l'Evolution.

---

### Post by Kette on 2008-11-15
Hola.
El problema de que no t'ocupi la part inferior de la pantalla pot ser per la configuració del AWM, mira si tens activada l'opció per a que les finestres maximitzades no cobreixin la barra del AWM.
Saut
Eugeni

---

### Post by SiscoGarcia on 2008-11-15
> **Kette said:**
> El problema de que no t'ocupi la part inferior de la pantalla pot ser per la configuració del AWM, mira si tens activada l'opció per a que les finestres maximitzades no cobreixin la barra del AWM.

Justa la fusta, Eugeni. El que no sé és en quin moment ho he canviat, perquè sóc conscient que ho vaig configurar així. Suposo que mentre feia les proves proposades pel Patrick, sense adonar-me'n amb el Touchpad ho hauré activat.

Merci.

---

### Post by ffp on 2008-11-17
Hola,

Avui se m'ha actualitzat la extensió pel Firefox, NoSript, una vegada actualitzat et demana reiniciar el Firefox, l'hi dic que si, i ostres el Firefox torna a ocupar tota la pantalla. F11 i una altra vegada F11 i arreglat.
Es clar que es un bug amb el Compiz, però encara no s'ha resolt.

Ho sento,

---

### Post by jvmonjo on 2008-11-20
> **ffp said:**
> Doncs així a mi també em funciona.

A mi no m'ha funcionat això. Jo crec que aquest bug no està resolt encara i algú deuria traure l'etiqueta SOLVED de l'article.

---

### Post by Kette on 2008-11-20
Hola.
A veure si aclarim el tema. Això de la pantalla completa poden ser dues coses:
- que realment sigui un bug i com a tal s'hauria de resoldre pels problemes que comporta o...
- que sigui una nova "propietat" de la versió 3 que no vol dir que no ens toqui el "voraviu".
Per saber si es tracta del segon cas deixeu que la finestra estigui maximitzada i apropeu la fletxa del ratoli a la part superior de la pantalla i, molt possiblement, veureu que torna a aparèixer la barra de navegació i els botons per a tancar o minimitzar la pantalla.
Es tracta d'una nova funcionalitat del Firefox 3: la navegació a pantalla completa, però completa de veritat.
Us adjunto dues captures per a entendre millor l'explicació
Salut
Eugeni

---

### Post by PatrickVogeli on 2008-11-20
es un bug, i esta ben clar. Em sembla que nomes passa amb algunes combinacions de hardware, ja que a mi, per exemple, no em passa.

A la meva novia si que li passava i, la veritat, es bastant empipador.

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/270400](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/270400)

D'aquest "bug report" hi ha posat el següent:

> 


I got this fixed last night without disabling Compiz or anything. I think what I did was do the F11 trick to get it as it should be, then I unmaximised the window and found that it had no border, so I closed it in it's unminimixed state, opened it again and maximised it. The problem hasn't come back since. I'm not 100% sure if that was the correct way I did things but I know I had to unminimize the window and move it down also as the top bar was behind the Gnome top panel.

Obviously this isn't a fix per se but I hope it's of some use to a developer! =)


Sembla que a la gent li funciona.

salut

---

### Post by SiscoGarcia on 2008-11-20
Doncs jo no tinc clar que sigui un bug, però segur que no és el que diu el Kette, ja que la finestra maximitzada no era la que ell adjunta i no apareixia la barra de navegació en passar-hi per sobre, ja que de fet aquesta barra mai desapareixia (mireu les imatges que havia adjuntat a les entrades 4 i 10 del fil, no tenen res a veure amb les del Kette).

Si voleu torno a deixar el fil sense resoldre, però no ho tinc clar.

---

### Post by papapep on 2008-11-20
Els fils es donen per resolts si la persona que l'ha obert resol el seu problema, no en funció de si un problema o bug generalitzat es corregeix a l'upstream. Aquesta seria la tasca d'un bugtracker, que no és el nostre cas.
Aleshores, si el Sisco ho ha pogut solventar, fil resolt.

---

### Post by jvmonjo on 2008-11-21
> **papapep said:**
> Els fils es donen per resolts si la persona que l'ha obert resol el seu problema, no en funció de si un problema o bug generalitzat es corregeix a l'upstream. Aquesta seria la tasca d'un bugtracker, que no és el nostre cas.
Aleshores, si el Sisco ho ha pogut solventar, fil resolt.

Desconeixia aquest procediment. Una cosa més que he aprés.	:oops:

---

### Post by SiscoGarcia on 2008-11-21
> **jvmonjo said:**
> :oops:

No patisques, som ací per aprendre. Jo espere continuar fent-ho cada dia ;)

---

### Post by gtermes on 2008-12-04
Hola!
ja sé que aquest tema està tancat, però m'ha passat una cosa que potser pot ajudar a algú.
Jo també em trobava amb el problema de la finestra que ocupa tota la pantalla, i la veritat és que de moment ho resolc amb l'F11. Però m'he fixat en una cosa: al prémer el botó de maximitzar (el quadrat) per passar de pantalla maximitzada a mida personalitzada, resulta que m'ha tornat a ocupar la pantalla sencera. Però aleshores, he estirat una cantonada per fer-la més petita i voila! problema resolt! A partir d'aquest moment ja no se m'obre ocupant tota la pantalla.

Per tant, crec que, simplement, tenim la "mida personalitzada" totalment sobredimensionada. Com que la mida personalitzada es manté fins que no la tornes a canviar, n'hi ha prou en canviar aquesta mida una sola vegada amb un cop de ratolí, i problema resolt.

Ai, no sé si m'he explicat gaire bé, espero que si.

A reveure

---

### Post by tanreb20 on 2008-12-04
Crec que ho vaig respoldre = jaja

em passava exacamanet el mateix, i no s ecom ara no pasa, pot ben ser aixo!

---

### Post by torracastanyes on 2008-12-07
A mí no m'havía passat, fins que he instalat un tema d'Ubuntu Studio.
Com diu en gtermes, es problema de la mida personalitzada, que pel que sembla, per defecte es molt més gran que la maximitzada.
Vosaltres també teniu temes d'Ubuntu Studio?

---

### Post by trinkus on 2009-02-10
Despres de tot a mi em segui passant i buscant en altres forums diuen que molts cops es a causa d'algunes web que obren popups pero que es pot solucionar desmarcant una de les opcions que hi ha a Sistema>Preferencies>Editor de la configuracio del Compiz>Utilitats>Workarounds
Per si de cas he desmarcat les dues (basicament perque desconec el que fan...) i ara no em passa mes... i les demes funcions del Compiz segueixen funcionant be... a veure si algu pogues contrastar-ho...

---

### Post by SiscoGarcia on 2009-02-10
> **trinkus said:**
> Despres de tot a mi em segui passant ... a veure si algu pogues contrastar-ho...

A mi també em continuava passant en un usuari que només faig anar eventualment, i he pogut contrastar que es compleix el que proposes.

---

