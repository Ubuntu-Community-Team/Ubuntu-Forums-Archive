---
title: "[SOLVED] Instalació de navegador Flock"
date: 2008-03-12
forum: Catalan Team
---

### Post by lluisalguero on 2008-03-12
Hola nois,
he instalat aquest nou navegador per veure si no tinc tants problemes com amb el Firefox.
He seguit les instruccions d'aquest blog [http://bricogeek.blogspot.com/2007/11/como-instalar-flock-en-ubuntu.html](http://bricogeek.blogspot.com/2007/11/como-instalar-flock-en-ubuntu.html)
Se m'ha creat l'icona al escriptori però no s'obre el programa, i ni idea de que pot ser...

moltes gràcies per l'ajuda que em pugeu donar.

Lluís

---

### Post by papapep on 2008-03-12
I cridant-lo en un terminal funciona o no?

Necessitem més informació per saber on ets ara. No sabem ni si tan sols s'ha instal·lat realment.

---

### Post by lluisalguero on 2008-03-12
No sé si et refereixes a això

```
lluis@lluis-laptop:~$ flock
flock (util-linux-ng 2.13)
Usage: flock [-sxun][-w #] fd#
       flock [-sxon][-w #] file [-c] command...
  -s  --shared     Get a shared lock
  -x  --exclusive  Get an exclusive lock
  -u  --unlock     Remove a lock
  -n  --nonblock   Fail rather than wait
  -w  --timeout    Wait for a limited amount of time
  -o  --close      Close file descriptor before running command
  -c  --command    Run a single command string through the shell
  -h  --help       Display this text
  -V  --version    Display version
lluis@lluis-laptop:~$ 


```

Com sé si s'ha instalat? Se suposa que si he seguit les instruccions si que ho tindria que estar, no? :confused:

La veritat és que com no entenc lo que he fet (només he seguit les instruccions) no sé on l'haig de buscar.

Gràcies papapep

---

### Post by patrickfromspain on 2008-03-12
aixo no es el navegador!! La comanda flock tambe la tinc jo i no el tinc insta&#320;lat.

EDITO: la guia te un fallo, ja que no es pot fer un simlink a /usr/bin/flock perque ja existeix.. prova a fer el link a /usr/local/bin/flock-browser

salut!

---

### Post by lluisalguero on 2008-03-12
Vaaaale, he estat mirant per internet i ja he entés una mica el que ha anat fent les ordres, i crec que ja sé on és l'errada.

al principi que em diu: "cd Desktop", suposant que es dona per entés que em baixa't l'arxiu a l'escriptori, cosa que jo ho tinc dins d'una carpeta a /home/lluis/arxius...crec que aquest és l'error.

Vaig a intentar començar des de'l principi però fent cd /home/lluis/arxius...i a veure que en surt

---

### Post by lluisalguero on 2008-03-12
> **lluisalguero said:**
> Vaaaale, he estat mirant per internet i ja he entés una mica el que ha anat fent les ordres, i crec que ja sé on és l'errada.

al principi que em diu: "cd Desktop", suposant que es dona per entés que em baixa't l'arxiu a l'escriptori, cosa que jo ho tinc dins d'una carpeta a /home/lluis/arxius...crec que aquest és l'error.

Vaig a intentar començar des de'l principi però fent cd /home/lluis/arxius...i a veure que en surt

Em cito a mi mateix...no ha funcionat el que he comentat...:(

---

### Post by patrickfromspain on 2008-03-12
> **patrickfromspain said:**
> aixo no es el navegador!! La comanda flock tambe la tinc jo i no el tinc insta&#320;lat.

EDITO: la guia te un fallo, ja que no es pot fer un simlink a /usr/bin/flock perque ja existeix.. prova a fer el link a /usr/local/bin/flock-browser

salut!

aixo no serveix?

---

### Post by lluisalguero on 2008-03-12
> **patrickfromspain said:**
> aixo no serveix?

Doncs no, i tampoc sé com esborrar-ho i començar des del principi...:confused:

---

### Post by patrickfromspain on 2008-03-12
be tio, temps per pensar per tu mateix. Us obsesioneu tant en seguir tutorials i copiar+pegar+enter, copiar+pegar+enter, inicio+enter.. merda no funciona, que ja no penseu on pot estar l'error.

Baixat el flock i el descomprimeixes a ma, i a veure si aixi el pots executar.

Revisa tots els pasos i, molt important intenta ENTENDRE que estas fent. Si no entens el que fas i perque, no n'apendras mai. 

No hauras intentat fer aixo:
udo tar -zxvf flock-0.9.1.2.es-ES.linux-i686.tar.gz -C /opt i el teu arxiu es una version mes nova i en un altre idioma, no?

salut!

---

### Post by lluisalguero on 2008-03-12
> **patrickfromspain said:**
> be tio, temps per pensar per tu mateix. Us obsesioneu tant en seguir tutorials i copiar+pegar+enter, copiar+pegar+enter, inicio+enter.. merda no funciona, que ja no penseu on pot estar l'error.

Baixat el flock i el descomprimeixes a ma, i a veure si aixi el pots executar.

Revisa tots els pasos i, molt important intenta ENTENDRE que estas fent. Si no entens el que fas i perque, no n'apendras mai. 

No hauras intentat fer aixo:
udo tar -zxvf flock-0.9.1.2.es-ES.linux-i686.tar.gz -C /opt i el teu arxiu es una version mes nova i en un altre idioma, no?

salut!

No estic obsesionat en seguir tutorials, però si no sé com es fa una cosa, bé que ho haig de mirar o preguntar, no?

I seguint amb el tema...he descomprit l'arxiu tar.gz i allà dins hi ha un arxiu "flock" que sembla l'executable del programa on em pregunta si el vull "mostrar" "executar" o be "executar en un terminal". He triat "executar i s'ha obert (ara estic des de'l flock precisament).

A veure, sóc curt, però no tant...he fet
sudo tar -zxvf flock-1.0.9.ca.linux-i686.tar.gz -C /opt
era de suposar que havia de ficar la versió que m'havia baixat.

I respecte de fer les coses ENTENENT el que es fa, i no fer un copy-paste com dius tu...si una cosa té la gent que fa servir qualsevol distro de Linux, és la gran quantitat de tutorials i ajudes que es troben per Internet. Linux no és fàcil, ho reconéc, però d'aquí a insinuar que els neòfits en el tema com jo, som uns "comodons" que només fem el copy-paste pertinent, crec que vas equivocat, aquesta no és la filosofia que jo he entés.

Pot ser si que em tinc que esforçar més en apendre les 4 coses bàsiques, però no tinc temps material per fer-ho i les poques que he aprés, és a base de TUTORIALS i de webs i fòrums com aquest. Per això estic agraït a gent com vosaltres que ajudeu a la gent que comença com jo.

Lluís

---

### Post by patrickfromspain on 2008-03-12
No volia insinuar que fossis un comodon o un ruc. Perdó.

si has fet sudo tar -zxvf flock-1.0.9.ca.linux-i686.tar.gz -C /opt comprova que existeix /opt/flock i que pots arrencar el flock, en terminal fent /opt/flock/flock. Si no et funiona, refes aquest últim pas. Si funciona, sudo ln -s /opt/flock/flock /usr/local/bin/navegador-flock i el podras arrancar fent alt+f2 i posant navegador-flock.

Ara nomes et queda porsar-ho als menus, adapta lúltim pas del tutorial per a que executi navegador-flock.

salut

---

### Post by lluisalguero on 2008-03-12
> **patrickfromspain said:**
> No volia insinuar que fossis un comodon o un ruc. Perdó.
No hi ha res a perdonar...no ha passat res...
> **patrickfromspain said:**
> 
si has fet sudo tar -zxvf flock-1.0.9.ca.linux-i686.tar.gz -C /opt comprova que existeix /opt/flock i que pots arrencar el flock, en terminal fent /opt/flock/flock. Si no et funiona, refes aquest últim pas. Si funciona, sudo ln -s /opt/flock/flock /usr/local/bin/navegador-flock i el podras arrancar fent alt+f2 i posant navegador-flock.

el directori /opt/flock hi és i amb el terminal el puc ficar en marxa. Ara provaré lo del sudo ln -s (he buscat i veig que es per a crear el accesos directes), encara que fent alt+f2 el puc ficar en marxa, he mirat dins al directori /usr/local/bin...però no hi ha res...ni ocult tampoc..:confused:
> **patrickfromspain said:**
> 
Ara nomes et queda porsar-ho als menus, adapta lúltim pas del tutorial per a que executi navegador-flock.

salut

L'últim pas, a que et refereixes? al *sudo gedit /usr/share/applications/flock.desktop* perquè he provat de fer *sudo gedit /usr/share/applications/navegador-flock* i pegar allò que indica al tutorial, però no fa res a l'accés directe creat a Aplicacions->Internet.

---

### Post by papapep on 2008-03-12
Si ara el pots executar amb l'alt+F2 només et cal crear una llançadora a l'escriptori (botó de la dreta, crear llançadora), ficar-hi la mateixa ordre que fiques al diàleg de l'alt+F2 i tot hauria de funcionar.

---

### Post by patrickfromspain on 2008-03-12
a /usr/local/bin no hi hauria d'haver res.. fins que facis el sudo ln -s.. (que, efectivamente, es per fer "accesos directes").

L'ultim pas, si, gksudo gedit /usr/local/share/applications/navegador-flock.desktop i alla enganxar-hi:

Desktop Entry]
Name=Flock
Name[en_US]=Flock
Name[es]=Flock
Comment=Flock Web browser
Comment[en_US]=Flock Web browser
Comment[es]=Flock el navegador social
Encoding=UTF-8
Exec=navegador-flock
Terminal=false
Type=Application
Icon=flock-icon.xpm
Categories=Application;Network;

salut!

---

### Post by lluisalguero on 2008-03-12
> **patrickfromspain said:**
> a /usr/local/bin no hi hauria d'haver res.. fins que facis el sudo ln -s.. (que, efectivamente, es per fer "accesos directes").

L'ultim pas, si, gksudo gedit /usr/local/share/applications/navegador-flock.desktop i alla enganxar-hi:

Desktop Entry]
Name=Flock
Name[en_US]=Flock
Name[es]=Flock
Comment=Flock Web browser
Comment[en_US]=Flock Web browser
Comment[es]=Flock el navegador social
Encoding=UTF-8
Exec=navegador-flock
Terminal=false
Type=Application
Icon=flock-icon.xpm
Categories=Application;Network;

salut!

Perfecte, ara si. Al meu anterior post i revisant ara el teu, he vist que he comés una errada. Havia ficat:

```
sudo gedit /usr/share/applications/navegador-flock
```

quan hagués tingut que ficar
```
sudo gedit /usr/share/applications/navegador-flock.desktop
```

i també veig que no havia ficat al navegador-flock.desktop 
Application: navegador-flock
només tenia: flock

Ara bé la segona part...tinc 2 icones a aplicacions->internet del flock, una que no funciona i l'altra que si. Com ho puc fer (o desfer) per treure l'icona que no funciona?

Em contesto per no esborrar l'anterior. Sistema->Preferències->Menú Principal, des d'allà he esborrat l'accés directe que no funcionava.

Gràcies a tots dos per l'ajuda rebuda, prometo el pròxim cop que faci una consulta saber el que he fet abans de postejar el meu dubte.

Dono per solucionat el tema.:lolflag:

---

