---
title: "Problema amb els drivers de la tarja de só"
date: 2008-05-02
forum: Catalan Team
---

### Post by Satboy on 2008-05-02
Hola tothom,
 Des que vaig actualitzar de la **Gutsy** a la **Hardy**, cada cop que engego l'ordinador i se'm comença a iniciar la **Hardy** allà on diu **Loading hardware drivers** em surt el següent missatge:

 **SIS 630_Smbus 0000:00:02.0 SIS 630 COMP BUS NOT DETECTED, MODULE NOT INSERTED** :shock:

 Amb la **Gutsy** no vaig tenir cap problema al respecte.Què em podeu recomanar que faci?
 Gràcies!

 Siau!:wink:

---

### Post by papapep on 2008-05-02
Sense més coneixement de causa, jo diria que la SIS 630 és una placa de video, no d'audio.

---

### Post by Satboy on 2008-05-02
> **papapep said:**
> Sense més coneixement de causa, jo diria que la SIS 630 és una placa de video, no d'audio.
 Hola,
 Així doncs, com és que tampoc sento res? Com puc esbrinar quina tarja de só tinc?
 Acabo de comprobar via google que es tracta de la tarja de vídeo, què puc fer pq me la detecti?

 Siau i gràcies!

---

### Post by papapep on 2008-05-02
En un terminal:

```
lspci|grep Audio
```

---

### Post by Satboy on 2008-05-02
> **papapep said:**
> En un terminal:

```
lspci|grep Audio
```

 Hola,
 Ja ho he fet i m'ha sortit això:

 **00:0d.0 Multimedia audio controller: ESS Technology ES1969 Solo-1 Audiodrive (rev 02)**

 I ara què?

 Siau!

---

### Post by papapep on 2008-05-02
Doncs ara ja saps quina placa d'audio tens i ja pots buscar informació sobre per què no et funciona  ;-)

---

### Post by papapep on 2008-05-02
Ja ho has pogut solucionar? Si expliques com, quedarà per la posteritat i els que vinguin darrera amb el mateix problema :-)

---

### Post by diablessamariken on 2008-05-10
Hola

seguint una mica aquest fil us volia preguntar si des que heu actualitzat a HARDY heu notat diferències pel què fa al so. El meu portàtil ACER ASPIRE 5104 WLMi reprodueix els sons a un volum bastant menor que abans. 
Tinc la següent tarjeta de so:

ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)

Algú se li actud perquè pot ser? 

Gràcies
Astrid

Salut, tabals i foc!

---

### Post by pespin on 2008-05-10
Segurament deu ser perquè abans utilitzaves ALSA i ara al actualitzar a hardy el predeterminat és PulseAudio :)

---

### Post by diablessamariken on 2008-05-10
HOla!

el predeterminat de què? com ho podria modificar?

Gràcies

---

### Post by pespin on 2008-05-10
El servidor de so predeterminat, que fa de capa entre el programari i el maquinari.

Pots modificar-ho a "Sistema->Preferències->So". Segurament tindràs posat als menus desplegables la opció "Detecta automàticament". Prova a posar-hi ALSA a tots i reinicia a veure que tal.

---

### Post by diablessamariken on 2008-05-10
Hola

doncs no millora gens després de seleccionar ALSA a totes les opcions de so...

no sé què deu de ser...

---

