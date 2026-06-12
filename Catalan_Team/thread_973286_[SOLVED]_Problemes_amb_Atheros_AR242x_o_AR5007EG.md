---
title: "[SOLVED] Problemes amb Atheros AR242x o AR5007EG"
date: 2008-11-06
forum: Catalan Team
---

### Post by freski on 2008-11-06
Hola! Acabo d'actualitzar l'Ubuntu a la versió 8.10 de 32 bits i, com era d'esperar, he tingut problemes amb la targeta wifi (o com es digui). La targeta és una **Atheros AR242x** // **AR5007EG**, i amb la versió 8.04 ja m'havia donat problemes, però els havia aconseguit solucionar.

El problema és que ja per començar actua com si no em reconegués la targeta, així que tampoc em detecta les xarxes d'internet sense fil.

A veure si algú em pot ajudar. Moltes gràcies!

---

### Post by decoherence on 2008-11-06
I don't speak the language, but I think what you want is to enable the backports repository and install the package "linux-backports-modules-intrepid"

Then restart or type 'sudo modprobe ath5k'. Hope that helps. Sorry, I can only speak english (is there a translator in the house?)

Bug report is here
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/289014](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/289014)

---

### Post by freski on 2008-11-07
Algú em pot explicar com activo el repositori dels backports (o com es digui això)? Gràcies!

---

### Post by SiscoGarcia on 2008-11-07
Per activar els backports has de fer-ho triant les fonts de programari a "Sistema>Administració>Fonts de programari" i allà, després de validar-te, obres la pestanya que hi diu "Actualitzacions" i selecciones les fonts de programari que vols fer servir. Fes-ho amb compte de què tries, ja que els backports són actualitzacions no suportades oficialment ;)

---

### Post by tanreb20 on 2008-11-07
(El volai esvriure fa 3 dies ja...)

Jo tinc aquesta mateixa tarjeta, i he aconseguit ferla rular amb el ndiswrapper i el seu driver corresponent.

A risc de no se politicament correctament, ja que sempre es diu que demanem mes dades i tot aixo...

T'explico com u vaig fer, i si no et va, no perds res, no?

```
sudo aptitude install ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
```

Després, amb Alt + F2 => 

```
gksu ndisgtk
```
(el gksu es perque et demani la contrasenya.. que sino no podras fer res...)

i després i poses els drivers, jo et passo els que tinc jo, per la atheros que tu tens... a veire si et funciona

* Has de agafar l'arxiu .inf

Llavors, esperar una estona i en principi et començara a detectar les xarxes wifi

Espero que et serveixo, i ja et dic... no se si es la solucio.. epro alguna cosa és alguna cosa.

PD: A vegades he de borrar el driver i tornar a posar-lo perque funcioni quan torni a obrir el PC al cap d unes hores...

---

### Post by papapep on 2008-11-07
> (el gksu es perque et demani la contrasenya

Matització: el gksu serveix per executar ordres amb drets d'administració i _per a això_ et demana la contrasenya. La contrasenya no és un fi, és un mitjà.

El concepte és important :-)

---

### Post by tanreb20 on 2008-11-07
Ups

---

### Post by SiscoGarcia on 2008-11-08
> **papapep said:**
> El concepte és important :-)

Jo matisaria la importància del concepte, sense entendre'l no podem entendre què fem, i llavors és gairebé com si ens trobéssim al costat fosc :)

---

### Post by freski on 2008-11-08
Moltes gràcies a tots! La solució aportada per en *tanreb20* m'ha funcionat satisfactòriament. Esperem que duri!

---

### Post by tanreb20 on 2008-11-08
Doncs marca el post com a [SOLVED]

---

### Post by blauigris on 2008-11-14
Ja se que arribo tard, però l'altre dia, a un amic meu que té la mateixa targeta, vam poder instalar el driver natiu, el de madwifi, compilant una hal especial (no vaig acabar de entedre ben bé que era) que si a algú li interessa ja miraré d'on ho vam treure. Ho dic perque ara li funciona de conya, veu un colló d'AP's i a més injecta. Ara bé, si fa poc que estàs a linux i no et cal fer virgueries jo millor ho deixaria per a més endavant.

---

### Post by dafaktor on 2008-11-17
A mi m'ha funcionat perfectament la solució que ha proposat el company decoherence.

Thanks so much decoherence!!

---

