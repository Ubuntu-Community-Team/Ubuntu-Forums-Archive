---
title: "VLC MediaPlayer, no para mai..."
date: 2008-04-01
forum: Catalan Team
---

### Post by prostata on 2008-04-01
Doncs que a part de lo malament que te la vista qui gestiona el fòrum,  em recorda  l'LSD, no és conya, lo de l'LSD... doncs que fa uns dies el VLC MediaPlayer, quan el paro de forma manual, ell solet continua treballant i malgrat no veure  la imatge, evidentment, si que continuo escoltant el só de la peli...alguna idea???

gràcies..

PS, algú coneix l'administrador de la web, ho dic per la coloraina... ;-)

---

### Post by orestesmas on 2008-04-01
Avui és el dia dels innocents. Demà arreglarant això dels colors.

---

### Post by pespin on 2008-04-01
El procés es deu quedar obert suposo... Prova a fer un 

```
ps -ef | grep vlc
```

o similars (no utilitzo el vlc i no et puc dir el nom xacte del procés jeje)

sortirà una cosa com aquesta:
```
usuari    5719     1  4 17:54 ?        00:05:44     vlc
```

El primer nombre és el PID. Per tancar el procés pots fer llavors:


```
kill 5719
```

A veure si així para. :)

---

### Post by niculau on 2008-04-01
a mi també em passava, la meva solució es en mode gràfic, obres el monitor de sistema (sistema/administració) i et sortirà un procés anomenat "wxvlc" el selecciones i marques "finalitzar el procés"

be, de fet no es cap solució, però així podràs tancar el procés exactament no se perquè passa, tampoc m'he dedicat a investigar-ho


salut

---

### Post by prostata on 2008-04-02
Gràcies per les respostes, he provat les dues i les dues funcionen, malgrat això voldria saber, si fos possible, com de sopte i sense haver fet res, s'ha creat aquesta anomalia. 

salut.

---

### Post by niculau on 2008-04-02
a mi de sobte i sense fer res se'm va arreglar sol.

salut

---

### Post by prostata on 2008-04-02
> **niculau said:**
> a mi de sobte i sense fer res se'm va arreglar sol.

salut


Ostres....!!!! això ja sembla windows.................., ep!!! és conya, és conya...!!!!, però...en això, si que s'ha sembla, ho dic per la màgia, ara funciona, ara no funciona... ;-)

---

### Post by papapep on 2008-04-02
La diferència rau en que en Ubuntu això passa per què en fer alguna actualització de les que es fan, alguna llibreria o programa arregla el problema. I si algú es dediqués a buscar a les bases de dades d'errors dels desenvolupadors això segur que hi consta. A Windows mai es sap el perquè de les coses....lleugera diferència.

---

