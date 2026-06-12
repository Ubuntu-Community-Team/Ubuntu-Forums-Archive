---
title: "[SOLVED] Després de recuperar Grub no accepta login"
date: 2008-09-29
forum: Catalan Team
---

### Post by farigola on 2008-09-29
Vaig instal·lar Windows i fruit d'això vaig tenir la típica incidència del Grup. Un cop recuperat aquest al meu ordinador procedeixo a iniciar la Ubuntu 8.04.1 Kernel 2.624-19-generic i surt la pantalla per escollir usuari. Procedeixo a introduir la clau i surt una pantalla negre per dos segons i torna a la pantalla de login. Estic segur que la clau és la que toca doncs al posar una errònia surt el corresponent avis. 
He fet una revisió per diferents fòrums i crec que això és un bug. No se si teniu coneixement de com recuperar l'inici de l'ordinador. He de dir que aquest ha estat 20 dies parat sense ser utilitzat, però no crec que sigui aquest el motiu. Teniu alguna idea?

---

### Post by farigola on 2008-09-29
Per cert tinc KDE 4.0

---

### Post by farigola on 2008-09-29
Estic un xic preocupat per el comportament del meu ordinador. Resulta que si deixo l'equip sense introduir la clau de pas durant uns minuts (potser 10) Llavors tinc possibilitat d'iniciar i veure l'escriptori però aquest no funciona correctament doncs hi ha eines que no poden ser utilitzats "actualitzador de paquets" no funciona.

---

### Post by tanreb20 on 2008-09-29
has provat d'inciar en mode text?

diria que quan s'et posi la pantalla per posar l'usiari apreta ctrl + alt + F1 i entraries al mode consola.

Prova de psoar el teu usuari i el teu password a veure que passa.

---

### Post by farigola on 2008-09-30
La cosa sembla ser de bruixes. Vaig deixar la pantalla de login durant uns minuts oberta i pendent d'identificació. Després d'escriure diferents correus amb el portàtil vaig inserir el login i va funcionar. Després de veure el contingut de l'escriptori vaig tornar a iniciar l'equip i el problema va tornar. Avui he fet el mateix i després de diferents minuts he aconseguit reiniciar l'equip. Ara veig que Adept no funciona i no aconsegueix actualitzar paquets (no debugging simbols found)
El meu coneixement de tot això del Linux es força justet i crec que tot plegat podria tenir cert lligam amb la configuració actual del GRUB, però no estic segur.

Ara miro de trobar quelcom en referència al adept!

---

### Post by farigola on 2008-10-07
Avui no he aconseguit iniciar una sessió gràfica doncs la pantalla sempre queda en petició de logon. Avui he vist que des de terminal si que tinc possibilitat de iniciar sessió. Potser els sistema gràfic s'ha quedat fet una coca, però no entenc el motiu d'aquest problema doncs abans de fer la instal·lació de Windows la cosa funcionava perfectament.
Total que el meu Kubuntu ha deixar de funcionar. Crec que el millor serà iniciar amb cd, copiar \home i tornar a instal·lar el sistema.
:(

---

### Post by tanreb20 on 2008-10-07
Abans de fer aixo prova a fer:

```
sudo dpkg-reconfigure xserver-xorg
```

i a veure si pots arreglar-ho!

---

### Post by oriolsbd on 2008-10-09
Hola, pots mirar si falta espai en algun FileSystem? Entrant en un terminal, executa la següent comanda:

```
df -k
```

No crec que sigui això (perquè comentes que després d'uns minuts esperant sí que t'entra al sistema), però és una comprovació molt tonta i no costa res fer-la.

Salut!

---

### Post by farigola on 2008-10-09
Gràcies per el vostres comentaris. Aquesta nit he de fer proves. Un cop tingui els resultats els insereixo fòrum.

---

### Post by farigola on 2008-10-11
Hola, 
Ja tinc l'ordinador recuperat, ahir vaig veure el problema i tot gràcies al vostres comentaris. La cosa al final va estar en un tema d'espai en disc doncs sense saber-ho com l'equip va quedar al 100%. Tot va estar en que al final ja només podia fer logon des de una terminal. Vaig executar el df-k per veure que el disc de dades el tenia al 100% vaig esborrar uns fitxers mp3 i ja vaig iniciar l'equip. Després vaig iniciar un cerca per l'ordinador i vaig veure un directori de mes de 30Gb "Strigi"

Bé doncs ja està. Moltes gràcies per tot.

---

