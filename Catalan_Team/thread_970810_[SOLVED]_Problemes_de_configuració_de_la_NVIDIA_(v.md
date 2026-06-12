---
title: "[SOLVED] Problemes de configuració de la NVIDIA (visquin les actualitzacions xD)"
date: 2008-11-04
forum: Catalan Team
---

### Post by LitusMayol on 2008-11-04
Bones familiaa!


Ahir no vaig tenir cap problema amb la meva flamant *intrèpid*. Però avui al encendre l'ordinador s'ha queixat. Resulta que no suporta la NVIDIA que tinc. 

Abans tenia els drivers del paquet *nvidia-glx-new* però ara han canviat aquest paquet. El sistema em deia que instal·lés el paquet "*nvidia-glx-177*". Però amb aquest ni tan sols podia engegar les X. He provat amb tots els "*nvidia-glx-*"177,173,96,71... I cap em deixa passar de la resolució de 800x600. També he provat fent córrer "*sudo nvidia-xconfig*" al terminal. Però no serveix de re... M'obre una avís al taulell superior que em diu que m'he d'instal·lar el paquet "*nvidia-glx-177*". Però com ja he dit: no funciona.

El problema és que no sé quina NVIDIA tinc i que no sé com mirar-ho. He pensat que anant a [aquí]("http://www.nvidia.com/Download/index.aspx?lang=en-us") i baixant-me els drivers ja ho tindria solucionat. Però sense saber la meva targeta no puc arreglar-ho... 

Algú sap com puc mirar el model d'NVIDIA que tinc? I com arreglar el problema?

Merci

---

### Post by indiosincracia on 2008-11-04
$ lspci

Salut.

---

### Post by LitusMayol on 2008-11-04
D'acord:

ara sé que tinc un NVIDIA GeForce 6100 nForce 405.


He anat al web d'nvidia he descarregat els drivers pertinents (una arxiu anomenat *NVIDIA-Linux-x86-177.80-pkg1.run*)

Aleshores per consola jo faig:
```
litus@mayolets-desktop:~$ cd /home/litus/Escriptori/
litus@mayolets-desktop:~/Escriptori$ sudo sh NVIDIA-Linux-x86-177.80-pkg1.run 

```
Comença a instal·lar i aleshores em diu:
```
  ERROR: You appear to be running an X server; please exit X before            
         installing. 
```

Com ho faig per fer-ho sense engegar les X. Si surto de sessió i li dic a l'ordinador d'engegar sessió desde Terminal en mode segur (més o menys ho diu així) em dóna el mateix problema.

Algú sap com fer-ho?

Merci de nou.

---

### Post by indiosincracia on 2008-11-04
Ctrl + Alt + F1 (per sortir de les X)
Salut.

---

### Post by LitusMayol on 2008-11-04
Mmmm...

Ho he fet, he entrat a la meva sessió. M'he mogut a /home/litus/Escriptori i he fet el *sudo sh NVIDIA-blablablabla*. Em dóna el mateix problema, exactament idèntic.

Algú se li acut com solucionar-ho?

---

### Post by torracastanyes on 2008-11-04
Ho has provat amb l'ENVY ?
Es l'únic que m'ha mes o menys funcionat.
Al menys tinc 1024x768 (el meu monitor és de 1280x1024).
La meva tarja és la la GForce 6600 i l'unic driver que em funciona es el 177.

---

### Post by LitusMayol on 2008-11-04
A veure...
amb Alt+Ctrl+F1 he escrit al terminal
```
sudo /etc/init.d/gdm stop
```
aleshores m'ha deixat proseguir amb la instal·lació del driver. Però m'ha donat un altre error. M'ha dit que el trobaria a /var/log (i gràcies a Déu, perquè sinó no el recordaria). És aquest
>    The compiler used to compile the kernel (gcc 4.2) does not exactly match the
   current compiler (gcc 4.3).  The Linux 2.6 kernel module loader rejects kern
   el modules built with a version of gcc that does not exactly match that of t
   he compiler used to build the running kernel.
   
   If you know what you are doing and want to ignore the gcc version check, sel
   ect "No" to continue installation.  Otherwise, select "Yes" to abort install
   ation, set the CC environment variable to the name of the compiler used to c
   ompile your kernel, and restart installation.  Abort now? (Answer: No)
ERROR: Unable to find the kernel source tree for the currently running kernel. 
       Please make sure you have installed the kernel source files for your
       kernel and that they are properly configured; on Red Hat Linux systems,
       for example, be sure you have the 'kernel-source' or 'kernel-devel' RPM
       installed.  If you know the correct kernel source files are installed,
       you may specify the kernel source path with the '--kernel-source-path'
       command line option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

Alguna idea?

---

### Post by PatrickVogeli on 2008-11-04
prova a instal·lar els paquets dkms, nvidia-177-modaliases i nvidia-177-kernel-source i desinstal·lar els glx. Reinicia i a veure que pasa

salut

---

### Post by LitusMayol on 2008-11-04
> **PatrickVogeli said:**
> prova a instal·lar els paquets dkms, nvidia-177-modaliases i nvidia-177-kernel-source i desinstal·lar els glx. Reinicia i a veure que pasa



Això mateix acabo de fer... i res de res. No hi ha manera segueix igual q abans! :(

---

### Post by LitusMayol on 2008-11-05
He provat una cosa diferent. Però em dóna un error semblant sobre els *headers* del kernel (o una cosa semblant).
```
litus@mayolets-desktop:~$ envyng -t
[sudo] password for litus: 


 +-------------------------------------------------+
 |                                                 |
 |             Welcome to EnvyNG                   |
 |    Developed by Alberto Milone (aka tseliot)    |
 |                                                 |
 +-------------------------------------------------+


 +-----------------------------------------------------------+
 |    EnvyNG Menu                                            |
 |                                                           |
 |    1 - Install the NVIDIA driver                          |
 |                                                           |
 |    2 - Uninstall the NVIDIA driver                        |
 |                                                           |
 |    3 - Install the ATI driver                             |
 |                                                           |
 |    4 - Uninstall the ATI driver                           |
 |                                                           |
 |    5 - Restart the Xserver                                |
 |                                                           |
 |    6 - Restart your computer                              |
 |                                                           |
 |    7 - Exit                                               |
 |                                                           |
 |    NOTE: IF THE SCREEN TURNS BLACK, PLEASE TYPE ALT+F1    |
 +-----------------------------------------------------------+
Please select one of the activities displayed above and press ENTER:

1
 +------------------------------------------------------------------------------+
 | Number | Candidate Version    | Installed Version | Compatible | Recommended |
 |------------------------------------------------------------------------------|
 | 0      | 177.80-0ubuntu2      | 177.80-0ubuntu2   | +          | -           |
 |------------------------------------------------------------------------------|
 | 1      | 173.14.12-1-0ubuntu4 | -                 | +          | +           |
 |------------------------------------------------------------------------------|
 | 2      | 96.43.05-0ubuntu10   | -                 | +          | -           |
 |------------------------------------------------------------------------------|
 | 3      | 71.86.04-0ubuntu10   | -                 | -          | -           |
 +------------------------------------------------------------------------------+
Please select the number corresponding to the desired driver and press ENTER 
(or type another number and press Enter to go back to the previous menu): 
1
False


 +--------------------------------------------------------+
 |    Error:                                              |
 |                                                        |
 |    EnvyNG has detected that the headers for            |
 |    your kernel are missing and cannot be installed     |
 |                                                        |
 +--------------------------------------------------------+

litus@mayolets-desktop:~$ 

```


 Algú sap que són els *headers* aquests i com puc solucionar-lo?

---

### Post by papapep on 2008-11-05
```
sudo aptitude install linux-headers-`uname -a | cut -f 3 -d' '`
```

Copia-ho i enganxa-ho, no intentis picar-la a mà.

---

### Post by Pablitus on 2008-11-05
> **LitusMayol said:**
> A veure...
amb Alt+Ctrl+F1 he escrit al terminal
```
sudo /etc/init.d/gdm stop
```
aleshores m'ha deixat proseguir amb la instal·lació del driver. Però m'ha donat un altre error. M'ha dit que el trobaria a /var/log (i gràcies a Déu, perquè sinó no el recordaria). És aquest


Alguna idea?

Pots provar de fer ```
export CC=gcc-4.2
```abans d'instal·lar el driver.
Crec que en el log et diu algo així com que no coïncideixen les versions del compilador, però si algú més s'ho mira i confirma o corregeix millor.

Salut!

---

### Post by LitusMayol on 2008-11-05
Bones!

Ni el que en **papapep**, ni el que en **Pablitus** proposen ha funcionat. 

Em segueix dient exactament el mateix. Tan si provo d'instal·lar-lo manualment com si provo via *envyng -t*...

No sé què fer.

---

### Post by papapep on 2008-11-05
No barregem les coses. La meva ordre era per instal·lar les fonts del nucli que tens funcionant. Les de'n pablitus, per forçar la versió del compilador.

T'ha instal·lat o no les fonts del nucli amb la ordre? Sense això, encara que el tema del compilador estigui solventat no et podrà compilar res.
I mostra el missatge d'error, encara que sigui el mateix d'abans, si us plau. Se't poden escapar detalls.

---

### Post by LitusMayol on 2008-11-05
Vaig!

A veure, fent:
```
sudo aptitude install linux-headers-`uname -a | cut -f 3 -d' '`
```

Sembla instal·lar sense problemes. Aleshores em torna a mostrar això:
```
The compiler used to compile the kernel (gcc 4.2) does not exactly match the
current compiler (gcc 4.3). The Linux 2.6 kernel module loader rejects kern
el modules built with a version of gcc that does not exactly match that of t
he compiler used to build the running kernel.

If you know what you are doing and want to ignore the gcc version check, sel
ect "No" to continue installation. Otherwise, select "Yes" to abort install
ation, set the CC environment variable to the name of the compiler used to c
ompile your kernel, and restart installation. Abort now? (Answer: No)
ERROR: Unable to find the kernel source tree for the currently running kernel.
Please make sure you have installed the kernel source files for your
kernel and that they are properly configured; on Red Hat Linux systems,
for example, be sure you have the 'kernel-source' or 'kernel-devel' RPM
installed. If you know the correct kernel source files are installed,
you may specify the kernel source path with the '--kernel-source-path'
command line option.
ERROR: Installation has failed. Please see the file
'/var/log/nvidia-installer.log' for details. You may find suggestions
on fixing installation problems in the README available on the Linux
driver download page at www.nvidia.com. 
```

També he fet el que deia en **Pablitus**. I res. El mateix missatge.

---

### Post by papapep on 2008-11-05
Crec que et serà tan simple com desinstal·lar el gcc-4.3 i instal·lar el gcc-4.2.

---

### Post by LitusMayol on 2008-11-05
I com ho faig...?

```
sudo apt-get remove gcc-4.3 && sudo apt-get install gcc-4.2
```
Així?

---

### Post by papapep on 2008-11-05
Clar :-)

---

### Post by LitusMayol on 2008-11-05
Doncs sembla que tampoc...


Això sí ha canviat l'error:
```
ERROR: Unable to find the development tool `cc` in your path; please make sure
       that you have the package 'gcc' installed.  If gcc is installed on your
       system, then please check that `cc` is in your PATH.

ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```

---

### Post by papapep on 2008-11-05
A veure...sentit comú.

Verifica que tinguis el gcc-4.2 instal·lat...o quin tens instal·lat...(a veure si en vers d'escoltar tanta música fem un xuletari d'ordres, home!!!:-P)

```
sudo aptitude search gcc|grep ^i
```

---

### Post by LitusMayol on 2008-11-05
Oh!

Com ho saps que escolto molta música... hehehehe

```
litus@mayolets-desktop:~$ sudo aptitude search gcc|grep ^i
[sudo] password for litus: 
i   gcc-4.2                         - The GNU C compiler                        
i   gcc-4.2-base                    - The GNU Compiler Collection (base package)
i A gcc-4.3-base                    - The GNU Compiler Collection (base package)
i   libgcc1                         - GCC support library                       
litus@mayolets-desktop:~$ 


```

---

### Post by papapep on 2008-11-05
Tens instal·lat un paquet de la 4.3 que igual et dóna problemes. Jo l'esborraria.
Després de fer-ho, torna a provar a veure si ara comença a compilar. Si et dóna el mateix error del PATH, doncs ja saps: comprova que la tinguis ben definida i que coincideixi amb el path real de l'executable del compilador.

> Com ho saps que escolto molta música... hehehehe


Jovenalla....:twisted:

---

### Post by LitusMayol on 2008-11-05
I un altre problema... el paquet té depèndencies (es veu que mig ordinador em depèn d'aquest paquet: abiword, xine, amarok... xD). I si provo de desinstal·lar-lo per consola:
```
litus@mayolets-desktop:~$ sudo apt-get remove gcc-4.3-base
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació d'estat... Fet
No s'han pogut instal·lar alguns paquets. Això pot ser degut a que vàreu
requerir una situació imposible o a que esteu emprant la distribució
unstable i alguns paquets requerits encara no han estat creats o bé
encara no els hi han afegit.

Degut a que només heu requerit una única operació, serà molt
probable que el paquet no sigui instal·lable i que s'hagi d'emetre
un informe d'error en contra d'aquest per a arxivar-lo.
La següent informació pot ajudar-vos a resoldre la situació:

Els següents paquets tenen dependències sense satisfer:
  libgcc1: Depén: gcc-4.3-base (= 4.3.2-1ubuntu11) però no serà instal·lat
E: Paquets trencats
litus@mayolets-desktop:~$ 

```


Aleshores potser seria millor
> **papapep said:**
>  comprova que la tinguis ben definida i que coincideixi amb el path real de l'executable del compilador.


La pena és que, **papapep**, és com si em parléssin en xinès. No sé què he de fer.

---

### Post by papapep on 2008-11-05
Per veure com està definida una variable:

```
echo $NOM_DE_LA_VARIABLE
```

En el cas de PATH, com que el que fa es dir-li al sistema on trobar executables, cal trobar on és l'executable que et porta de cap (gcc) i verificar que el resultat de la ordre de dalt conté el directori on és.

Les variables d'entorn es poden definir a nivell global de sistema i/o a nivell d'usuari, o sigui que pot haver-hi tantes variables PATH diferents com usuaris tingui un sistema operatiu. Amb això, el que vull dir, és que el contingut de PATH per a root, pot perfectament no coincidir amb el contingut de la variable PATH del teu usuari, amb el qual cal considerar abans de verificar aquestes coses quin usuari et genera l'error (en el teu cas crec que root) per a fer l'echo i demés en consonància, i no portar-te tu mateix a l'hort :-)

Ara m'he explicat?

---

### Post by papapep on 2008-11-05
Per cert, a veure què et torna això:

```
ls -la /usr/bin/gcc
```

---

### Post by LitusMayol on 2008-11-05
És això útil?

El *echo* fa com si res... no sé si és bo o dolent.

```
root@mayolets-desktop:~# echo $gcc

root@mayolets-desktop:~# ls -la /usr/bin/gcc
ls: no s’ha pogut accedir a /usr/bin/gcc: No such file or directory
root@mayolets-desktop:~# 

```

---

### Post by papapep on 2008-11-05
La variable que has de mirar com està definida és PATH. gcc és el compilador, no una variable.

Prova a veure què diu això:

```
ls -la /usr/bin/gcc*
```

> És això útil?

Millor no contesto...

---

### Post by LitusMayol on 2008-11-05
Aquí va! ;)

```
litus@mayolets-desktop:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
litus@mayolets-desktop:~$ ls -la /usr/bin/gcc*
-rwxr-xr-x 1 root root 193148 2008-10-26 17:24 /usr/bin/gcc-4.2
-rwxr-xr-x 1 root root   2018 2008-08-05 02:44 /usr/bin/gccmakedep
litus@mayolets-desktop:~
```




> **papapep said:**
> Millor no contesto...
Hehe, em referia a que jo servia una informació i no sabia si era útil: venia a ser un *Ho he fet bé **papa**[COLOR="Silver"]pep[/COLOR]?*



Merciii!

---

### Post by papapep on 2008-11-05
Doncs del que m'has passat, resulta:

> litus@mayolets-desktop:~$ ls -la /usr/bin/gcc*
-rwxr-xr-x 1 root root 193148 2008-10-26 17:24 /usr/bin/gcc-4.2
-rwxr-xr-x 1 root root   2018 2008-08-05 02:44 /usr/bin/gccmakedep


Falta l'enllaç simbòlic gcc i, per tant, cal crear-lo (ja que t'agrada fer servir els ampersands...:-D):

```
 cd /usr/bin && sudo ln -s gcc-4.2 gcc

```

Com que PATH ja té definit (_amb l'usuari que has executat l'echo_) /usr/bin, 

> litus@mayolets-desktop:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:**[COLOR="Red"]/usr/bin[/COLOR]**:/sbin:/bin:/usr/games



t'hauria de funcionar la compilació, o no :-D ...

---

### Post by LitusMayol on 2008-11-05
Sembla que tampoc...

Guita l'error:
```
ERROR: Unable to find the development tool `cc` in your path; please make sure
       that you have the package 'gcc' installed.  If gcc is installed on your
       system, then please check that `cc` is in your PATH.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```

---

### Post by PatrickVogeli on 2008-11-05
prova amb sudo update-alternatives --config gcc i alla selecciona el gcc-4.2 i despres torna a provar a instal·lar el driver.

salut

---

### Post by LitusMayol on 2008-11-05
M'estic començant a preocupar...

```
litus@mayolets-desktop:~$ sudo -s
[sudo] password for litus: 
root@mayolets-desktop:~# sudo update-alternatives --config gcc
No hi ha alternatives per a gcc.
root@mayolets-desktop:~# 
```

Em fa por... m'hauré de quedar am la pantalla de 19" a 800x600! :S Es veu tot massa gran i amés és incòmode. Renoi...

Merci de totes maneres patrick. Que més puc provar?

---

### Post by PatrickVogeli on 2008-11-05
a veure: ls -la /usr/bin/cc i ls -la /etc/alternatives/cc

EDITO: i prova tambe sudo update-alternatives --config cc

---

### Post by LitusMayol on 2008-11-05
Ups...

```
root@mayolets-desktop:~# ls -la /usr/bin/cc i ls -la /etc/alternatives/cc
ls: no s’ha pogut accedir a /usr/bin/cc: No such file or directory
ls: no s’ha pogut accedir a i: No such file or directory
ls: no s’ha pogut accedir a ls: No such file or directory
ls: no s’ha pogut accedir a /etc/alternatives/cc: No such file or directory
root@mayolets-desktop:~# sudo update-alternatives --config cc
No hi ha alternatives per a cc.

```

---

### Post by PatrickVogeli on 2008-11-05
sudo ln -s /usr/bin/gcc-4.2 /usr/bin/cc i torna a provar a instalar el driver

---

### Post by papapep on 2008-11-05
> ls -la /usr/bin/cc [COLOR="Red"]**i**[/COLOR] ls -la /etc/alternatives/cc



Com ha mínim no has posat el "a veure" :-D

---

### Post by PatrickVogeli on 2008-11-05
jajajaja que gran. Se m'havia passat completament :D

---

### Post by LitusMayol on 2008-11-05
Res... Seguim amb errors...

```
ERROR: Unable to find the kernel source tree for the currently running kernel. 
       Please make sure you have installed the kernel source files for your
       kernel and that they are properly configured; on Red Hat Linux systems,
       for example, be sure you have the 'kernel-source' or 'kernel-devel' RPM
       installed.  If you know the correct kernel source files are installed,
       you may specify the kernel source path with the '--kernel-source-path'
       command line option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```

Renoi... em sap greu. Us tinc com esclaus, aquí treballant *dale que te pego*... :S

---

### Post by PatrickVogeli on 2008-11-05
em sembla que farem tornar a windows :D

sudo apt-get install build-essential kernel-package linux-headers-generic

---

### Post by LitusMayol on 2008-11-06
Després de fer:
```
sudo apt-get install build-essential kernel-package linux-headers-generic

```

Ha tornat a fallar, aquest cop ha canviat l'error. Torna a ser aquell que es queixa de la versió actual (4.3) no concorda amb la necessària (*mà o menóh*):
```
The CC version check failed:
   
   The compiler used to compile the kernel (gcc 4.2) does not exactly match the
   current compiler (gcc 4.3).  The Linux 2.6 kernel module loader rejects kern
   el modules built with a version of gcc that does not exactly match that of t
   he compiler used to build the running kernel.
   
   If you know what you are doing and want to ignore the gcc version check, sel
   ect "No" to continue installation.  Otherwise, select "Yes" to abort install
   ation, set the CC environment variable to the name of the compiler used to c
   ompile your kernel, and restart installation.  Abort now? (Answer: Yes)
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```


Merci nanos.

---

### Post by PatrickVogeli on 2008-11-06
sudo rm -rf /usr/bin/cc && sudo ln -s /usr/bin/gcc-4.3 /usr/bin/cc

i torne'm-hi

---

### Post by LitusMayol on 2008-11-06
Doncs tampoc.. i a més el mateix error.

```
 The compiler used to compile the kernel (gcc 4.2) does not exactly match the
   current compiler (gcc 4.3).  The Linux 2.6 kernel module loader rejects kern
   el modules built with a version of gcc that does not exactly match that of t
   he compiler used to build the running kernel.
   
   If you know what you are doing and want to ignore the gcc version check, sel
   ect "No" to continue installation.  Otherwise, select "Yes" to abort install
   ation, set the CC environment variable to the name of the compiler used to c
   ompile your kernel, and restart installation.  Abort now? (Answer: Yes)
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```

---

### Post by PatrickVogeli on 2008-11-06
sudo rm -rf /usr/bin/cc
sudo rm -rf /usr/bin/gcc
sudo ln -s /usr/bin/gcc-4.2 /usr/bin/gcc
sudo ln -s /usr/bin/gcc-4.2 /usr/bin/cc

---

### Post by LitusMayol on 2008-11-06
Tampoc... Canvia d'error. Però no és un nou:
```
ERROR: Unable to find the kernel source tree for the currently running kernel. 
       Please make sure you have installed the kernel source files for your
       kernel and that they are properly configured; on Red Hat Linux systems,
       for example, be sure you have the 'kernel-source' or 'kernel-devel' RPM
       installed.  If you know the correct kernel source files are installed,
       you may specify the kernel source path with the '--kernel-source-path'
       command line option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```

Em sembla que hauré de formatejar i amb una Live cascar-li de nou.. però emf a por que tingui el mateix problema! :S

---

### Post by papapep on 2008-11-06
Enganxa el que et mostrin aquestes dues ordres:

```
uname -a
```

i

```
sudo aptitude search linux-headers build-essential pkg-config gcc|grep ^i
```

---

### Post by LitusMayol on 2008-11-07
Aquí està

```
root@mayolets-desktop:~# uname -a
Linux mayolets-desktop 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux
root@mayolets-desktop:~# sudo aptitude search linux-headers build-essential pkg-config gcc|grep ^i
i   build-essential                 - Informational list of build-essential pack
i A gcc                             - The GNU C compiler                        
i   gcc-4.2                         - The GNU C compiler                        
i   gcc-4.2-base                    - The GNU Compiler Collection (base package)
i A gcc-4.3                         - The GNU C compiler                        
i A gcc-4.3-base                    - The GNU Compiler Collection (base package)
i   libgcc1                         - GCC support library                       
i A linux-headers-2.6.27-7          - Header files related to Linux kernel versi
i A linux-headers-2.6.27-7-generic  - Linux kernel headers for version 2.6.27 on
i   linux-headers-generic           - Generic Linux kernel headers              
i   pkg-config                      - manage compile and link flags for librarie
root@mayolets-desktop:~# 
```


(de debò: MERCI!!!!)

---

### Post by oriolsbd on 2008-11-07
Veig (pel que diu el teu uname -a) que entres amb el kernel 2.6.24-19 (que és de Hardy). En el menú del grub no hi tens l'opció per entrar amb el kernel 2.6.27-7?

No et puc ajudar massa bé (segur que en Papapep et podrà ajudar més), però potser aquesta petita "pista" et serveix.

Salut!

---

### Post by papapep on 2008-11-07
A algun lloc ens hem perdut, o ens hem trobat dins un poltergeist, per que si [aquí]("http://ubuntuforums.org/showpost.php?p=6109402&postcount=11") deies això:

> A veure, fent:
Code:

sudo aptitude install linux-headers-`uname -a | cut -f 3 -d' '`



El que ara has mostrat de un kernel funcionant, amb unes fonts del kernel diferents, doncs no quadra per enlloc amb la teva frase:

> Sembla instal·lar sense problemes. Aleshores em torna a mostrar això:

Em fa l'efecte de que no acabava de ser "exacte".

A veure quins kernels tens instal·lats...

```
Sembla instal·lar sense problemes. Aleshores em torna a mostrar això:
```

i també el contingut de **/boot/grub/menu.lst**

---

### Post by LitusMayol on 2008-11-07
Mmmm...

Potser el problema és que tinc dos Grubs i que el grub principal NO és el de la *Intrèpid*.
Tinc l'**UbuntuStudio**, que veient com ha anat el canvi de versió amb l'altre l'he fet romandre a la *Hardy*. 

Us adjunto els dos *menus.lst* però sota els noms de *menuSTUDIO.txt* (el grub que fa servir l'ordinador)i *menuINTREPID.txt*.

---

### Post by papapep on 2008-11-07
...a veure...i amb quin dels dos es suposa que hem estat fent proves aquestes 5 pàgines de posts i intentant compilar, instal·lant paquets i modificant enllaços simbòlics?

i et falta dir quins nuclis tens instal·lats.

---

### Post by LitusMayol on 2008-11-07
Perdó. ](*,) 

La veritat és que no ho sé... Tot i que no acabo de veure la relació entre el Grub i el *driver* de la Nvidia (per això fins ara no li havia donat importància al fet de tenir-ne dos...). 

Doncs hem estat treballant sobre el de la *Intrepid*. :lolflag: 

> **papapep said:**
> i et falta dir quins nuclis tens instal·lats.
Eing? No sé com fer-ho, ni que he de mirar...



Ho sé. És per matar-me.:-s

---

### Post by papapep on 2008-11-07
```
sudo aptitude search linux-image|grep ^i
```

Però a l'intrepid, no t'equivoquis.

---

### Post by LitusMayol on 2008-11-07
Fins ara tot ho he fet a la *Intrepid*.


Resultat de fer *sudo aptitude search linux-image|grep ^i*:
```
litus@mayolets-desktop:~$ sudo aptitude search linux-image|grep ^i
[sudo] password for litus: 
i   linux-image-2.6.24-19-generic   - Linux kernel image for version 2.6.24 on x
i   linux-image-2.6.27-7-generic    - Linux kernel image for version 2.6.27 on x
i   linux-image-generic             - Generic Linux kernel image                
litus@mayolets-desktop:~$ 


```

---

### Post by papapep on 2008-11-07
Recapituleixons:

- Tens instal·lat el nou nucli 2.6.27-7.
- Al menu.lst és la teva primera opció.
- Tens les fonts d'aquest mateix nucli instal·lades.

aleshores...

com és possible que estiguis fent córrer el 2.6.24-19????

> root@mayolets-desktop:~# uname -a
Linux mayolets-desktop **2.6.24-19**-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux


això és o que ho has fet a l'Ubuntustudio, el més probable, o que el tries a l'arrencada...

M'ho aclareixes?

---

### Post by LitusMayol on 2008-11-08
> **papapep said:**
> Recapituleixons:

- Tens instal·lat el nou nucli 2.6.27-7.
- Al menu.lst és la teva primera opció.
- Tens les fonts d'aquest mateix nucli instal·lades.

aleshores...

com és possible que estiguis fent córrer el 2.6.24-19????



això és o que ho has fet a l'Ubuntustudio, el més probable, o que el tries a l'arrencada...

M'ho aclareixes?


No, no. Ho he fet a l'*Intrèpid*. Suposo que arrenco amb el 2.6.24-19 perquè al menú de grub que faig servir (el de **UbuntuStudio**) no hi és la opció. 

He provat de fer un "còpia i enganxa" del *menu.lst* de la *Intrèpid* a l'**UbuntuStudio**, però aleshores em donava l'Erro: 15 de Grub (File Not Found).

Merci

---

### Post by Diegstroyer on 2008-11-08
Proba el que diu aquesta pàgina: [http://gambasconchocolate.blogspot.com/2008/11/instalar-los-drivers-propietarios-de.html]("http://gambasconchocolate.blogspot.com/2008/11/instalar-los-drivers-propietarios-de.html")

A veure que tal... ja comentaràs si et funciona.

Això contant que tinguis el kernel 2.6.27.7.

---

### Post by PatrickVogeli on 2008-11-08
No provis a instal·lar cap driver fins que no aconsegueixis arrancar amb el kernel 2.6.27.7, no servira de res.

Enganxan's el teu /boot/grub/menu.lst de l'ubuntustudio

---

### Post by oriolsbd on 2008-11-08
El grub és un programa que s'instal·la en el MBR del disc, o sigui que només n'hi pot haver un d'actiu per a cada disc. En el teu cas, sembla clar que tens actiu el grub de UbuntuStudio, de manera que cap actualització del kernel que facis a l'altre Ubuntu no es veurà reflectida en el grub (perquè actualitza el menu.lst del seu grub, que no és actiu).

El que hauries de fer és, sobretot, fer-te una còpia de seguretat del menu.lst de UbuntuStudio, editar-lo i modificar les entrades de l'Ubuntu Intrepid (o afegir-ne unes de noves iguals a elles) modificant el kernel 2.6.24-19 per 2.6.27-7.

Apart d'això, has de tenir en compte que si a Intrepid hi ha una actualització del Kernel, per veure-la efectiva hauràs de modificar el grub de UbuntuStudio.

Salut!

---

### Post by Diegstroyer on 2008-11-08
Pot posar també quins kernels tens instal·lats (a vegades no coincideixen amb els del GRUB), utilitza la següent ordre en terminal:

**sudo dpkg -l | grep linux-image**

Copia els resultats en un post.

---

### Post by LitusMayol on 2008-11-08
> **Diegstroyer said:**
> Proba el que diu aquesta pàgina: [http://gambasconchocolate.blogspot.com/2008/11/instalar-los-drivers-propietarios-de.html]("http://gambasconchocolate.blogspot.com/2008/11/instalar-los-drivers-propietarios-de.html")

A veure que tal... ja comentaràs si et funciona.

Això contant que tinguis el kernel 2.6.27.7.
Ostres! És fantàstica! Així que arreglem el tema del nucli ho probaré: fa molt bona pinta! Merci.



> **PatrickVogeli said:**
> No provis a instal·lar cap driver fins que no aconsegueixis arrancar amb el kernel 2.6.27.7, no servira de res.

Enganxan's el teu /boot/grub/menu.lst de l'ubuntustudio

D'acord. Aquí va el *menu.lst*!

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		1

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		15

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=98300a0c-c554-4d92-9d5f-a25f4e04ca50 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##
## MISATGE D'ENTRADA
title		Escolliu el Sistema Operatiu Lliure desitjat:
root

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.04.1
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=950d8be1-e06a-4bef-9f1a-4f532c68993b #ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot

title		UbuntuStudio 8.04.1
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=98300a0c-c554-4d92-9d5f-a25f4e04ca50 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-rt
quiet


###ALTRES UBUNTUSTUDIO
#title		UbuntuStudio 8.04.1 (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=98300a0c-c554-4d92-9d5f-a25f4e04ca50 ro single
#initrd		/boot/initrd.img-2.6.24-19-rt

#title		UbuntuStudio 8.04.1, kernel 2.6.24-16-rt
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-16-rt root=UUID=98300a0c-c554-4d92-9d5f-a25f4e04ca50 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-16-rt
#quiet

#title		UbuntuStudio 8.04.1, kernel 2.6.24-16-rt (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-16-rt root=UUID=98300a0c-c554-4d92-9d5f-a25f4e04ca50 ro single
#initrd		/boot/initrd.img-2.6.24-16-rt

#title		UbuntuStudio 8.04.1, memtest86+
#root		(hd0,2)
#kernel		/boot/memtest86+.bin
#quiet


###ALTRES UBUNTU



# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
#title		Ubuntu 8.04.1
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=950d8be1-e06a-4bef-9f1a-4f532c68993b #ro quiet splash 
#initrd		/boot/initrd.img-2.6.24-19-generic
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
#title		Ubuntu 8.04.1 (recovery mode)
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=950d8be1-e06a-4bef-9f1a-4f532c68993b ro single 
#initrd		/boot/initrd.img-2.6.24-19-generic
#savedefault
#boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
#title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (on /dev/sda2)
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=950d8be1-e06a-4bef-9f1a-4f532c68993b ro quiet splash 
#initrd		/boot/initrd.img-2.6.24-16-generic
#savedefault
#boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
#title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode) (on /dev/sda2)
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=950d8be1-e06a-4bef-9f1a-4f532c68993b ro single 
#initrd		/boot/initrd.img-2.6.24-16-generic
#savedefault
#boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
#title		Ubuntu 8.04.1, memtest86+ 
#root		(hd0,1)
#kernel		/boot/memtest86+.bin  
#savedefault
#boot
```

---

### Post by Diegstroyer on 2008-11-08
Proba fent:

**sudo update-grub**

No se si t'has fixat, però no t'apareix el kernel del 8.10 a la llista de kernels.

Mira també quins kernels tens:

**sudo dpkg -l | grep linux-image**

Posa'ls a veure quins tens instal·lats.

---

### Post by PatrickVogeli on 2008-11-08
Veient el teu menu.lst hi has d'afegir el següent:

```

title		Ubuntu 8.10, kernel 2.6.27-7
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=950d8be1-e06a-4bef-9f1a-4f532c68993b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot

```

ho pots colocar just a sobre de les linies corresponents al Ubuntu 8.04.1. Reinicia i comprova si va. Si arranca comprova amb uname -r el kernel que estas fent servir. Si es el 27-7, torna a provar a instal·lar el driver.

ja diras quelcom

---

### Post by LitusMayol on 2008-11-08
**Patrick**, you rule maan!


No ha fet falta ni instal·lar el driver!!! Tan sols afegir les línies que m'has donat, al Grub: s'ha engegat! I bé! 

Perfecteeeeee!


Merci a tots! 
[SOLVED!]

---

