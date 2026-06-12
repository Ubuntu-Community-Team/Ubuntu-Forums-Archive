---
title: "arxiu .mht"
date: 2008-02-21
forum: Catalan Team
---

### Post by rogespierre on 2008-02-21
uns apunts que he d'usar estan en .mht i no ho puc obrir. He llegit en altres fils que el navegador opera els pot obrir però tampoc m'ho fa... és més, em diu que l'arxiu està optimitzat per a explorer...

hi ha alguna manera que els pugui obrir sense anar-me'n al windows?

---

### Post by papapep on 2008-02-21
Hi ha una eina per KDE que es diu kmhtconvert, hi ha una solució per l'Opera que solventa el que no els llegeixi de sortida:

> Type application/mime in "Mime type" and mim,mime,mht,mhtml in "File extensions", then check the action "Open with Opera".

---

### Post by rogespierre on 2008-02-21
ok, l'he convertit a format .war ..pero ara com l'obro? ni am firefox ni am opera puc

---

### Post by papapep on 2008-02-21
Saps què passa, que no tinc ni idea del format mht (ni ganes) ni de com funciona el kmhtconverter. Només he buscat informació per passar-te-la. Ni tan sols sé perquè has passat els mht a war.

A partir d'aquí, potser hauries de buscar una miqueta per la xarxa a veure què expliquen al respecte.

---

### Post by guillemsola on 2008-02-21
En aquest post ho expliquen pas per pas per obrir-los directament al firefox. Thread 26

Això si, està en guiri...

[http://ubuntuforums.org/showthread.php?t=495131&page=3](http://ubuntuforums.org/showthread.php?t=495131&page=3)

Sort!

---

### Post by marcoil on 2008-02-21
> **rogespierre said:**
> ok, l'he convertit a format .war ..pero ara com l'obro? ni am firefox ni am opera puc

Un arxiu .war és una aplicació web en Java, en teoria és un arxiu .zip. L'hauries de poder obrir amb el Gestor d'Arxius.

---

### Post by lluisanunez on 2008-02-21
Però en format war no pot obrir-ho cap navegador.
Això del mht és un invent del diable que en realitat emmascara html , javascript i imatges perquè només es puguin obrir amb l'IExplorer. 
Si no et queda més remei insta&#320;la't l'Explorer amb wine, però no deixis d'enviar una queixa, perquè no és manera de publicar apunts. Fins i tot amb el Hasefroch hi ha versions que tenen problemes per a usar això

ECS!

---

### Post by rogespierre on 2008-02-24
**angrychai:** ara miraré de seguir aquest post

**marcoil:** s'executa amb el gestor d'arxius pero em dona error

**lluisanunez**: Sí, ja havia pensat enviar-li al professor, només faltaria que a les universitats també anem amb aquest pal...

he instal·lat el wine per a tal fi.. pero no veig ben bé q faig, com s'instal·la l'explorer? a configuració l'he afegit per alguna banda crec... i hi ha una opcio d'explorar com un C: virtual, alla executo iexplorer.exe pero es una finestra tota blanca...

---

### Post by papapep on 2008-02-24
Si només et cal l'explorer igual en tens prou amb [ie4linux]("http://www.tatanka.com.br/").

Has provat a descomprimir els war amb?:

```
jar -xvf [fitxer war] 
```

I respecte el format, és que mira que en tenen de diferents per fer-ne servir. Sembla ben bé que sigui per tocar allò que no sóna...

---

### Post by Ganton on 2008-07-09
En la web del kmhtConvert diuen:

kmhtConvert is an mht (Windows Web Archive) file to war (KDE Web Archive) file converter.

Aixina que no és un "war" dels de Java.

Si tinc un "war" anomenat 'AMI200.war' i execute
$ file   'AMI200.war'
em contesta:
$ AMI200.war: gzip compressed data

Amb lo que podem descomprimir-ho usant un descompresor que usem normalment. També podem visualitzar el .war usant el Konqueror, però si no el tens instal·lat ja, millor descomprimir els arxius de dins.

---

