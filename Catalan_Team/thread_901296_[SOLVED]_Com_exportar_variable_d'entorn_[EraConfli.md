---
title: "[SOLVED] Com exportar variable d'entorn [Era:Conflicte amb software de diseny]"
date: 2008-08-26
forum: Catalan Team
---

### Post by carlesbm on 2008-08-26
Hola ha tothom

  Us vull plantejar la següent qüestió referent ha un programa de disseny de circuits impresos PCBs anomenat Eagle.

  L'altre dia el vaig instal·lar al Ubuntu i tot va anar be però les finestres apareixien com transparents i es feia totalment impracticable, vaig començar ha cercar per la xarxa i he localitzat una solució, el problema es que no ser massa be com l'he d'aplicar. Segons el que he pogut trobar cal escriure un petit codi en forma de script ho podeu veure en la següent web
      
       [http://www.minipop.org/](http://www.minipop.org/)

  El codi que cal introduir es: 

*"What you have to do is to launch this command 'export XLIB_SKIP_ARGB_VISUALS=1' before eagle . In my case i write a simple script that does just that, renamed it as 'eagle' and renamed eagle to 'eagle1' and voila Eagle Cad is working with compiz."*


[B]#!/bin/sh
export XLIB_SKIP_ARGB_VISUALS=1
exec /opt/eagle/bin/eagle1[/B]

    Com he de introduir aquestes 3 linies?

Moltes gracies per la vostra ajuda

Carles

---

### Post by papapep on 2008-08-26
Pots ficar l'exportació de la variable (export XLIB_SKIP_ARGB_VISUALS=1) dins /etc/profile (per a tot el sistema) o dins ~/.profile (només pel teu usuari) i executar el programa normalment

o bé,

si realment vols crear l'script que has posat, doncs crees un fitxer amb el nom que vulguis i extensió .sh, li dones permisos d'execució i ja està:

```
nano executaeagle.sh
```

dins hi fiques el codi que has esmentat abans:

```
#!/bin/sh
export XLIB_SKIP_ARGB_VISUALS=1
exec /opt/eagle/bin/eagle
```

deses amb Ctrl+X i prement intro.

Un cop fet això, li dones permisos d'execució:

```
chmod +x executaeagle.sh
```

i ja hauria de funcionar. L'invoques (sí, a cops és una mica esotèric el tema...):

```
./executaeagle.sh
```

i tot plegat hauria de funcionar.

---

### Post by pespin on 2008-08-26
Ep, en papapep t'ho ha posat tal qual surt a l'exemple que has dit, però no se n'ha adonat que  al teu exemple deia que renombrava l'arxiu, i ell no ha posat res d'això.

Segurament si no toques res de l'executable que ja tens del programa, l'script és així (eagle en comptes d'eagle1):
```

#!/bin/sh
export XLIB_SKIP_ARGB_VISUALS=1
exec /opt/eagle/bin/eagle
```

---

### Post by oriolsbd on 2008-08-26
Hola, com a comentari, he provat d'instal·lar-me l'eagle, i en Ubuntu no l'executable no s'instal·la a /opt/eagle/bin, sinó a /usr/bin. O sigui que ho hauries de tenir en compte en totes les instruccions anteriors.

Apart d'això, tot i que el que comenta en Papapep és correcte, el que indica a les instruccions que ens passes seria més aviat:

1- Renombrar l'executable d'Eagle com a eagle 1:
```
mv /usr/bin/eagle /usr/bin/eagle1
```

2- Crear un nou executable amb el mateix nom que l'anterior:
```
nano /usr/bin/eagle
```
A aquest fitxer, s'hi ha de posar el codi que esmentaves en el teu correu original (amb l'"1" al darrere):
```
#!/bin/sh
export XLIB_SKIP_ARGB_VISUALS=1
exec /usr/bin/eagle
```

3- Donar permisos d'execució a aquest nou executable:
```
chmod +x /usr/bin/eagle
```

D'aquesta manera, tens l'avantatge que et serveix la mateixa opció de menú que utilitzaves fins ara. Ara, també té els seus desavantatges. Si hi ha alguna actualització de l'Eagle, quan s'instal·li s'escriurà sobre el teu executable, i ho hauràs de tornar a fer.

De tota manera, encara que siguin diferents de les instruccions que vas trobar, crec que el millor és seguir les indicacions que ha escrit en Papapep (suposo que no ho has dubtat en cap moment :-) ) i, apart de fer el que ell diu, modificar el menú corresponent perquè executi la seva shell en comptes del executable original. Això ho podràs fer des de "Sistema>Preferències>Menú Principal".

Salut!

---

### Post by carlesbm on 2008-08-26
Gracies de seguida que pugui ho provaré, i ja us diré que tal ha anat.

    Tinc la curiositat per saber quina acció realitza aquest script per tal de poder entendre molt millor que estic fent.


    Gracies

---

### Post by papapep on 2008-08-26
El que fa és exportar una variable d'entorn amb un valor concret.
La variable és **XLIB_SKIP_ARGB_VISUALS**, i el valor que se li assigna és **1**.

Les variables d'entorn són això, variables, que estan disponibles independentment del programa, per això es diuen "d'entorn", ja que són al sistema operatiu, fora del programa tot i que, normalment, són accessibles per aquests, que les fan servir. N'hi ha d'usuari, per un en concret, i de sistema, per a tots els usuaris, i això, a Gnu/Linux, depèn de on i en quin moment es declarin (s'exportin). 
La resta de l'script és el "[shebang]("http://en.wikipedia.org/wiki/Shebang_(Unix)")", inici necessari per a qualsevol script de [bash]("http://ca.wikipedia.org/wiki/Bash") (seria #!/bin/bash o #!/usr/bin/bash o similar) o, en aquest cas d'[sh]("http://es.wikipedia.org/wiki/Bourne_shell") (#!/bin/sh).
La última línia, evidentment, és la que crida l'executable que vols executar (valgui la redundància).

No sé si t'ho he aclarit suficientment.

---

### Post by carlesbm on 2008-08-26
Hola de nou

   Us comunico que ja esta solucionat tot ique ha costat una mica, adjunto les linies de codi finals per tal de facilitar a altra gent el poder solucionar-ho.


#!/bin/sh
export XLIB_SKIP_ARGB_VISUALS=1
exec /usr/bin/eagle


Agraïr la vostra ajuda

---

### Post by carlesbm on 2008-08-27
Hola ha tots 


    [SIZE="6"]**Comunico**[/SIZE] ha tot el que li pugui interessar i utilitzi el EAGLE per ha fer PCBs que si utilitzeu la nova versio que hi ha al web de Cadsoft la 5.2.0, el problema ja esta solucionat, la una pega insignificant es que tindreu que crear manualment l'acces directe per poder executar el programa.

---

