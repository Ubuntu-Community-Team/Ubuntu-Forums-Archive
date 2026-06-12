---
title: "[SOLVED] Problemes amb drivers: e1000 i e1000e"
date: 2008-08-14
forum: Catalan Team
---

### Post by JosepRibes on 2008-08-14
Hola companys,

ja fa uns quants dies que m'estic esbarrallant amb la posada amb funcionament d'uns ordinadors amb ubuntu. El problema recau en que la tarja de xarxa d'aquests ordinadors utilitza el driver e1000e, i amb això no hi ha manera de conectar a la xarxa. He estat llegint per molt forums i pel que he entes s'ha d'utilitzar el driver e1000 enlloc del e1000e. 
He probat de conectar un altra tarja de xarxa (realtek 8139) per tal d'actualitzar i aveure si amb alguna actualització es solucionava el tema però tot continua igual.
La meva pregunta és: es pot forçar la utilització del driver e1000 enlloc del e1000e?

Moltes gràcies.

Josep Ribes.

---

### Post by papapep on 2008-08-14
Un cop sàpigues el nom exacte dels dos mòduls, afegeixes una línia al fitxer */etc/modprobe.d/blacklist* en el format  (suposant que el nom del mòdul que no vols que es carregui sigui 'e1000e') següent:

```
blacklist e1000e
```

i el que sí que vols que es carregui l'afegeixes al fitxer */etc/modules*, darrera els que ja hi hagi:

```
e1000
```

---

### Post by JosepRibes on 2008-08-19
Hola de nou, 

he probat el que heu proposat i tot continua igual. no es força la carrega del driver. despres de probar i probar resulta que en una de les 11 maquines que estic instal·lant SI que funciona be la xarxa amb el driver e1000e i aixo ja m'ha descologat del tot. tots els ordinadors estan a la versio de kernel 2....19. i en totes elles he seguit els mateixos pasos d'instal·lació. 

Hi ha alguna forma de clonar unicament la partició d'ubuntu a la resta de màquines aprofitant que una de les maquines ja funciona correctament? Es tracta d'una aula dual (innombrable i ubuntu). 

A més, el curiós del cas es que en aquests ordinadors he "punxat" una tarja de les velles (realtek pci barateta) i a l'hora de mirar quines interficies de xarxa tinc surt correctament el nom de la tarja de xarxa que dona tants problemes. Aixo vol dir que ubuntu sap ben be quina tarja te instal·lada si i només si quan hi "punxem" una altra tarja de xarxa??   El nom de la tarja és: Intel 82562V-2.

No se per on continuar. 

Que en penseu? 

Josep Ribes.

---

### Post by papapep on 2008-08-19
Has provat el que diu [aquí]("http://ubuntuforums.org/showpost.php?p=3050436&postcount=4")?

En tot cas, si vols provar-ho, en vers del controlador de l'enllaç descarrega [aquest]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&Inst=Yes&ProductID=998&DwnldID=9180&strOSs=39&OSFullName=Linux*&lang=eng"), que és el més actualitzat.

---

### Post by patrickfromspain on 2008-08-19
la manera bestia de fer-ho:

carrega't l'arxiu e1000e.ko (o copia'l a algun lloc fora de /lib/modules)

---

### Post by JosepRibes on 2008-08-21
Hola companys,

he seguit els pasos del papapep i tot ha funcionat correctament.
no he probat el que diu el patrickfromspain, per tant, feu cas a la resposta que dona el papapep, ja que és la que a mi m'ha funcionat. He de comentar que un cop carregat el driver i fet el:
/etc/init.d/networking restart   cal tenir una mica de paciencia, ja que si de seguida intenteu fer un ping a una web per comprovar el correcte funcionament, aquest no és inmediat, cal donar-li una miqueta de temps a que tot es fiqui a lloc, jeje (uns 10 segons més o menys).

Moltes gràcies per tot.

---

