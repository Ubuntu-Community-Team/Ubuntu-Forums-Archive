---
title: "[SOLVED] Problemes amb la consola de l'escriptori"
date: 2007-12-02
forum: Catalan Team
---

### Post by alhanduin on 2007-12-02
Bones!

Ja torno a ser aquí amb més problemes per resoldre!!!! Elk em passa ara és que vaig intentar posar una consola a l'escriptori (d'aquestes que no es mouen d'allí i que son quasi transparents...) i ho vaig fer seguint el tutorial que hi ha a la quia ubuntu, pero tinc 2 problemes:

1.- Només em surt en un dels 4 escriptoris que tinc
2.- No surt a la posició exacta on jo la poso (vaig probant empíricament amb altres pantalles de la consola fins a trobar quina és la posició que vull i aquella és la que poso al alltray que és a la cantonada inferior dreta i em surt allí però desplaçada al mig, ara bé, si obro un lanzadaor amb una consola en aquelles coordenades s'obra on jo vull....)

No se si m'he explicat bé.... espero que m'entengueu i em pogueu ajudar que vull començar a treure-li suc a la consola.

Moltes gràcies per adelantat!!!!

---

### Post by papapep on 2007-12-02
Doncs jo no acabo d'entendre ben bé de quina "consola" parles (crec que és bastant millor que tu t'expliquis que no pas que els altres haguem d'assumir coses...), però per a poder decidir on posar i com, els programes en el moment d'execució, hi ha un programa que es diu **[devilspie]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=devilspie&searchon=names&subword=1&version=gutsy&release=all")**, el qual et permet decidir posició, mida, etc...

---

### Post by alhanduin on 2007-12-02
A vere ho tornaré a intentar....

Vaig llegir a la guia ubuntu que podia posar una terminal o consola a l'entorn de l'escriptori de manera fixa i permanent utilitzant un programa anomenat alltray.

Els passos que s'havien de fer eren:

1.- DEscarregar-te l'alltray
2.- obrir una terminal anar al botó editar --> perfil i crear un nou perfil
3.- Editar el nou perfil creat: - Desactivar l'opció: Mostrar la barra de menús
                                             - Activar fondo transparente
                                             - Desactivar la barra de desplaçament

4.- Un cop fet això miraves les coordenades de l'escriptori on volies que es quedés fixada la terminal.

5.- Anaves a Sistema --> Preferencias -->Sesiones --> Añadir
6.- Al recuadre on posa comando havies d'escriure:

alltray -x -st -g +600+430 "gnome-terminal --geometry=50x17 --window-with-profile=ruy"

(600+430 son les coordenades i 50x17 la mida de la terminal)

Fet tot això t'hauria de sortir una terminal transparent i fixa a l'escriptori.

El meu problema és:

1.- Només em surt en un dels 4 escriptoris que tinc configurats
2.- No surt a les coordenades que jo li donc.

Espero haver-me explicat millor ara jejejeje

Moltes gràcies

---

### Post by papapep on 2007-12-02
Ara si.

Bé, respecte l'alltray aquest ni idea, però el que si que funciona correctament és el que t'he comentat abans. 
Per cert, l'alltray serveix ([segons diu la base de paquets]("http://http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=alltray&searchon=names&subword=1&version=gutsy&release=all")) per a:

> Package alltray

    * gutsy (x11): Dock any program into the system tray [universe]
      0.69-1: amd64 i386 powerpc


"Ficar qualsevol programa a la barra de sistema". 

No parla de ficar-lo a tots els espais de treball com tu esmentes.

Per a això fes un cop d'ull al** devilspie**, que aquest el tinc provat i funciona (Tot i que amb Compiz activat no em va bé, només amb el gestor de finestres per defecte de Gnome, Metacity).

---

### Post by alhanduin on 2007-12-02
Okis gràcies! ho buscaré i ja et diré com m'ha anat!

---

### Post by CarlesOriol on 2007-12-02
Ups.... em sembla que t'estas embolicant.

Prova en gnome amb el tilda (bastant fluixot) i en kde amb el yakuake (aquest fa enveja malsana :-) )

---

### Post by papapep on 2007-12-02
El tilda m'anava bé amb Feisty, però amb Gutsy no es veu bé (amb el Compiz activat...)

---

### Post by alhanduin on 2007-12-02
Ja ho he solucionat!

He trobat un how to que utilitzava el devilspie i ja he pogut posar-ho en totes les meves àrees de treball.

Moltes gràcies a tots!!

---

