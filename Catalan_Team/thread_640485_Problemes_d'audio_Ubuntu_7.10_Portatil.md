---
title: "Problemes d'audio Ubuntu 7.10 Portatil"
date: 2007-12-14
forum: Catalan Team
---

### Post by pablinsfc on 2007-12-14
Bon dia a tots!!

Al final el tema de convertir àudio a mp3 ha quedat solventat amb l'audacity + lame, ja que a la radio encara tirem de windows i algunes propostes vostres del synaptic no les podia baixar.

El problema que se'm planteja ara és amb el portàtil, on tinc l'Ubuntu 7.10 des de ja fa temps. Em va de fàbula, però té el petit problema que no emet cap tipus de so. Ni a la de tres. Ni amb el totem, ni des d'internet, ni des de CD; res de res.

El més curiós és que sembla que no funcionen els altaveus, doncs si connecto la sortida de línia a la radio de l'habitació ho sento perfectament. He canviat la configuració d'audio mil vegades i ja no se ni com estava inicialment, però no hi ha manera...

Gràcies per endavant!

---

### Post by papapep on 2007-12-14
Ens cal saber quin ferro tens per a poder-te ajudar. Marca, model, model de placa de audio, etc.

---

### Post by eduardsola on 2007-12-14
Jo em moc per l'experiència i et dic que et falten els paquets de l'ALSA.

Aquí en tens l'enllaç:

[http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download)


Espero que et vagi bé!

Salut!

---

### Post by papapep on 2007-12-14
A veure, amb tot el carinyo, abans de començar a instal·lar res, i encara més quan no és paquets .deb, estaria bé saber on som. Bàsicament per no pifiar-la encara més...

---

### Post by eduardsola on 2007-12-14
> **papapep said:**
> A veure, amb tot el carinyo, abans de començar a instal·lar res, i encara més quan no és paquets .deb, estaria bé saber on som. Bàsicament per no pifiar-la encara més...

Ja ja... però és que a mi em passava just el mateix.

Per cert, el driver de l'ALSA és als repositoris, me n'oblidava.

---

### Post by pablinsfc on 2007-12-14
Us enganxo això, no sé si és el que voleu, o haig de picar alguna ordre al terminal (que excepte per compilar codi, encara el tinc bastant verd...).

Ubuntu 7.10
Kernel Linux 2.6.22-14-generic
GNOME 2.2o.1
Memòria 2,0 Gb
Processador: Intel Pentium M 2.00GHz

Us adjunto també una imatge.

Merci per tot!

---

### Post by papapep on 2007-12-14
Enganxa el que et mostri la següent ordre:

```
lspci | grep audio
```

---

### Post by pablinsfc on 2007-12-14
La ordre íntegre com la poses no em mostra res. amb lspci em mostra això de la foto,

---

### Post by papapep on 2007-12-14
Bé, afinem una mica més. Executa la següent ordre i enganxa el resultat:

```
lspci -n | grep `lspci | grep -i Audio | awk '{print $1}'`
```

---

### Post by pablinsfc on 2007-12-14
La resposta és:

00:1b.0 0403: 8086:2668 (rev 04)

(per mi chino mandarí...)

Salut i gràcies!

---

### Post by papapep on 2007-12-14
Houston, we've got a problem :-(:
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131133](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131133)

Un problema important, fins que no ho solucionin, amb l'audio. Quina marca i model concret d'ordinador és?

---

### Post by pablinsfc on 2007-12-14
Tinc un Fujitsu Siemens Amilo M1450G...

---

### Post by papapep on 2007-12-14
Doncs fins on jo se del tema, que tampoc és gaire, ho tenim un pèl complicat per ara.

Estàs en el mateix cas que el Dell Inspiron 1300. 

Si vols podem fer provatures amb el que diuen al primer enllaç, però tampoc sembla que sigui gaire exitós el tema...

---

### Post by pablinsfc on 2007-12-14
El més curiós és que amb la versió anterior em funcionava... en fi, de moment ja he posat a la bossa del portatil uns cascos i me'ls poso quan haig d'escoltar algo. Emprenya una mica, però fins que no trobem la solució adient ja tiro amb això.

Gràcies de debò per tot.

Salut!

---

### Post by papapep on 2007-12-14
Sembla ser que és una problemàtica dels kernels 2.6.22-13 i posteriors, per això no et passava abans.

---

### Post by eduardsola on 2007-12-15
> **papapep said:**
> Sembla ser que és una problemàtica dels kernels 2.6.22-13 i posteriors, per això no et passava abans.

:???: Vaja...

---

