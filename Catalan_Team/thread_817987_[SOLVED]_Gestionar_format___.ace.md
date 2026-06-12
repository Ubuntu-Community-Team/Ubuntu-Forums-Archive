---
title: "[SOLVED] Gestionar format   .ace"
date: 2008-06-04
forum: Catalan Team
---

### Post by LitusMayol on 2008-06-04
Bon dia a la vila del pingüí!


Bon dia, sabeu com gestionar arxius *.ace*? Us explico, per l'aMule m'he baixat la discografia de **Gigatrón** (ho sé són *macho ibérico typical spanish*, però les seves lletres em fan riure molt). Doncs per sorpresa meva la discografia es va baixar a trentaqueté, però al anar a descomprimir l'arxiu: descobreixo que finalitza amb *.ace* i que quan faig click al damunt diu:

```
No s'ha pogut obrir «Gigatron - Discografia completa+videos+fotos+letras, cojonudo peña!, (by Max Mahony).ace»

Aquest tipus d'arxiu no es pot gestionar.
```

Algú sap com gestionar-lo? Com obrir-lo o com descomprimir-lo?


Merci de nou!

---

### Post by papapep on 2008-06-04
[http://packages.ubuntu.com/search?keywords=unace&searchon=names&suite=hardy&section=all](http://packages.ubuntu.com/search?keywords=unace&searchon=names&suite=hardy&section=all)

Últimament no fem gaire els deures, eh!... :-/

---

### Post by LitusMayol on 2008-06-04
> **papapep said:**
> [http://packages.ubuntu.com/search?keywords=unace&searchon=names&suite=hardy&section=all](http://packages.ubuntu.com/search?keywords=unace&searchon=names&suite=hardy&section=all)

Últimament no fem gaire els deures, eh!... :-/

Es que primer penjo el post... després busco... *jupé*! Ho sento! La setmana que ve els faré tots!
:lolflag:

hehehe, merci **papapep**!

---

### Post by LitusMayol on 2008-06-04
```
litus@mayolets-desktop:~$ sudo aptitude install unace unace-nonfree
[sudo] password for litus: 
S'està llegint la llista de paquets... Fet
S'està construint l'arbre de dependències       
Reading state information... Fet         
S'està llegint la informació d'estat estesa      
S'estan inicialitzant els estats dels paquets... Fet
S'està escrivint la informació d'estat estesa... Fet
S'està generant la base de dades de marcadors... Fet
Els paquets nous següents s'instal·laran:
  unace unace-nonfree 
0 paquets actualitzats, 2 instal·lats, 0 a suprimir i 0 a no actualitzar.

...

S'estan inicialitzant els estats dels paquets... Fet
S'està escrivint la informació d'estat estesa... Fet
S'està generant la base de dades de marcadors... Fet
litus@mayolets-desktop:~$ 

```


Després d'instal·lar, me'n vaig tot feliç a obrir el meu arxiu *.ace* i... S'obre el **Gestor d'Arxius** i així es queda, obrint. La barra taronja va rebotant eternament... 

Com l'obro? (com l'obro amb consola, perquè vegueu els errors, es que jo no ho sé fer...)

---

### Post by pespin on 2008-06-04
prova amb "unace nom_del-arxiu.ace"

---

### Post by papapep on 2008-06-04
> Com l'obro? (com l'obro amb consola, perquè vegueu els errors, es que jo no ho sé fer...)

```
man unace
```

:-)

---

### Post by LitusMayol on 2008-06-04
```
litus@mayolets-desktop:~$ cd /home/litus/.aMule/Incoming
litus@mayolets-desktop:~/.aMule/Incoming$ unace e Gigatron\ -\ Discografia\ completa+videos+fotos+letras\,\ cojonudo\ peÃ±a\!\,\ \(by\ Max\ Mahony\).ace 
```


solucionat.
En mode gràfic no puc però així ja va! ;) Merci als dos!

---

### Post by lo gambusí on 2008-06-05
Gigratrón? Déu meu XD

---

### Post by pespin on 2008-06-05
> **lo gambusí said:**
> Gigratrón? Déu meu XD

Sí, és un hijo del trueno, hijo del metal! xD

---

### Post by LitusMayol on 2008-06-05
:guitar: yeah! :P

---

### Post by SiscoGarcia on 2008-06-05
> **pespin said:**
> Sí, és un hijo del trueno, hijo del metal! xD

M'ho pots traduir? :-k

---

### Post by pespin on 2008-06-06
> **SiscoGarcia said:**
> M'ho pots traduir? :-k

Res, una simple conya/al·lusió a una cançó de Gigatrón xD [http://www.youtube.com/watch?v=5b-pVB4jk8s]("http://www.youtube.com/watch?v=5b-pVB4jk8s")

---

