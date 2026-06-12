---
title: "[SOLVED] Tinc un problema amb l'ubuntu 7.10"
date: 2008-02-23
forum: Catalan Team
---

### Post by ggrifols on 2008-02-23
Hola a tots i a totes, fa pocs dies que he migrat a ubuntu i avui és el primer dia que aconsegueixu conectarme amb ell (tenia problemes de compativilitat amb el meu netgear wg111v2). 
Després de la instal·lació del sistema operatiu tot em va bastant bé, tot tret de unes coses que m'agradaria que m'ajudessiu a solocionar i aclarir.

Un dels meus problemes principals es l'idioma, en teoria el meu ubuntu està configurat perquè estigui amb català pero tot i això la major part del sistema està amb anglés (Gimp, Firefox, reproductor...). Així doncs m'agradaria saber quina és la manera amb la qual el meu sistema operatiu quedi 100% amb català o que per lo menys els programes principals estiguin amb català.

L'altre problema que tinc és a l'hora de reproduir arxius de musica i videos (només ho he probat amb arxius MP3) el reproductor em diu que necessitu obtenir un codec (tot això amb anglès), aleshores clico a "Search" i em troba un arxiu per instal·lar, perìo en el moment que el clico em surt una finestra en la que sem dona a coneixer el següent:

```
The use of this software may be restricted in some countries. You must verify that one of the following is true:

&#8226; These restrictions do not apply in your country of legal residence
&#8226; You have permission to use this software (for  example, a patent license)
&#8226; You are using this software for research purposes only

```

Aleshores clico a "Confirm" i em surt la finestre següent:

[[IMG]http://img339.imageshack.us/img339/50/screenshotmk5.th.png[/IMG]](http://img339.imageshack.us/my.php?image=screenshotmk5.png)

Així doncs, mai puc instal·lar el codec. sper-ho que em pogueu ajudar en aquest tema ja que no mi entenc gaire joc amb l'angles i em lio bastant.


El tercer problema que tinc està relacionat amb la instal·lació de plugins per el Firefox, he intentat de instal·lar varis cops els comoponents adaptats per linux que et facilita la gent de Mozilla i de moment res de res.


Bé, això és tot, espero que hem pogueu ajudar ja que tinc moltes ganes de començar a utilitzar l'ubuntu que aquest funcioni bé ^^

---

### Post by patrickfromspain on 2008-02-23
I bé, quin es el problema?

T'esta avisant de que en alguns paisos aquest software esta restringit i podria ser ilegal. Confirm i llestos!

---

### Post by jodufi on 2008-02-23
Problema 1:

Ves a Sistema -> Suport d'Idioma i et dirà que queden algunes coses per a instal·lar. És important que tingui connexió a Internet en fer aquest pas.

Problema 2:

Et diu que necessites connexió a Internet. Torna a provar-ho quan estiguis connectat. 
També pots instal·lar el paquet «Ubuntu restricted extras» mitjançant Aplicacions -> Afegeix/Elimina. Així se t'instal·laran moltes coses com codecs, flash, java...

Problema 3:

Mai he tingut problemes per a instal·lar connectors del Firefox. Potser algú altre et podrà ajudar.

---

### Post by Joan Marc on 2008-02-23
Pel que dius de la llengua... vas instal·lar la versió en català, o vas instal·lar la versió de [www.ubuntu.org?](www.ubuntu.org?)
Esque la segona, tots els programes van en anglès, en canvi la primera tot és en català.

Pel que fa als codecs, podría ser que no tinguessis el **multiverse** i l' **universe** activats, per activar-los, has d'anar a Sistema>Administració>Gestor de paquets Synaptic>Paràmetres>Repositoris, i allà, marcar, si no els tens marcats, el **multiverse** i l' **universe** (mira la captura si tens dubtes).

Què vols dir, els plugins per el Firefox? Si et refereixes a Complements, a Eines>Complements, tens un fil on te'n pots descarregar uns quants... no sé si et refereixes a aixo?

---

### Post by CarlesOriol on 2008-02-23
Problema 4:

**Una pregunta per fil.**

Simplifica les respostes i fa que més gent pugui participar tant en la solució com més tard quan algú es trobi en el mateix problema.

---

### Post by SiscoGarcia on 2008-02-23
Hola ggrifols, benvingut.

Pel que dius no tens un problema amb l'ubuntu, en tens 3; per la qual cosa hauries d'haver obert 3 fils i d'aquesta manera se't podrien donar solucions concretes a tu i a d'altres que puguessin tenir els mateixos.

1.- Tema llengua, a part de la versió d'ubuntu que tinguis instal·lada, fes el que et diu jodufi i podràs descarregar-te els paquets que et falten en català (jo ho tinc així i em funciona perfectament).

2.- També m'ha passat que necessito còdecs però amb la solució que et proposa jodufi n'hi hauria d'haver prou.

3.- Tema plugins, si entenc el que vols dir, crec que fent el que et proposa Joan Marc t'hauria de funcionar, en qualsevol cas mira pel fòrum quin és el plugin que no et funciona per si pots trobar que el teu problema **ja** està solventat.

Ànims i endavant;)

EDITO: Veig que mentre escrivia la resposta el Carles et deia el mateix; un fil un problema!

---

### Post by ggrifols on 2008-02-24
Moltissimes gracies a tots, crec que ho he pogut realitzar tot correctament, al final he tingut que instal·lar el plugins del firefox (java, flash, etc) des de la Terminal pero el que compte es que funcionen jeje

Respecte el tema, les meves sinceres disculpes, intentaré que no em torni a passar una cosa d'aquest estil.

Moltissimes gracies nois ;)

---

### Post by SiscoGarcia on 2008-02-24
Bé, doncs ara tocaria marcar el fil com a resolt: Thread Tools>Mark This Thread As Solved.

Apa, a ubuntejar!

---

