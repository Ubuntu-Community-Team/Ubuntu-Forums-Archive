---
title: "[SOLVED] MythTV: tv3 no es veu"
date: 2008-08-06
forum: Catalan Team
---

### Post by patrickfromspain on 2008-08-06
Hola gent!

A casa m'he muntat un ordinador amb un mythbuntu. Tot sembla anar prou be i la veritat es que n'estic content: un cop configurat va perfectament.

L'unic problema que li veig per ara es que no aconsegueixo sintonitzar els canals del grup de la televisió catalana: tv3, 3/24, 33 i 300. Al mythtv, per configurar la tarja de tv he fet servir un channels.conf, s'importa bé i s'afegeixen tots els canals, però a l'hora de posar tv3 em diu que no ha rebut un channel lock i no es veu el canal. Si m'espero un rato, al final em diu que esta a mig lock, però d'alla no pasa. El mateix channels.conf funciona be amb tv3 fent servir el me-tv.

He provat a canviar valors de time-out i de retras a la sintonitzacio, però res. Algu em sap dir alguna cosa?

Per cert, la meva tarja de tv es una Hauppage Nova-T pci.

salut!

---

### Post by CarlesOriol on 2008-08-07
El mythtv no usa el channels.conf.
Has reescanejat els canals amb el mythtv-setup?

---

### Post by patrickfromspain on 2008-08-07
si, el mythtv té una opcio per importar el channels.conf, i funciona bé, al menys amb els demes canals.

A part tambe he provat a escanejar els canals, en trova un munt i entre ells tv3, pero fa el mateix.

---

### Post by patrickfromspain on 2008-08-07
per cert, un altra cosa que no funciona: el contro de volum. Si escolto musica i pujo/baixo el volum, funciona be, pero veient la tele, el volum no canvia, encara que per pantalla surt la barra de volum que puja i baixa.

Salut

---

### Post by CarlesOriol on 2008-08-08
mmmmm....

És extrany. Jo tinc el mythtv en 2 ordinadors i l'he provat en tants d'altres. Mai no he tingut cap problema amb el control de volum ni amb les capturadores dvb. (tot i que no he provat el model que comentes).

Pots comprovar per curiositat que a l'alsa mixer si la teva controladora de so té un canal d'audio exclusiu pel dvb? (en les meves no passa però per cercar el possible origen del problema).

Una altra cosa que pots comprovar (ara no soc a Can fanga per mirar-ho) és que els canals de tv3 s'emeten per dos ids. Mira que no els tinguis duplicats i estiguis agafant el de pitjor qualitat en el myth i l'altre al me-tv.

Quan pugui et penjo una copia de la meva configuració de canals (channels.conf i la taula del mythtv) per si et serveix de res.

---

### Post by patrickfromspain on 2008-08-08
com miro si el tv3 esta duplicat? al channels.conf nomes surt un cop.

La controladora no sembla tenir un canal d'audio exclusiu pel dvb, pero gracies a l'alsa mixer he vist el problema: quan estic amb la musica, puja i baixa el canal pcm, quan estic en tele no es mou cap control.

Tu que fas anar? Ubuntu i a sobre hi instal·les el mythtv o mythbuntu o alguna distro similar?

merci per l'ajuda

EDITO: audio solucionat. Configuracio -> Configurar -> general. Al final he deixat mixer  /dev/mixer i dispositiu d'audio /dev/adsp.

---

### Post by CarlesOriol on 2008-08-09
Bé... com a mínim has arreglat el tema audio.

Per l'altre la referència que cerques no serveix, he insta&#320;lat a voltes el mythbuntu i d'altres cops el mythtv subre ubuntu.

En ambdos casos l'escriptori de fons faig que sigui gnome ja que el xcfe que porta el mythbuntu m'agobia.

Però per aquí no veig com podem anar endavant.

---

### Post by patrickfromspain on 2008-08-09
moltes gracies carles. Al final, m'has donat la solució. Amb això dels ids, buscant he trovat, al mythtv-setup, sota l'editor de canals, no-se-que de transponders. He vist que moltes freqüències estaven duplicades i amb alguns valors diferents. En el cas de la freqüència de tv3 ho he solucionat posant els mateixos valors a l'un que a l'altre: en un dels apartat, hi deia 1/2 a un i 2/3 a l'altre, i deixant-ho a 2/3 als 2 ha solucionat el problema.

menos mal!

merci per l'ajuda

---

### Post by CarlesOriol on 2008-08-09
Tot i que la solució l'has tret tu :-D, espero haver ajudat evitant que insta&#320;lessis i desinsta&#320;lessis uns quants cops el myth fent proves.

Au... a veure si aquest pots serveix per algú més al futur.

---

