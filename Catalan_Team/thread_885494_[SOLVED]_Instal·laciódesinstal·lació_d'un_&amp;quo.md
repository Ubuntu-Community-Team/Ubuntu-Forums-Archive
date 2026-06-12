---
title: "[SOLVED] Instal·lació/desinstal·lació d'un &amp;quot;tar.gz&amp;quot;"
date: 2008-08-10
forum: Catalan Team
---

### Post by LitusMayol on 2008-08-10
Bones familia ubuntaire!

Us explico, he instal·lat l'[StorYBoard]("http://storybook.intertec.ch/?g_page=home&g_lang=en"), un genial programa per ajudar-te a ordenar quan escrius. (L'he conegut a través d'[aquesta]("http://http://www.somgnu.cat/storybook-tajuda-a-escriure-novel%C2%B7les/") estimada plana web)


Doncs bé la instal·lació ha sigut totalment correcta i el programa em funciona.

He fet:
```

$ cd ~/Escriptori
~/Escriptori$ tar -xzf storybook_2.1.2_linux.tar.gz 
./install.sh

```
I per engegar-lo:
```
./storybook.sh
```


Fins aquí tot bé. Però resulta que el "*tar -xzf*" l'he fet a l'escriptori i el paquet s'ha descomprimit a l'escriptori (lògic...). Però en lloc de ser una carpeta comprimida (amb tots els arxius dins d'aquesta), simplement són els arxius comprimits en grup...! Per tan el meu Escriptori ara és això:
```
litus@mayolets-desktop:~/Escriptori$ ls            
Amanijag.jpg  install.sh    MÃºsica CD Dern               Thyrien-Maqueta
De tot        INSTALL.txt   README.txt                    Ventafocs.mp3
dict          Led Zeppelin  reports
icon.ico      lib           storybook_2.1.2_linux.tar.gz
icon.png      LICENSE.txt   storybook.sh
litus@mayolets-desktop:~/Escriptori$ 
 
```

Tots aquest són els que pertanyien a "*storybook_2.1.2_linux.tar.gz*":
```
  
install.sh
INSTALL.txt
README.txt                  
dict           
reports
icon.ico      
lib           
storybook_2.1.2_linux.tar.gz
icon.png      
LICENSE.txt   
storybook.sh
```


Els meus dubtes són:
[LIST=1]
[*]Si ho he elimino (botó dret i cap a la paperera), el programa no seguirà funcionant correctament, oi?
[*]Com puc fer-ho per instal·lar-lo més ordenadament (si, ho sé: ho puc posar en una carpeta que es digui "**StorYBoard**", però aquesta carpeta on la deixo? Al mig de l'escriptori no...)
[*]I ja posats... No sé desintal·lar "*tar.gz*", com es fa? Ho sé... És molt "*down*", però no en sé.
[/LIST]



Merci!

---

### Post by papapep on 2008-08-10
> Els meus dubtes són:

   1. Si ho he elimino (botó dret i cap a la paperera), el programa no seguirà funcionant correctament, oi?
   2. Com puc fer-ho per instal·lar-lo més ordenadament (si, ho sé: ho puc posar en una carpeta que es digui "StorYBoard", però aquesta carpeta on la deixo? Al mig de l'escriptori no...)
   3. I ja posats... No sé desintal·lar "tar.gz", com es fa? Ho sé... És molt "down", però no en sé.


1.- Prova-ho i ho sabràs :-)(evidentment fes-ne còpia abans).

2.- On vulguis dins el teu espai d'usuari. P. ex., dins /home/Litus (suposant que el teu usuari es digui Litus).

3.- No hi ha un sistema estàndard d'instal·lació d'un arxiu tar.gz. És un arxiu de fitxers que després s'ha comprimit, i l'script d'instal·lació pot fer qualsevol cosa. Així mateix, no hi ha un procediment de desinstal·lació, tot i que algunes vegades l'arxiu porta un fitxer de desinstal·lació (uninstall.sh, remove.sh, etc).
Hi ha vegades que l'instal·lador fa molta feina i instal·la els binaris als directoris "normals" pels executables d'usuari (/usr/bin, /usr/sbin). D'altres cop els executa des del lloc on s'han descomprimit, sense més.
O sigui, i en conclusió, que no hi ha un sistema únic, sinó un fotimer. Cal saber què fa l'instal·lador (mirar el codi d'install.sh) i normalment per aquí es veurà com fer "marxa enrera".
Algun cop el fitxer INSTALL.txt que sol acompanyar aquests arxius, explica què cal fer tant per instal·lar-lo com per a eliminar-lo.

---

### Post by LitusMayol on 2008-08-10
Bones **papapep**!

Ara feia dies que no tenia un dubte i començava a perdre el meu rang de "*preguntón* oficial"!

Mira a l'INSTALL.txt només hi ha això:
```

see

storybook.intertec.ch
```
És a dir que, m'envia al web. Però a la plana només hi ha informació de la instal·lació, re de desinstal·lar. :S 

Pel que fa al tema de treure-ho de l'Escriptori. Es com desinstal·lar-l'ho. És a dir si elimino els arxius (no el tar.gz!! que sinó no puc tornar-lo a instal·lar) la consola em deixa ana rel típic:

```
litus@mayolets-desktop:~$ ./storybook.sh
bash: ./storybook.sh: No such file or directory

```


Merci de totes maneres **papapep**! :)

---

