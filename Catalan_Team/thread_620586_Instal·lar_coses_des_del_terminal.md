---
title: "Instal·lar coses des del terminal"
date: 2007-11-22
forum: Catalan Team
---

### Post by Bensy on 2007-11-22
Ja l'he tornada a fer. O no. No ho tinc massa clar.

Estic intentant instal·lar-me l'ePSXe, i com pràcticament tot fins ara, ho he buscat al google i m'he dedicat a copiar-pegar (encara que ara ja comence a deduir la sintaxi de la terminal, segueix costant-me). He trobat aquestes instruccions: [http://www.ubuntu-es.org/index.php?q=node/11348](http://www.ubuntu-es.org/index.php?q=node/11348) que pareixien les menys engorroses, però així i tot tinc problemes.

M'he quedat atrancat en el pas 8, Quan intente fer:

usuario@ubuntu:~$ sudo mv $EPSXE/plugins/cfgPeteMesaGL $EPSXE/cfg/
usuario@ubuntu:~$ sudo mv $EPSXE/plugins/gpuPeteMesaGL.cfg $EPSXE/cfg/
usuario@ubuntu:~$ sudo chmod 666 $EPSXE/cfg/gpuPeteMesaGL.cfg

no funciona. He intentat moure els arxius a mà (a vore si sonava la flauta) però en arribar a la darrera ordre, no em funciona. L'error diu que el directori o l'arxiu no existeix, però de fet em consta que si, ja que tinc una finestreta amb la carpeta oberta, i la ruta està ben escrita, els arxius són els mateixos (no he baixat el primer pedaç d'aquest pas, ni fet servir les ordres que li pertoquen perquè sí em funciona l'acceleració 3D, i segons la pàgina dels pedaços el mateix del tutorial és l'adient per a la meua targeta gràfica).

M'ha passat que s'havia calat internet i he hagut de reiniciar mentre estava fent açò, però no crec que siga aquest el problema, perquè no estava executant cap ordre quan ho he fet, i també m'ha passat mentre instal·lava altres coses, com ara VirtualBox, i no m'ha donat problemes mai a l'hora de continuar la instal·lació.

Moltes gràcies una altra vegada, sou uns solets :)

PS: Us deixe una còpia del que em diu el terminal, per si us cal mirar-ho.

bensy@LaCabaretera:~$ sudo mv $EPSXE/plugins/cfgPeteMesaGL $EPSXE/cfg/
[sudo] password for bensy:
mv: target `/cfg/' is not a directory: No such file or directory
bensy@LaCabaretera:~$

---

### Post by RainCT on 2007-11-23
Sembla que la variable $EPSXE ha perdut el valor al reinicia i que per això no busca al directori correcta. Torna-la a definir (busca la línia de les instruccions que comenci per «EPSXE=» i torna-la a executar) i prova un altre cop des d'on t'ha fallat, a veure si és aques tel problema.

Salut!

---

### Post by Bensy on 2007-11-23
Ah! Aixó era, moltes gràcies.

Ara ja ho he fet tota la instal·lació tal i com em diu, però en arribar al final, no marxa.

bensy@LaCabaretera:~/Games/ePSXe$ ./epsxe
bensy@LaCabaretera:~/Games/ePSXe$ epsxe
bash: epsxe: command not found

primer he provat com diu a les intruccions, però no piula, ni llevant-li el "./" ni amb sudo ni res. El cas es que l'arxiu si està dins de la carpeta (vaig mirant què hi passa allí per a aprendre què fa més o menys cada comandament).

També se m'ha quedat una carpeta temporal en l'escriptori, on m'he baixat els arxius per tindre'ls més controlats, en comptes de baixar-los a la carpeta temporal com deien les instruccions, i he canviat la ruta en l'ordre quan li pertocava. He descomprimit un arxiu tgz com deia allí, amb sudo i tal, i és clar, no tinc els permissos per esborrar-ho una vegada he posat cada cosa de dins la carpeta al seu lloc, i no m'atrevisc a inventar-me comandaments, no siga cosa que m'ho carregue tot.

Dubte final: si ho he posat tot dins del meu directory (/home/bensy/Games/ePSXe), que té la seua partició pròpia, en reinstal·lar Ubuntu si fóra necessari, hauria de retocar cap cosa ací? Ho dic perquè segons el que entenc de les ordres que he introduït, no he tocat res del sistema (libreries, etc...), com a molt els permissos, i si sé bé el que he fet, em quede més tranquil.

Moltes gràcies una altra vegada!!

---

### Post by papapep on 2007-11-24
Enganxa'ns el resultat de la ordre:

```
ls -la ~/Games/ePSXe/
```

---

### Post by RainCT on 2007-11-24
Pots modificar tots els arxius del sistema de manera gràfica obrint el navegador de fitxers com a root:

```
sudo nautilus
```


Per tal de poder canviar de forma normal els arxius aquests que has posat a la teva carpeta executa:

```
sudo chown bensy:bensy /home/bensy/Games/ePSXe -R
```

Això canviarà el propietari de tot el que hi ha al directori ~/Games/ePSXe per tal de que siguis tu :).

---

### Post by Bensy on 2007-11-24
bensy@LaCabaretera:~$ ls -la /home/bensy/Games/ePSXe/
total 264
drwxr-xr-x 13 bensy bensy    448 2007-11-23 17:48 .
drwxr-xr-x  3 bensy bensy     72 2007-11-23 00:06 ..
drwxr-xr-x  3 root  root     208 2007-11-23 18:06 bios
drwxrwxrwx  2 root  root     344 2007-11-23 17:18 cfg
drwxr-xr-x  2 root  root     160 2002-05-05 23:13 cheats
drwxr-xr-x  2 root  root     192 2003-08-04 23:18 docs
-rwxr-xr-x  1 root  root  149019 2003-08-04 22:52 epsxe
drwxr-xr-x  2 bensy bensy     80 2007-11-23 00:07 ePSXe Install files
-rw-r--r--  1 root  root    1719 2002-01-28 00:04 keycodes.lst
-rwxr-xr-x  1 root  root  108238 2007-11-23 16:55 libpthread.so.0
drwxrwxrwx  2 root  root     152 2007-11-22 23:58 memcards
drwxr-xr-x  2 root  root      48 2002-01-28 00:02 patches
drwxr-xr-x  2 root  root     392 2007-11-23 17:17 plugins
drwx------  2 bensy bensy    152 2007-11-23 00:21 scph1001
drwxrwxrwx  2 root  root      72 2002-01-24 22:43 snap
drwxrwxrwx  2 root  root      96 2002-01-28 00:03 sstates
-rw-rw-rw-  1 bensy bensy    193 2007-11-23 17:41 startepsxe.sh~

---

### Post by papapep on 2007-11-24
> -rw-rw-rw- 1 bensy bensy 193 2007-11-23 17:41 startepsxe.sh~

Aquí et surt un script que sembla que sigui per executar el programa aquest.

Enganxa el resultat d'aquesta ordre:

```
cat ~/Games/ePSXe/startepsxe.sh~
```

---

### Post by Bensy on 2007-11-25
bensy@LaCabaretera:~$ cat /home/bensy/Games/ePSXe/startepsxe.sh~
#!/bin/bash

export EPSXE='/usr/local/games/epsxe'
export LD_LIBRARY_PATH=$EPSXE
cd $EPSXE
./epsxe
chmod 666 $EPSXE/cfg/*.cfg $EPSXE/sstates/* \
$EPSXE/memcards/*.mcr $EPSXE/snap/* 2>/dev/null


Açó. Em fa poreta! ;_;

---

### Post by papapep on 2007-11-25
Res home, res!!! Com a molt provoques la 3a guerra mundial!!! :-D

Prova això:

Canvia el nom del fitxer per treure el ~ del davant:

```
mv /home/bensy/Games/ePSXe/startepsxe.sh~ /home/bensy/Games/ePSXe/startepsxe.sh
```

després, dóna-li permisos d'execució al nou fitxer:

```
chmod +x /home/bensy/Games/ePSXe/startepsxe.sh
```

i ara, prova a veure si funciona:

```
cd /home/bensy/Games/ePSXe/
```

```
./startepsxe.sh
```

---

### Post by Bensy on 2007-11-27
A vore, és que se'm va oblidar comentar una coseta. Espereu que vaig un moment al racó a fustigar-me. Es que als comentaris de la pàgina que vaig enganxar hi havia un altre link, que és d'on han tret quasi tot, que és on diu com fer eixe script (que encara que m'ajudeu també intente apanyar-me també, a vore si us estalvie feina). Però tot i aixó no va piular. [http://www.ubuntu-es.org/node/8637](http://www.ubuntu-es.org/node/8637)

Total, que vaig trobar un repositori que es podia afegir per a que se t'instal·li tot en un momentet. Però solucionar açò a maneta em fa il·lusió també... Ara provaré el que m'has dit, a vore si puc fer-ho anar.

Per cert, em diu que el fitxer amb ~ no hi és.

---

