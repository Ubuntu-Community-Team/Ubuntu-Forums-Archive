---
title: "[SOLVED] Hardy-heron 8.04 alpha2"
date: 2008-01-01
forum: Catalan Team
---

### Post by SiscoGarcia on 2008-01-01
Hola,

Com podeu veure a la imatge que us adjunto estic baixant-me la versió alfa2 de la Hardy Heron que sortirà a l'abril. No sé quants problemes tindré ni si tornaré a instal·lar-me la Gutsy però ara mateix tinc una mica de temps i aquesta màquina que m'han deixat a la feina perquè vagi fent provatures.:rolleyes:

Ja us explicaré què tal.

---

### Post by SiscoGarcia on 2008-01-05
Hola un altre cop,

Després d'uns dies d'inactivitat amb el Hardy-Heron, us comunico el que he trobat:
al moment d'actualitzar-se em va sortir un "bug", no podia comunicar-ho directament el firefox i deia "gnome-screenshot crashed with SIGSEGV". A part d'això m'estic movent tranquil·lament i només trobo que no agafa xarxa sense fils (amb la Gutsy no tenia cap problema), no sé si ara que ha actualitzat programari anirà millor (de fet siu que el bluetooth ara és connectable.

Ja us aniré informant.;)

---

### Post by Neret on 2008-01-09
Doncs jo vinc de batallar amb la 6.06 i nois he instal.lat aquesta 8alpha2 sense cap problema ni amb la ipw2200 - després dels maldecaps que sempre m'hi han donat les actualitzacions de kernel del 6.06-  ahir es va actualitzar ja a l'alpha 3 i realment el canvi és bestial, això ha progressat molt i molt bé. :)
salut

---

### Post by SiscoGarcia on 2008-01-09
Hola Neret,

Acabo d'actualitzar-me a l'alpha3 però continuo amb el mateix problema que amb l'alpha2, no tinc xarxa inalàmbrica. Potser el problema és que es tracta d'una màquina amb una edat, és un portàtil Dell latitude D800 de segona mà que tindrà uns 4-5 anys, i la veritat és que abans ja anava una mica curt de tarja inalàmbrica (perdia molt senyal amb una mica de distància al router).

La veritat és que espero que en properes actualitzacions se solucioni la que per mi és l'única pega que hi he trobat.;)

---

### Post by papapep on 2008-01-09
Fes un 

```
lspci |grep Network
```

a veure quin model de tarja wifi tens. Si és una BCM4309 (Broadcom), hi ha un fil on donen solució al tema. 

Tot i que és antic crec que et pot funcionar:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Ndiswrapper_for_Broadcom_43xx_wireless_chipset](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Ndiswrapper_for_Broadcom_43xx_wireless_chipset)

---

### Post by SiscoGarcia on 2008-01-09
Efectivament papapep, aquest és el model de tarja que tinc
```
sisco@sisco-laptop:~$ lspci |grep Network
02:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 02)

```
El que passa és que quan segueixo l'enllaç que proposes no puc accedir al fitxer que em demana descarregar
   ```
 * Put the Ubuntu CD that you installed Ubuntu with in the CD drive.
    * Download this to the desktop (the Firefox default, so if you haven't changed it, that's where it went/will go).
    * In a terminal type 
```
Llavors ja no sé què fer.

Gràcies de tota manera.

---

### Post by patrickfromspain on 2008-01-10
aqui te l'adjunto!

---

### Post by SiscoGarcia on 2008-01-14
Gràcies patrick per passar-me el fitxer però no rutlla (t'adjunto el missatge que m'ha donat el terminal després d'intentar-ho seguint el fil que indicava el papapep). No sé si té res a veure amb què és una Hardy-alfa o què però no tinc CD d'instal·lació, de manera que tot i que em sap molt greu, ara provaré d'instal·lar el driver natiu segons què diu aquest [HOWTO]("http://ubuntuforums.org/showthread.php?t=197102&highlight=install+ndiswrapper"). 

Us seguiré informant.

---

### Post by SiscoGarcia on 2008-01-14
He provat el controlador propietari (és .deb) i tampoc no me n'he sortit. Us adjunto la captura amb el que em deia a Sistema>Administració>Eines de Xarxa.

Alguna idea sobre com poder fer-ho? per consola?

Tampoc no és res greu ja que tinc la màquina amb cable i navego sense problema, és una qüestió de tenir-ho tot com cal.

Gràcies.

---

### Post by patrickfromspain on 2008-01-14
et falta marcar el fitxer com a executable... sudo chmod +x ndiswrapper_setup

---

### Post by SiscoGarcia on 2008-01-14
Gràcies Patrick però no me'n surto. Aquest cop sí que ha començat a funcionar però s'ha quedat una bona estona dient que feia una pausa de 10 segons i que llegís no sé quin missatge. Alguna idea?

---

### Post by jodufi on 2008-01-15
Com et diu a la captura, tenies un gestor de paquets obert quan l'has executat? Com ara el Synaptic o el gestor d'actualitzacions....
Torna a provar-ho amb aquestes aplicacions tancades

---

### Post by PauGNU on 2008-01-15
A vosaltres no us passa que han canviat l'xorg.conf a Hardy?. No sé com s'ho han fet, però han canviat els fitxers de configuració i ara no hi ha forma de trobar-los...

(disculpeu que canvie una mica de tema... però no veia necessari obrir un nou fil)

SAluT!

---

### Post by SiscoGarcia on 2008-01-15
jodufi gràcies pel teu interès però no tenia cap gestor de paquets obert, ni synaptic ni gestor d'actualitzacions ni cap altre. No sé què em passa, suposo que és una versió molt "verda" encara, pensa que no deixa de ser una versió alfa, no és ni beta. Gràcies de tota manera, seguiré intentant.

---

### Post by patrickfromspain on 2008-01-16
perque no ho fas a mà, com tota la vida?

sudo ndiswrapper -i driver.inf
sudo ndiswrapper -l (per veure si s'ha instalat)
sudo ndiswrapper -ma
sudo modprobe ndiswrapper

salut!

PD: voleu dir que haurieu d'estar fent servir aquesta alpha? D'algu que s'insta&#320;la una versió alpha diria que s'espera que aquestes coses les sapiga fer sol.. i sino google sempre es un bon aliat.

---

### Post by CarlesOriol on 2008-01-16
-ma -mi -m 

Quina diferencia hi ha?

---

### Post by SiscoGarcia on 2008-01-16
Moltes gràcies pel teu interès Patrick. Ara mateix no puc provar-ho a mà però quan tingui temps ho intento.

D'altra banda tens raó que no sóc la persona més indicada per fer aquestes proves. Em sembla que ha quedat clar que una alfa em va gran, però com que la Gutsy la tinc instal·lada des de la beta, em va picar la curiositat de provar l'alfa.

Si no me'n surto com m'has dit torno a la Gutsy i esperaré que la Hardy estigui més madura. ;)

---

### Post by SiscoGarcia on 2008-01-21
Sento dir-vos que no me n'he sortit d'instal·lar els drivers de la tarja i com vaig comentar l'altre dia deixo l'alpha i me'n torno a Gutsy fins que això estigui més avançat.

---

### Post by eduardsola on 2008-01-22
> **SiscoGarcia said:**
> Sento dir-vos que no me n'he sortit d'instal·lar els drivers de la tarja i com vaig comentar l'altre dia deixo l'alpha i me'n torno a Gutsy fins que això estigui més avançat.

Jo en el teu cas ja no ho hauria ni intentat, amb una tarja sense fils... amb la de problemes que hi ha amb la Gutsy, i ja està implantada, imagino que amb la Hardy versió aplha n'hi deuen haver el doble.

Però sempre va bé provar, ara ja ho sabrem per una altre vegada :biggrin:

---

### Post by SiscoGarcia on 2008-01-22
Eduard, amb la Gutsy no n'he tingut cap de problema perquè els drivers lliures són compatibles i a més permet d'instal·lar els privatius (fins i tot en mode gràfic). El problema és que la Hardy encara és alpha, no és ni beta, és a dir, no és ni una versió de proves, encara és per desenvolupadors, i jo no em trobo en aquest grup.

Ja està bé haver-ho provat, el que problema és que he fet perdre temps a gent que podria haver-se dedicat a una altra cosa. Ho sento.:confused:

---

### Post by eduardsola on 2008-01-23
> **SiscoGarcia said:**
> Eduard, amb la Gutsy no n'he tingut cap de problema perquè els drivers lliures són compatibles i a més permet d'instal·lar els privatius (fins i tot en mode gràfic). El problema és que la Hardy encara és alpha, no és ni beta, és a dir, no és ni una versió de proves, encara és per desenvolupadors, i jo no em trobo en aquest grup.

Ja està bé haver-ho provat, el que problema és que he fet perdre temps a gent que podria haver-se dedicat a una altra cosa. Ho sento.:confused:

Bé, a tu et van anar bé, però a mi em van suposar molts problemes, fins que vaig acabar escaldat de tan provar coses i em vaig passar al cable...

I no crec que hagis de patir perquè la gent hagi perdut el temps, les solucions ja estan escrites, ara només falta que algú les busqui, les trobi aquí, i solucioni algun problema...

---

