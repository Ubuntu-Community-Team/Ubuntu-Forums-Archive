---
title: "Disc dur extraible"
date: 2008-01-08
forum: Catalan Team
---

### Post by Joan Marc on 2008-01-08
Hola a tothom.
Els reis m'han portat un disc dur extraible (ConceptronicCSM3PL500).
El cas és que he guardat documents i carpetes de windows i des de windows, al disc extraible, i en algunes carpetes, em surt un candau a sobre (adjunt), i això fa que pugui veure el contingut de la carpeta però que no la pugui ni canviar de nom, ni guardar-hi res a dins.

Algú sap per què passa i com solucionar-ho?

Gràcies :)

---

### Post by papapep on 2008-01-08
És un problema dels permisos que t'hi ha posat el windows.

Si, per exemple, el teu disc dur és /media/disk, el teu usuari és jmarc, i vols donar a tots els fitxers dins aquesta partició permisos totals per al teu usuari i només de lectura per a la resta d'usuaris del teu grup d'usuari i la resta d'usuaris del món mundial, fes:

```
chown jmarc:jmarc /media/disk -r
```

amb això hem fet que tots els fitxers siguin de propietat del teu usuari.
Ara pots fer:

```
chmod 744 /media/disk -r
```

amb això li dius que apliqui els permisos que abans hem esmentat.

Per a més informació al respecte:

[https://wiki.ubuntu.com/JosepS%c3%a0nchez/documentaci%c3%b3/interpret_comandes#head-3788c5ad6871630006ca18ed74c5f0a460ece417](https://wiki.ubuntu.com/JosepS%c3%a0nchez/documentaci%c3%b3/interpret_comandes#head-3788c5ad6871630006ca18ed74c5f0a460ece417)

---

### Post by Joan Marc on 2008-01-08
He fet el que m'has dit, però en surt això:
```
gami@Gami:~$ chown gami:gami /media/CSM3PL500 -r
chown: invalid option -- r
Try `chown --help' for more information.
gami@Gami:~$ 

```

Gràcies.

---

### Post by papapep on 2008-01-08
Perdó:

```
sudo chown gami:gami -R /media/CSM3PL500
```

i l'altre igual, amb sudo i la R majúscula.

---

### Post by Joan Marc on 2008-01-08
Al final de cada arxiu em diu: Operation not permitted.
Per què no està permès¿?

---

### Post by papapep on 2008-01-08
Si no ens ensenyes l'error exacte, i la ordre que el provoca, no podem ajudar-te.

---

### Post by Joan Marc on 2008-01-08
Ni ha la tira, te'n poso un d'exemple, ja que tots són iguals:
```
chown: changing ownership of `/media/CSM3PL500/Joan Marc/Linux-Ubuntu 64bits/Ubuntu 64bits Documents/TREBALLS DE CLASSE/Treball familia/Bibliografia.doc': Operation not permitted
```

---

### Post by papapep on 2008-01-08
Però no has enganxat la ordre que l'ha provocat. Posa el que tu has teclejat.

---

### Post by Joan Marc on 2008-01-08
No ho he posat perquè al terminal, després de posar l'ordre i la contrasenya em surt un procés. És com si hi haguéssin tants processos que no cabessin al terminal, i el primer que surt es aquest:
```
chown: changing ownership of `/media/CSM3PL500/Joan Marc/Linux-Ubuntu 64bits/Ubuntu 64bits Documents/TREBALLS DE CLASSE/Treball familia/Antonia Riera Alzina.doc': Operation not permitted

```

L'ordre que li he dit és:
```
sudo chown gami:gami -R /media/CSM3PL500
```

---

### Post by papapep on 2008-01-08
Enganxa el resultat de un:

```
ls -la /media/CSM3PL500
```

Quin és el format del sistema de fitxers del disc?

---

### Post by Joan Marc on 2008-01-08
M'ha sortit això:
```
gami@Gami:~$ ls -la /media/CSM3PL500
total 164
drwx------ 6 gami root 32768 1970-01-01 01:00 .
drwxr-xr-x 6 root root  4096 2008-01-08 18:23 ..
drwx------ 4 gami root 32768 2008-01-06 23:45 Joan Marc
drwx------ 2 gami root 32768 2008-01-06 11:02 Recycled
drwx------ 3 gami root 32768 2008-01-06 10:10 System Volume Information
drwx------ 2 gami root 32768 2008-01-08 18:26 .Trash-gami
gami@Gami:~$ 
```

Si els he creat amb Windows, el propietari del fitxer serà el del windows? Amb linux en soc propietari o no?

El format és FAT32, hi té res a veure?

---

### Post by Joan Marc on 2008-01-10
Ho dic pel que diu si miro això:

---

