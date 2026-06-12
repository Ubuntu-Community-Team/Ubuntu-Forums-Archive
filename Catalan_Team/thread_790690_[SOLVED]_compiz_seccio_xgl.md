---
title: "[SOLVED] compiz seccio xgl"
date: 2008-05-11
forum: Catalan Team
---

### Post by abosch on 2008-05-11
Volia provar el compiz, seguint consell [d-aqui]("http://www.ubuntu-es.org/index.php?q=node/87554") he excecutat l-ordre ```
sudo aptitude install xserver-xgl


``` llavors si vaig a terminal em surt ```
abosch@abb-portatil:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 945GM 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 7.0.1

abosch@abb-portatil:~$ compiz --replace
Checking for Xgl: present.
Checking for nVidia: not present.
Checking for Xgl: present.
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: Support for non power of two textures missi                                                              ng
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0
abosch@abb-portatil:~$

``` suposo que alguna cosa no he fet *prou( be :(
a m'es la pantalla va com 'al relenti' i ara estic notant que els simbols i les tecles no s-entenen ...[-(    em podeu recomanar que fer?  

gracies
Alex

---

### Post by CarlesOriol on 2008-05-12
No hauries d'usar això en la teva gràfica Intel 945.

Tens hardy o gutsy? En hardy t'hauria de funcionar directament.

En qualsevol cas desinstala el xgl ja que no funciona bé en el teu ordinador.
Mira que s'està embolicant en dues linies:

    OpenGL renderer string: Mesa DRI Intel(R) 945GM 20061017 x86/MMX/SSE2
i
    Enabling Xgl with fglrx ATi drivers...



L'xgl és un servidor x alternatiu al xorg standard desenvolupat per novell a porta tancada. Va ser el primer en permetre efectes d'escriptori "xulos" però un temps més tard l'xorg va treure la extensió aiglx que s'ha acabat convertint en l'"standard".
Però hi ha controladors de gràfiques i gràfiques que encara no suporten el aiglx i per en aquests casos es pot provar d'usar el xgl per veure la composició d'escriptori.

---

### Post by abosch on 2008-05-12
Gràcies CarlesOriol,
> L'xgl és un servidor x alternatiu al xorg standard desenvolupat per novell a porta tancada. Va ser el primer en permetre efectes d'escriptori "xulos" però un temps més tard l'xorg va treure la extensió aiglx que s'ha acabat convertint en l'"standard".
Però hi ha controladors de gràfiques i gràfiques que encara no suporten el aiglx i per en aquests casos es pot provar d'usar el xgl per veure la composició d'escriptori.   



Tinc Gutsy, encara no he actualitzat ... aquesta era l'intenció, no haver de reinstal.lar, però ...:(  ahir vaig continuar 'remenant' i després de carregar-me l'acceleració gràfica 3D i m'he quedat també sense entorn gràfic. Quant engego la màquina puc iniciar sessió però tot per text.

El que vaig fer és tirar endavant amb el que posa l'article, crear seccions 'Extensions' i 'ServerFlags' . I també el directori per la nova entrada del Gnome amb XGL . Espero no haver-ho embolicat molt ...

Per casa tinc el l'interpret de comandes (ara volia imprimir la xuleta ordres del wiki, pero no puc entrar-hi).Sòc novell, he d'executar l'odre ?

 ```
sudo apt-get remove -purge xserver-xgl
```

tanmateix hauria de recuperar la sessió que prèviament tenia ¿? ... he llegit en un altre post semblant que es recomana fer un

 ```
dpkg-reconfigure ubuntu-desktop
``` potser he d'anar per aquí? 


Tot consell és de molta ajuda, 
gràcies


PS. He conseguit treure la xuleta-wiki ----> gràcies

---

### Post by CarlesOriol on 2008-05-12
un 

sudo apt-get remove xserver-xgl

hauria de ser suficient.

...i pufff les instruccions que vas seguir no eren necesaries per a la gutsy. 

Recorda un cop finalitzat eliminar les entrades al xorg.conf ja que et molestaran de cara a l'actualització a la hardy.

---

### Post by abosch on 2008-05-12
Ara mateix vaig a provar-ho :popcorn:




acabo de recordar el mític fil del@ Druiling .... quin munt d'info que conté ... [l'enllaço]("http://ubuntuforums.org/showthread.php?t=742429&highlight=entrada+gnome")  

merci
apasiau

---

