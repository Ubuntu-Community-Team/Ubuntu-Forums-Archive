---
title: "[SOLVED] Configuració d'internet"
date: 2008-11-20
forum: Catalan Team
---

### Post by markinux on 2008-11-20
Hola a tothom
Us plantejo el meu problema:
En un principi tenia la xarxa configurada correctament amb els camps de l'adreça d'IP, màscara de subxarxa... completats correctament i em podia connectar a Internet, això ja des del moment que vaig instal·lar-me el linux.
Però en el moment en que apago o reinicio l'ordinador es perden les dades de la configuració d'Internet, i he de tornar a apuntar els números dels paràmetres d'IPV4.
Sabeu com es fa perquè se'm guardi la configuració?

Gràcies a tothom


Salutacions

---

### Post by papapep on 2008-11-20
Benvingut al fòrum, Markinux. Veig que ets un noi aplicat i ja has passat pel fil de benvinguda. Ja seria una canya que també t'haguéssis llegit l'altre fil per a nouvinguts ;-)

Respecte el problema que comentes, amb quina versió d'Ubuntu t'està passant? 

Crec recordar que no fa massa hi va haver un fil que parlava d'això...però ara no el sé trobar...:-/

En tot cas, fes a un terminal:

```
cat /etc/network/interfaces
```

i enganxa'ns aquí el que et mostri, si us plau.

---

### Post by markinux on 2008-11-20
Aquí deixo el meu terminal:

 ```
trias@trias-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

trias@trias-desktop:~$ 
```

Tinc la versió 8.10, que jo sàpiga la última versió.

---

### Post by papapep on 2008-11-20
Fes a un terminal:

```
sudo -s
```

i després

```
echo "iface eth0 inet static" >> /etc/network/interfaces
```

i

```
echo "auto eth0" >> /etc/network/interfaces
```

amb això afegiràs aquestes dues línies al fitxer. Reinicia l'ordinador i a veure si ara funciona correctament.

---

### Post by markinux on 2008-11-20
Ara em posa això:
```
trias@trias-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

trias@trias-desktop:~$ sudo echo "iface eth0 inet static" >> /etc/network/interfaces
bash: /etc/network/interfaces: Permission denied
trias@trias-desktop:~$ sudo echo "auto eth0" >> /etc/network/interfaces
bash: /etc/network/interfaces: Permission denied
trias@trias-desktop:~$ 

```

Ara reinicio l'ordinador i havera que passa.
Gràcies

---

### Post by markinux on 2008-11-20
Segueix igual. Novament he hagut de omplir els parametres d'IPv4 per a conectar-me.

---

### Post by papapep on 2008-11-20
Després de les dues ordres que t'he dit, que comencen per "sudo", has posat la teva contrasenya??? Quan et surt: 

```
[sudo] password for trias-desktop:
```

t'està demanant que posis la teva contrasenya, per poder efectuar aquesta tasca (la de les ordres) que necessiten drets d'administració.

Si tornes a fer el:

```
cat /etc/network/interfaces

```

veuràs com el fitxer segueix igual.

---

### Post by PatrickVogeli on 2008-11-20
sudo echo no funcionara mai. Una manera es fer sudo -s i llavors els echo.

salut

---

### Post by papapep on 2008-11-20
Perdó, cert.....

---

### Post by markinux on 2008-11-22
Noc puc posar la contrasenya perquè al crear el terminal de sudo pasword for trias no em deixa escriure ni lletres ni números, i tampoc em puc moure amb les flextes. 
Com puc apuntar la meva contrasenya?

---

### Post by PatrickVogeli on 2008-11-22
sudo -s i poses la contrasenya, encara que no veguis res de res, s'esta posant be.

---

### Post by oriolsbd on 2008-11-22
Quan et demana la paraula de pas, tu l'has d'escriure, però per pantalla no et mostra el que vas escrivint (ni asteriscos ni res). Simplment, escriu-la i prem "Enter".

Salut!

---

### Post by markinux on 2008-11-22
He fet el que m'heu dit però quan he reiniciat el sistema havia perdut la configuració de xarxa, i aquest cop no estava ni configurada amb el nom eth0. I quan la configurava, no sé que passava però tampoc tenia connexió.
He tornat a instal·lar l'ubuntu 8.10 i curiosament m'ha detectat la configuració d'internet i ara ja no s'em perd quan tanco o reinicio l'ordinador.
Gràcies a tothom igualment.
Gràcies papapep, ara ja sé que és un terminal!!!

Com que ja tinc el problema solucionat, per mi, dono el post per tancat.

---

### Post by papapep on 2008-11-22
Doncs triple enhorabona! per resoldre el problema, per passar-te a gnu/linux i per descobrir el terminal! :-D

Marca el fil com a resolt, triant l'opció "Mark thread as solved" al damunt del fil a "Thread tools".

---

