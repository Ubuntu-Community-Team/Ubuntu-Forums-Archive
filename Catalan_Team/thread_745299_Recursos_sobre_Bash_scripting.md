---
title: "Recursos sobre Bash scripting"
date: 2008-04-04
forum: Catalan Team
---

### Post by papapep on 2008-04-04
Com que l'Ernestux ha tret el tema, si hi ha gent que té ganes de mirar -s'ho, us deixo uns quants enllaços interessants (algun d'ells en anglés):

*** Les quatre coses bàsiques:**
[https://wiki.ubuntu.com/CatalanTeam/Recursos/Int%C3%A8rpretComandes](https://wiki.ubuntu.com/CatalanTeam/Recursos/Int%C3%A8rpretComandes)

*** TLDP, com no:**
(EN) Bàsic: [http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html)
(EN) Avançat: [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

(ES) [http://es.tldp.org/COMO-INSFLUG/COMOs/Bash-Prog-Intro-COMO/](http://es.tldp.org/COMO-INSFLUG/COMOs/Bash-Prog-Intro-COMO/)
(ES) [http://es.tldp.org/COMO-INSFLUG/COMOs/Bash-Prompt-Como/](http://es.tldp.org/COMO-INSFLUG/COMOs/Bash-Prompt-Como/)

*** Wikipedia: **
(ES) [http://es.wikipedia.org/wiki/Bash](http://es.wikipedia.org/wiki/Bash)

Un curs que sembla interessant, prou bàsic:
(ES) [http://www.aprendeaprogramar.com/course/view.php?id=10](http://www.aprendeaprogramar.com/course/view.php?id=10)

---

### Post by niculau on 2008-04-04
Molt interessant, jo vaig començar a estudiar "informàtica" amb ms-dos i tot això em resulta molt familiar, però tinc un petit dubte després de llegir la primera lliçó, que per cert m'ha agradat molt, molt ben redactat. 
Tinc un munt de processos en marxa (firefox, trasmission, etc...) però no apareixen quan teclejo l'ordre "ps" o "jobs" nomes apareixen els del exemple, Per tant com els puc "matar"?

salut

---

### Post by orestesmas on 2008-04-04
Jo normalment faig
```

ps axf

```
per tal que em surtin tots, i endreçats per pare-fill. Nota: els que surten entre corxets rectes [ ] són processos del nucli.

Mira't el manual:
```

man ps

```

---

### Post by papapep on 2008-04-04
Per buscar un procés en concret, jo faig:

```
ps -e|grep nomdelprocés
```

Per exemple, ara si faig:

```
ps -e|grep firefox

```

em mostra:

```
17126 ?        00:05:59 firefox
```

a partir d'aquí, fent un:

```
kill 17126
```

i si és fa el dur i no es vol deixar matar:

```
kill -9 17126
```

pots aturar-lo.

Existeix també un programet per terminal de nom [htop]("http://htop.sourceforge.net/"), que es troba als repositoris, el qual a banda de mostrar la càrrega del sistema permet gestionar els processos de manera prou fàcil i pràctica.

També hi ha un programa gràfic al menú de Gnome (Orestes no miris, que t'agafarà urticària) **Sistema > Administració > Monitor del sistema** que fa una cosa semblant, però què voleu que us digui, acabo abans pel terminal jo :-D

---

### Post by niculau on 2008-04-04
gracies, es clar amb aquest "man" ara tinc molta mes informació. 

Potser per a mi es mes entenedor el senzill "ps -e" ara com ara serà tot qüestió de memòria.

Si, el monitor de sistema ja el conec, gràficament l'he patejat bastant l'ubuntu, però intento no evitar fer servir el terminal.



Ep el "htop" aquest està molt bé, gasta molts menys recursos que el monitor del sistema, que l'engego per controlar la cpu i se m'he la menja tota, m'ha agradat.

---

