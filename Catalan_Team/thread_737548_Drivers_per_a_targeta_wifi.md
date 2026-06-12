---
title: "Drivers per a targeta wifi?"
date: 2008-03-27
forum: Catalan Team
---

### Post by pastanaga1 on 2008-03-27
Bé, primer de tot em presento, sóc de mataró (maresme) i estic preparant la meva migració a Linux, hi un problema amb el que m'he topat es que la meva targeta wifi, no té drivers compatibles per a linux. És una EDIMAX EW-7318USg "Wireless Hi-Gain USB Adapter". El que si que he trobat és una web, en anlès, que pot ser la solució però no en tinc NI IDEA d'anglès. és aquesta : [AQUI]("http://www.lockergnome.com/linux/2007/11/04/ubuntu-gutsy-with-expresscard-working-options/")
Gràcies de manera anticipada

salut

---

### Post by papapep on 2008-03-27
Benvingut pastanaga1, et convido a passar-te pel fil de benvinguda i a fer "oficial" la teva presentació. També estaria bé, si no ho has fet ja, que facis una bona llegida al fil pels que acaben d'arribar: [http://ubuntuforums.org/showthread.php?t=599965](http://ubuntuforums.org/showthread.php?t=599965)

Respecte la teva targeta usb de wifi, a l'enllaç que has posat diuen que funciona correctament fent servir el mòdul rt73usb, o sigui que no és que no tingui controlador per linux (segons diu el mosso aquest, clar).

L'script que has de descarregar i executar, el que fa es no deixar que es carregui un mòdul [1] (controlador) que suposo que deu intentar carregar el kernel de linux en detectar la teva targeta (i que no deu funcionar) i, posteriorment, carregar el mòdul correcte [2]. Finalment reinicia el servei de xarxa per carregar la configuració actual [3].

```
#! /bin/sh -f
[COLOR="Red"][1][/COLOR] echo 'blacklist rt2500usb' | sudo tee -a /etc/modprobe.d/blacklist
sleep 2
[COLOR="Red"][2][/COLOR] gksudo modprobe rt73usb
sleep 3
iwconfig
sleep 7
[COLOR="Red"][3][/COLOR] sudo /etc/init.d/networking restart
sleep 3
```

Un cop tinguis l'Ubuntu instal·lat, ja veuràs que no és complicat fer-ho.

---

### Post by sianeu on 2008-03-28
He pillat aquesta tarja per a un familiar i ara mateix l'estic fent servir per provar el nou Ubuntu Hardy. L'ha detectada sens cap problema des del mateix live CD (amb protecciò WEP, el WPA encara no l'he provat). Pots provar-lo o esperar el poc que falta per que surti la versió estable.

Salut

---

### Post by papapep on 2008-03-28
Collonut! Més ferro al sac ;-)

---

### Post by joant on 2008-03-28
La solució, com comentes, es diu Hardy Heron. Amb la dapper i la feisty em vaig barallar fins no poder més per provat d'instal·lar no una, ni dues, ni tres ... fins a 4 adaptadors wifi per USB, sense aconseguir res. Amb la gutsy vaig aconseguir-ho amb un adaptador CONCEPTRONIC. Els altres, res de res. I ara m'he instal·lat la beta del Hardy i oli en un llum. El salt en detecció d'aquests dispositius ha estat, amb aquesta darrera distribució, abismal.

No us trenqueu més el cap, actualitzeu a Hardy. Que, per cert, tret de que li falta molt per traduir al català, a mi no m'ha donat encara cap problema ni un, tot i ser beta.

Salut.

Joan T.

---

### Post by dafaktor on 2008-04-03
Jo he probat la alpha6 de la hardy en un pc amb una conceptronic amb xipset rt2500 i m'ha anat bé.

a veure si en el portàtil, que és el que faig servir habitualment, també funciona correctament i millora el suport per a la wifi que incorpora, també basada en una rt2500, ja que la gutsy funciona però a mitges.

soc molt nou en el món linux/ubuntu però, com he dit en el fil de presentació, n'estic enamorat i ja he atret a dos companys més cap a la banda Ubuntera !

---

### Post by patrickfromspain on 2008-04-03
jo estinc fent servir la hardy al meu pc amb un adaptador inalambric i li he de passar l'ordre sudo iwconfig rate 11M perque sino s'em connecta a 1Mbps

salut

---

### Post by jodufi on 2008-04-03
Tinc una amiga que portava mesos intentant que li funciones al WiFi sense cap sort i moltes hores invertides.
Amb la beta del Hardy li ha funcionat «de serie» sense cap problema :)

---

### Post by dafaktor on 2008-04-04
> **patrickfromspain said:**
> jo estinc fent servir la hardy al meu pc amb un adaptador inalambric i li he de passar l'ordre sudo iwconfig rate 11M perque sino s'em connecta a 1Mbps

salut

A mi em passa exactament el mateix. A veure si ho solucionen.

---

### Post by papapep on 2008-04-04
Mentrestant podeu fer que s'executi a cada arrencada i així no l'haureu de picar manualment.

---

### Post by dafaktor on 2008-04-04
> **papapep said:**
> Mentrestant podeu fer que s'executi a cada arrencada i així no l'haureu de picar manualment.

je je je... i propera pregunta de "novato" és: com ho fem això?

---

### Post by papapep on 2008-04-04
Tots ho hem estat, i alguns mai ho deixarem de ser, de novells, "no problemo".

Fes un script que tingui el següent:

```
#!/bin/bash
iwconfig rate 11M
```

el deses, amb el nom que et vingui de gust, dins el directori **/etc/init.d** (amb els permisos adients, clar, i cal que sigui executable "chmod +x fitxeret".).

Després executes:

```
sudo update-rc.d fitxeret defaults 
```

I ja hauria de funcionar tot plegat. ;-)

---

### Post by ernestux on 2008-04-04
[Fes un script que tingui el següent:

```
#!/bin/bash
iwconfig rate 11M
```

el deses, amb el nom que et vingui de gust, dins el directori **/etc/init.d** (amb els permisos adients, clar, i cal que sigui executable "chmod +x fitxeret".).]

Pregunta de novato: Tots els scipts es desen al directori /etc/init.d ? 
Hi ha algun enllaç senzillet i maco que expliqui el tema sript ?

P.D. Potser això que faig se'n diu "segrestar un fil..."

Ernest

---

### Post by papapep on 2008-04-04
> Pregunta de novato: Tots els scipts es desen al directori /etc/init.d ?

No, només els que vulguis que s'executin, i en casos concrets no s'ha de fer així, al arrencar l'ordinador.

> Hi ha algun enllaç senzillet i maco que expliqui el tema sript ?

No que jo conegui. El primer que et cal és entendre el funcionament intern (tampoc cal convertir-se en un hacker) de Linux. Sistema de fitxers, estructura de directoris, funcions bàsiques del sistema, etc. Aleshores buscant "bash scripting" a Google trobaràs milions de documents.
El primes que has de controlar una mica són les ordres de terminal, sinó és com intentar fer la travessa de l'Estret sense haver aprés a nedar abans.

> P.D. Potser això que faig se'n diu "segrestar un fil..."


Tu ho has dit. :-)

---

### Post by patrickfromspain on 2008-04-04
Jo no dire la meva manera perque implica tenir el sudo sense password i el papapep em renya :)

PD: ja ho se, es una xapuça!

---

### Post by CarlesOriol on 2008-04-05
Fas bé de no dir-ho per que si arribes a dir alguna cosa com:

echo lamevapasswordsupersecreta | sudo -S elquevullexecutar

segur que el càstig hauria estat descomunal.

---

### Post by patrickfromspain on 2008-04-05
bé...jo... es que tinc TOT el sudo sense password xD

---

