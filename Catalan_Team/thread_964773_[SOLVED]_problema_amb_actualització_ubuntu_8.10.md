---
title: "[SOLVED] problema amb actualització ubuntu 8.10"
date: 2008-10-31
forum: Catalan Team
---

### Post by loles on 2008-10-31
Hola,

Sóc relativament nova amb ubuntu i ja he tingut un greu problema per passar-me de llesta!

A vore, ahir vaig començar a baixar-me l'actualització de l'ubuntu al meu portàtil, amb tan mala sort, i descuit de la meua part, que es va acabar a bateria a la meitat del procès.

Aquest matí he engegat el portàtil i no hi ha manera de que passe de la primera pantalla. S'escolta el so d'inici, on et demana el nom d'usuari, però és torna a iniciar aquesta pantalla una i altra vegada. No em deixa que escriga res de res.

QUÈ PUC FER???

He pensat en gravar l'actualització a un CD i arrancar directament. Açò pot funcionar? Perdré la informació del meu disc dur?

Us agrairia moltíssim si em puguereu tranquilitzar i ajudar!

---

### Post by kukat on 2008-10-31
Jo el que faria, primerament, es amb un LiveCD, entrar amb ell i agafar tota la informació que puges (fotos, videos, etcètera...) Has fet l'actualització, i se t'ha apagat el portàtil... Tens les dades en altres particions? Si es així no hi haurà cap problema. I si no, prova de rescatar-ho en un liveCD.....

---

### Post by kukat on 2008-10-31
Però no facis res estrany fins que no parlen els grans mestres del forum!

---

### Post by loles on 2008-10-31
gracies kukat per la teua resposta

la veritat és que tinc dos particions i tinc informació en les dues que m'agradaria rescatar... 

això del live cd, on puc descarregar-lo? com funciona exactament?

---

### Post by badChecksum on 2008-10-31
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Un LiveCD és un CD que porta dins un sistema operatiu, en aquest cas l'Ubuntu. Al ficar-lo dins el lector de CDs i reiniciar l'ordinador en comptes de carregar el SO instalat es carrega el SO del CD. 

Així des d'aquí podries accedir al teu disc dur, guardar les dades en algun lloc segur i reinstalar el sistema operatiu si fés falta.

Salut

---

### Post by CarlesOriol on 2008-11-01
Tens connexió a internet per cable?

Si és així entra a la consola (ctrl+alt+f1)
i finalitza la insta&#320;lació

sudo apt-get -f install

---

### Post by indiosincracia on 2008-11-01
> He pensat en gravar l'actualització a un CD i arrancar directament. Açò pot funcionar? Perdré la informació del meu disc dur?QUÈ PUC FER???

per arrancar no, perdràs la info si l'instal·les.

la solucio d'en Carles t'hauria de funcionar, i
no està de més tenir sempre un CD-Live a mà, d'aquests que s'engeguen ràpidament slax, knoppix etc...

---

### Post by loles on 2008-11-01
moltes gràcies a tots per ajudar-me

una pregunta mes, si arranque l'ordinador amb el livecd puc canviar els arxius a una particio del disc dur i així salvar-ho tot? aquesta opció és possible abans de actualitzar el sistema?

no sé massa bé com he de fer-ho...

---

### Post by SiscoGarcia on 2008-11-01
Loles no tingues por de fer el que t'ha dit el Carles; això t'ha de funcionar. No t'espantes quan en fer "ctrl+alt+f1" (sense cometes) el monitor es pose negre, ja és això el que ha de fer! Llavors escriu "sudo apt-get -f install" (sense cometes) i continuarà la instal·lació.

A mi també m'ha passat alguna vegada que se m'ha aturat la instal·lació a mig fer però no he perdut res (tot i que cada cas és diferent).

---

### Post by CarlesOriol on 2008-11-02
> **loles said:**
> una pregunta mes, si arranque l'ordinador amb el livecd puc canviar els arxius a una particio del disc dur i així salvar-ho tot? aquesta opció és possible abans de actualitzar el sistema?

Si, evidentment.

un cop iniciat el sistema live pots muntar els discs.

la forma fàcil:

1. crear una carpeta on muntar el disc:

**mkdir discmuntat**

2. muntar el disc a la carpeta (per ext3)

**sudo mount /dev/sda1 discmuntat**

(compte que els discs muntats conserven tota l'estructura de permisos)

---

### Post by CarlesOriol on 2008-11-02
Si es va aturar configurant els programes pot ser que en comtpes del

**sudo apt-get -f install**

hagis de fer

**sudo dpkg --configure -a**

---

### Post by loles on 2008-11-03
gracies a tots, ja ho he solucionat

vaig ficar a la consola les ordres per tornar a instal·lar i fi del meu problema

tot recuperat! i per ara... la nova versió no em dona cap problema... que continue així!

---

### Post by SiscoGarcia on 2008-11-03
> **loles said:**
> gracies a tots, ja ho he solucionat

vaig ficar a la consola les ordres per tornar a instal·lar i fi del meu problema

tot recuperat! i per ara... la nova versió no em dona cap problema... que continue així!

Ara Loles toca marcar el fil com a resolt, és a dir, ves a "Thread Tools" i a baix de tot fes "Mark This Thread As Solved" (això només ho pots fer tu o un administrador del fòrum -els que tenen el nom en verd-), com diu el [fil de benvinguda]("http://ubuntuforums.org/showthread.php?t=599965") a l'apartat 12 ;)

---

