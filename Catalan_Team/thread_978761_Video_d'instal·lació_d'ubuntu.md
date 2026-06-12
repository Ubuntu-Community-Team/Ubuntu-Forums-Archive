---
title: "Video d'instal·lació d'ubuntu"
date: 2008-11-11
forum: Catalan Team
---

### Post by auska1714 on 2008-11-11
Bones,

necessito fer un vídeo on es vegi com instal·lo ubuntu en un ordinador. Teniu alguna idea de com o puc fer? Si no pot ser vídeo,es pot amb impressions de pantalla?

merci,

Salut!

---

### Post by papapep on 2008-11-11
Virtualbox, gtkrecordmydesktop, i oli en un llum. I amb audio incorporat, si vols.

---

### Post by auska1714 on 2008-11-11
Però com ho faig ja que he d'instal·lar de 0 passant d'un windows a ubuntu eliminat tot el q te l'ordinador per tant eliminaria el programa també a part que en tancar l'ordinador per tal d'obrir l'ordinador des del live CD es pararia el programa.

---

### Post by papapep on 2008-11-11
Home....tu has demanat això:

> necessito fer un vídeo on es vegi com instal·lo ubuntu en un ordinador

i jo t'he contestat en conseqüència :-)

Si el que tu volies dir és a una màquina real, la qual deixaràs sense sistema operatiu, per a tornar-li a instal·lar un altre, com no tinguis una càmara de vídeo doncs ho veig complicat...per ser eufemista.

---

### Post by SiscoGarcia on 2008-11-11
Perdoneu el cross-posting, però m'ha encuriosit el tema del vídeo i quan he intentat instal·lar el paquet gtkrecordmydesktop en intrepid m'he trobat amb això:

```
sisco@sisco-laptop:~$ sudo apt-get install gtkrecordmydesktop
[sudo] password for sisco: 
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació d'estat... Fet
E: No s'ha pogut trobar el paquet gtkrecordmydesktop
```

Com el puc aconseguir?

Merci.

---

### Post by papapep on 2008-11-11
És que el nom del paquet exacte és gtk-recordmydesktop. 

Podeu buscar paquets per aproximació, molts cops no es sap el nom correcte del paquet, i és molt útil en casos com aquest:

```
sudo aptitude search mydesktop
```

---

### Post by xoldy on 2008-11-11
Bona nit a tots,
Sisco a mi m'ha funcionat així:

```
sudo apt-get install gtk-recordmydesktop
```

Salut!

Massa tard, en papapep ja s'ha avançat! A veure si la pròxima faig la pole

---

### Post by xoldy on 2008-11-11
Sempre pots simular una instal·lació d'ubuntu sobre windows en una màquina virtual, i així t'estalvies maldecaps amb una càmera de video filmant la pantalla. A més penso que et donarà més feina que no treballar directament amb màquines virtuals.

Salutacions!

---

### Post by auska1714 on 2008-11-11
Com es fa això?

---

### Post by SiscoGarcia on 2008-11-11
> **papapep said:**
> És que el nom del paquet exacte és gtk-recordmydesktop. 

Podeu buscar paquets per aproximació, molts cops no es sap el nom correcte del paquet, i és molt útil en casos com aquest:

```
sudo aptitude search mydesktop
```

Diuen que "saber no ocupa espai" però a mi em costa creure que càpigui tanta ciència en un sol cap ;)

> **xoldy said:**
> Massa tard, en papapep ja s'ha avançat! A veure si la pròxima faig la pole

Si és que a més del que he dit abans sobre la ciència que arriba a tenir, és difícil treure-li la pole. De tota manera no defalleixis en l'intent :)

---

### Post by SiscoGarcia on 2008-11-11
> **auska1714 said:**
> Com es fa això?

El primer que et cal és instal·lar-te el [VirtualBox]("http://www.virtualbox.org/wiki/Downloads"), després crear-t'hi una màquina virtual on hi posis l'ubuntu, i tot plegat gravar-ho amb vídeo. El que passa és que necessitaràs tenir instal·lat abans l'ubuntu per poder fer córrer la màquina virtual i gtk-recordmydesktop ;)

---

### Post by papapep on 2008-11-12
[Aquí]("http://vimeo.com/1878416?pg=embed&sec=1878416") tens un breu tutorial en vídeo que vaig fer justament per a fer proves amb el gtk-recordmydesktop, que explica com crear màquines virtuals a nivell iniciàtic.

---

### Post by lluisanunez on 2008-11-13
Aquí tens un vídeo pel sistema cutre, o sigui filmant la pantalla amb una càmera, que també té la seva gràcia
[http://www.youtube.com/watch?v=nWIrxuF5NSo](http://www.youtube.com/watch?v=nWIrxuF5NSo)

---

### Post by papapep on 2008-11-13
Corporativista.... :-P

---

### Post by lluisanunez on 2008-11-13
... ràaaapid!!! :)

---

### Post by auska1714 on 2008-11-13
Oqs, merci bona gent ;)

Salut!

---

