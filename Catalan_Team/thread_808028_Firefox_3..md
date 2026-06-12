---
title: "Firefox 3."
date: 2008-05-26
forum: Catalan Team
---

### Post by oriolsbd on 2008-05-26
Hola a tothom.

Fa uns dies, hi havia uns fils comentant que el Firefox 3 en Ubuntu va lent. Avui he vist aquest post a FirefoxCat:
[http://firefoxcat.blogspot.com/2008/05/el-problemes-de-rendiment-del-firefox-3.html](http://firefoxcat.blogspot.com/2008/05/el-problemes-de-rendiment-del-firefox-3.html)

En el post s'explica el motiu del baix rendiment, i el que cal fer per a millorar-lo.

Salut!

Oriol.

---

### Post by jaume69 on 2008-05-26
Doncs jo un arxiu de **About:config**,que diu que s'ha de modificar no l'he trobat,n'hi havia un de semblant.
He pensat afegir-lo però no donen quins paràmetres s'hi han de posar.
Pel que llegit diu que és un problema amb el sistema d'arxius **ext3** i que ho arreglaran.

A part que,jo personalment quasi o mai he arreglat res des de About:config.

No sé...,pot ser és que no ho faig bé.

:lolflag:

P.D.No hos penseu que en **windows** 'Vita' vagi molt bé que diguem..,quan li dona la gana el Flash no funciona bé i els videos es paren i no sents res,al menys a mi.A algú altre també li ha passat,crec.

---

### Post by oriolsbd on 2008-05-26
Hola, Jaume.

L'about:config no és cap fitxer. Quan tens el Firefox obert, a la barra d'URL (on poses la web on vols anar) hi escrius "about:config" i podràs editar la configuració del Firefox.

Primer et donarà un missatge avisant-te que estàs tocant configuració interna del Firefox. Si acceptes, veuràs tota una llista de paràmetres. Filtra pel paràmetre que t'he passat. Jo al principi no el tenia. Si tu te'l trobes, només has de modificar el valor. Si no te'l troba, fes clic al Firefox amb el botó dret i fes "Nova -> Cadena". Com a nom li poses el paràmetre que indicava l'enllaç, i com a valor un dels tres que et donava.

Salut!

Oriol.

---

### Post by jaume69 on 2008-05-26
Doncs ja ho he posat,i el valor en **off** i la veritat no sé si hi ha millora,no ho sé diferenciar...pot ser una mica.(Però ara no tindré seguretat?,va home va..!)

El que si es nota és quan treus els efectes d'escriptori o canvies de gestor de finestres de Compiz a Metacity.

Merci,Oriolsbd.

:roll:

---

### Post by CarlesOriol on 2008-05-27
No sé com ho poseu però jo aquesta cadena **toolkit.storage.synchronous** no la tinc.

---

### Post by patrickfromspain on 2008-05-27
jo tampoc la tinc, però sembla normal.

La noticia es del 26 de maig i diu textualment: "a partir d'ara, des d'about:config podrem accedir a la cadena toolkit.storage.synchronous"

per tant, supuso que es bastant normal que no la tinguem al nostre firefox: tant l'RC1 com la Beta 5 son anteriors i, per tant, aquesta cadena no hi deu ser. I afegir-la dubto moltissim que faci res, ja que el firefox no deu saber que fer-ne..

Salut!

EDITO: efectivament, d'un dels articles:

> 
That patch will be in either Firefox 3.0.1 at the latest, and we’ve been in contact with Linux distributors to make sure they’re aware that the patch is fine to take in their builds — desirable, even. It might be in Firefox 3.0 proper, depending on what happens with an RC2,

---

### Post by RainCT on 2008-05-27
Per si no us heu llegit del tot l'[article](http://shaver.off.net/diary/2008/05/25/fsyncers-and-curveballs/) en anglès que explica el problema, si us posseu una versió nova del Firefox i canvieu això, esteu corrent el risc que si l'ordinador es queda penjat o se'n va la corrent podeu perdre TOTES les adreces d'interès (entre d'altres coses).

---

### Post by CarlesOriol on 2008-05-28
uala Sigfried... ara si que t'has quedat a gust.

Aconolliu-vos mortals si toqueu els valors sagrats de la configuració eterna!!!!

Malgrat que pot passar, tampoc cal ser tant catastrofista. A més no sé com deu estructurar els index el firefox amb aquesta llibreria però el mes probable és que tinguessis problemes amb una part (la de les darreres visites) i no amb la totalitat de l'estructura de dades.

---

### Post by RainCT on 2008-05-28
> **CarlesOriol said:**
> uala Sigfried... ara si que t'has quedat a gust.

Doncs sí :P :P.


> **CarlesOriol said:**
> 
Aconolliu-vos mortals si toqueu els valors sagrats de la configuració eterna!!!! Malgrat que pot passar, tampoc cal ser tant catastrofista.

Haha. No home, només vull evitar que després apareguin missatges del tipus «arghhh el $%*!# Firefox se m'ha carregat les dades!» ;).


> **CarlesOriol said:**
> A més no sé com deu estructurar els index el firefox amb aquesta llibreria però el mes probable és que tinguessis problemes amb una part (la de les darreres visites) i no amb la totalitat de l'estructura de dades.

Segons diu al bloc aquest on un dels desenvolupadors ho explica (jo no tinc ni idea del tema), si hi ha algun problema peta tota la base de dades.

---

