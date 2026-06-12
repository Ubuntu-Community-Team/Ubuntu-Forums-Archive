---
title: "[SOLVED] No m'arranca l'ubuntu"
date: 2008-02-18
forum: Catalan Team
---

### Post by Joan Marc on 2008-02-18
Hola de nou,
Tinc un problema, i crec que la causa es que vaig deixar unes actualitzacions a mitges i vaig parar l'ordinador.
EL problema és que l'ubuntu no m'arranca, m'explico, no em mostra els processos de l'inici, tot i que havia esborrat **quiet splash** de l'arxiu del grub, després, em demana el nom d'usuari i contrasenya, i després d'omplir-ho, se'm queda la pantalla de color rosat (el típic d'ubuntu) i no fa res més.
El primer cop que l'he engegat avui (ahir vaig deixar les actualitzacions a mitges) no em surtia el WinXP al grub, i l'ubuntu ja no arrancaba.
He engegat amb el LiveCD, i he editat el grub dient-li que em sortís el WinXP, copiant les línies de la còpia de seguretat que havia fet fa uns dies (consell de'n papapep :)).
Això ha tingut èxit, i almenys puc fer servir l'XP, però l'ubuntu continua sense arrencar.

Què puc fer?

---

### Post by papapep on 2008-02-18
Doncs el que jo faria és entrar al terminal (per exemple, fent Alt+Ctrl+F2) com i fer:

```
sudo apt-get -f install
```

A veure què diu.

---

### Post by Joan Marc on 2008-02-18
He intentat fer el que m'has dit, però m'és impossible iniciar el terminal, ja que al fer Alt+Ctrl+F2, no apareix res de res.
Putser no m'he explicat prou bé abans, però després dep osar el nom d'usuari i contrasenya, la pantalla queda tota rosada, i no hi apareix ni menús, ni escriptori ni funciona res de res, excepte una cosa, l'únic que funciona és el botó de captura de pantalla.
Puc fer alguna cosa desde el LiveCD?

---

### Post by patrickfromspain on 2008-02-18
al grub hauries de tenir una altra entrada d'ubuntu, que hi posa recovery mode. Entra alla i posa el que t'ha dit en papapep.

salut

---

### Post by Joan Marc on 2008-02-18
Problema resolt i amb bons resultats.
He entrat amb recovery mode, i he fet: ```
sudo apt-get -f install
```
M'ha dit, que abans d' escriure-ho, havia d'escriure manualment això:
```
dpkg --configure -a
```
I un munt de coses s'han carregat correctament.
Després he tornat a escriure el que m'heu dit, i m'ha ditt:
```
root@gami:~# sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded
```
I després l'he tancat, i he provat si anava bé, i per gran sorpresa, s'ha iniciat, i a més a més, per primer cop, m'ha aparegut la pantalla de l'ubuntu amb la línia taronja carregant-se.

Bé, gràcies!

PD: Com ho faig manualment per continuar descarregant-me les actualitzacions?

---

### Post by papapep on 2008-02-18
```
sudo aptitude update
```

```
sudo aptitude safe-upgrade
```

Per cert, t'aconsello, si m'ho permets, que no treballis com a root. Fes servir el sudo, però com a usuari "normal". T'estalviaràs disgustos ;)

---

### Post by patrickfromspain on 2008-02-18
sudo apt-get dist-upgrade

---

### Post by Joan Marc on 2008-02-18
mmm... Quin dels tres faig servir?

papapep, no ho he triat jo de fer-ho com a root, sinó que al mode rcovery, m'ha sortit així :confused:.

---

### Post by patrickfromspain on 2008-02-18
els del papapep xD

---

### Post by Joan Marc on 2008-02-18
d'acord :)

Gràcies als dos!

---

