---
title: "Lectura d'un fitxer"
date: 2008-11-19
forum: Catalan Team
---

### Post by dorcap on 2008-11-19
Bona nit:
Tinc un exercici per fer amb un punt del que no trobo la solució.
Es tracta de fer un guió de shell al que, passant-li un patró per paràmetre en l'executar-lo, em contesti amb el número de fitxers del directori actual que contenen aquest patró.
Ho tinc pensat i sé com obtenir facilment un fitxer que contingui, a una línia per fitxer, el directori actual. El que em fa falta és llegir sequencialment les línies de fitxer, per després aplicar-hi el filtre que em digui si contenen el patró i fer el compte de les que han passat la prova d'igualtat amb el patró. NO SÉ COM LLEGIR EL FITXER PER TENIR SEQUENCIALMENT LA LÍNIA ACTUAL EN UN VARIABLE I DETECTAR LA FI DE LA LECTURA. La resta ja sé com  fer-la.
Gràcies

---

### Post by papapep on 2008-11-19
Uuuuuuuuiiiiii, m'has tocat la fibra!!! :-D

Les ordres de terminal són brutals per aquestes cosetes.
Un simple:

```
ls -a |grep -c "patró"
```

et donarà el que vols. Ara només et cal modificar-ho per fer-ho funcionar dins un guió amb la variable que li passaràs i ja estarà :-)

És el que volies? (Ah! i no et caldrà per a res el fitxer intermig...)

PS Si vols alguna cosa més avançada, [sed]("http://unixhelp.ed.ac.uk/CGI/man-cgi?sed") i [awk]("http://unixhelp.ed.ac.uk/CGI/man-cgi?awk") poden fer virtualment qualsevol cosa que vulguis...

PS2 Una [pista]("http://www.ibm.com/developerworks/library/l-bash2.html") de com fer-ho, per si no ho veiessis clar.

---

### Post by papapep on 2008-11-20
[Aquí]("http://www.gnu.org/software/gawk/manual/") pots trobar un manual de [gawk]("http://www.nrl.navy.mil/code5595/online-software/manpages/gawk-manpage.html") (awk de gnu) que vaig fer servir en un moment puntual que em va fer falta i que és molt bo.

---

