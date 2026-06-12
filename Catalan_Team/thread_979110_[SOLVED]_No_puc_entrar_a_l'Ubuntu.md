---
title: "[SOLVED] No puc entrar a l'Ubuntu"
date: 2008-11-11
forum: Catalan Team
---

### Post by PauB on 2008-11-11
M'he baixat l'Ubuntu del rebost de Softcatalà, he fet servir la guia d'instal·lació que hi tenen penjada, i em pensava que em passaria com en els ordiandors que havia fet servir que el tenen: que en engegar em permetria triar entre el Windows (Vista, que és el que tinc) i l'Ubuntu, però no em deixa triar i vaig directament al Windows. I això que la partició ha anat bé (ara em diu que tinc menys disc dur) i que he acabat la instal·lació.

Algú em sap dir si és que ha fallat alguna cosa o si és que he de fer res més que m'he saltat?

---

### Post by SiscoGarcia on 2008-11-11
Hola PauB, benvingut al fòrum. No oblidis passar-te pels fils de [benvinguda]("http://ubuntuforums.org/showthread.php?t=562776") i [tutorial del fòrum]("http://ubuntuforums.org/showthread.php?t=599965") i explicar-nos una mica sobre tu mateix ;)

Pel que fa al teu problema és típic del Vista. Pots trobar un tutorial [aquí]("https://wiki.ubuntu.com/CatalanTeam/Recursos/ArrencadaDualAmbWindows?action=show&redirect=CatalanTeam%2FRecursos%2FArrencada_dual_Ubuntu_i_Windows") que et servirà d'ajuda. Allà hi trobaràs un pdf amb l'explicació de com redimensionar el [maligne]("http://badvista.fsf.org/") abans d'instal·lar-hi l'ubuntu per evitar aquests problemes. Ja diràs.

---

### Post by papapep on 2008-11-11
Hola Pau, benvingut al fòrum.

Si no ho has fet ja, et convido a fer una bona llegida als dos fils de capçalera pels nouvinguts, el de presentació i l'altre on intentem explicar una mica com intentem funcionar.

Probablement al punt de l'instal·lació on demana on instal·lar el Grub (el programa que comentes que et permet triar el sistema operatiu a l'inici) l'has instal·lat on no toca.

Jo t'aconsellaria tornar a fer tot el procés d'instal·lació (assumeixo que tens còpia de totes les dades importants del teu ordinador, oi??) a fi de familiaritar-te amb ell i veure el pas aquest del Grub. En principi l'hauries d'instal·lar al MBR, i així t'hauria de detectar correctament tots els sistemes operatius que tinguis al disc dur.

Hi ha maneres més "professionals" o avançades per a fer-ho, però crec que donada la teva (normal) inexperiència, val més fer-ho fàcil i didàctic. ;-)

EDITO: Bé, com podeu comprovar, en Siscu se m'ha adelantat mentre feia el post i he repetit part del seu, però vaja, la resta queda igual :-)

---

### Post by PauB on 2008-11-12
Gràcies per les respostes, però...

...si ho entès bé, ara ja l'he cagada i la sortida que em queda és fer net i tornar a instal·lar tots dos sistemes operatius?

En el manual d'instal·lació no deia res de cap Grub. snif... i on se suposa que l'he d'instal·lar?

---

### Post by papapep on 2008-11-12
Pau, exactament el que has fet ho tenim difícil per a saber-ho ja que no som al davant del teu ordinador, però tens dues possibilitats:

 a) realment t'has equivocat i al particionar el disc dur t'has passat per la pedra el windows.

 b) l'únic que no has fet bé és on instal·lar el grub, i segueixes tenint el windows a la seva partició ben esparrufadet.

Ara no recordo si el cd Desktop t'ho pregunta o no, però [l'Alternate]("http://releases.ubuntu.com/intrepid/ubuntu-8.10-alternate-i386.iso"), que és el que faig servir jo sempre, sí que ho fa. Et demana si vols instal·lar-lo (el Grub) al MBR o al principi de la primera partició del disc que conté l'Ubuntu. Normalment, la primera opció és la que funciona correctament.

---

### Post by PauB on 2008-11-12
No si el Vista el conservo (és l'únic que em trobo en entrar), només que encabit en un disc que ara és més petit.

Per això mateix en llegir que he d'instal·lar un altre cop l'Ubuntu m'he quedat amb el dubte de si això vol dir tornar-ho a instal·lar tot, en el sentit de què no sé si és necessari per recuperar aquesta part morta del disc dur o si és on s'instal·larà un altre cop l'Ubuntu si només instal·lo de nou aquest. El que em fa por és que instal·lant només l'Ubuntu un altre cop em demani una nova partició per a ell i que em devori un altre tros del disc dur (que potser torni a quedar mort).

Gràcies per les pacients respostes.

---

### Post by papapep on 2008-11-12
:-D No Pau, el disc dur no té ni parts "mortes" ni res semblant, no has de patir per això...

L'únic que hauries de fer, és tornar a repetir la instal·lació de l'Ubuntu(a poder ser aquest cop amb el cd Alternate) i dir-li que t'instal·li el Grub al MBR. Les particions que vas crear a la primera instal·lació ja et serviran, no cal tornar-les a refer. Quan arribis al punt de l'instal·lador que et demana les particions, digues-li que faci servir les que ja vas fer abans i ja està.

---

### Post by oriolsbd on 2008-11-12
Si no recordo malament, a la instal·lació "Desktop" també hi ha aquesta opció. És al'última pantalla de totes (quan hi ha el resum de tot el que has escollit), hi ha un apartat d'opcions avançades. Si no li dius res (o sigui, si no entres a les opcions avançades), t'instal·la el Grub correctament al MBR.

---

### Post by PauB on 2008-11-12
He intentat seguir-ho amb l'altre .iso recomanat, però demana tenir encara més conexeiements específics (suposo que a vosaltres ja no us ho semblarà, però sí), de manera que he tornat a l'anterior.

Veig que per evitar que no em faci el que em feia por i torni a dividir la part que li queda al Vista he d'escollir la partició manual.

El problema és que en escollir una partició, em demana dues eleccions que no sé fer.

La primera és "utilitza-ho com a" on em deixa triar entre:

-Sistema de fitxers transaccional ext 3
-Sistema de fitxers ext2
-Sistema de fitxers transaccional ReiserFS
-Sistema de fitxers transaccional JFS
-Sistema de fitxers transaccional XFS
-Sistema de fitxers FAT16
-Sistema de fitxers FAT32
-Àrea d'intercanvi
-No utilitzes aquesta partició

La segona elecció és "punt de muntatge" i em deixa triar entre:
-/
-/boot
-/home
-/tnp
-/usr
-/var
/-src
-/opt
-/usr/local

Sabeu què he de triar?

Perdoneu-me si aquesta informació estava amagada en enllaços passats abans, però no ho he sabut trobar.

---

### Post by papapep on 2008-11-12
Ara que som aquí, estaria bé saber quines particions tens tant pel Vista com la resta. Així tindrem més informació per saber on som.

Respecte el tipus del sistema de fitxers, l'actual recomanable és ext3. 
La segona pregunta te la podré respondre quan sàpiga quines particions tens.

---

### Post by PauB on 2008-11-13
I quines dades i on les aconsegueixo exactament?

A vore, mirant-ho pel Vista em diu que tinc tres particions.

La principal del Vista d'uns 200 Gigues, classificada com a NTFS, i "Sistema, Arranque, Archivo de Paginación, Activo, Volcado, i Partición primaria".

La segona que havia d'estar destina per a l'Ubuntu, d'uns 90 gigues, classificada simplement com a "partición primaria".

I una tercera que no sé d'on coi ha sortit, de 4 gigues marcada com a "espacio libre".

Era això?

---

### Post by papapep on 2008-11-13
Dues coses:

 1.- Si fas dos talls a una patata, en resulten tres trossos, oi? doncs la "[tercera partició desconeguda]("http://www.youtube.com/watch?v=tUcOaGawIW0")" és el tercer tros de patata :-)

 2.- Et falta la partició d'intercanvi (swap), sinó el Gnu/Linux pot tenir problemes. L'has de crear amb l'"espai perdut" o eliminant la de l'Ubuntu i creant-ne dues (la de l'Ubuntu i la d'intercanvi). La mida sol ser del doble de la memòria RAM que tinguis, sense superar, en condicions normals, els 2 Gb de partició. La regla es va establir (no formalment) en temps en que la RAM era molt més cara i escassa que ara. :-)

De fet, també seria recomanable crear-ne una pel /home, per si et cal tornar a instal·lar o actualitzar no tenir problemes amb les dades personals.

Aleshores tindries (sense considerar la NTFS), dues particions ext3, una amb punt de muntatge a / (de no més de 10 Gb) i l'altra a /home (la resta) més una d'intercanvi de només de 2 Gb.

---

### Post by PauB on 2008-11-17
Vaig reintentar-ho aquest cap de setmana i el procés semblava aturar-se en el moment d'indicar-me que estava avaluant l'estat de la bateria. Em posava [OK], però no canviava de pantalla.

Sona malament, oi?

---

### Post by PauB on 2008-11-18
Us escric des del meu nou i flamant Ubuntu!

Petonassos a tots!

---

### Post by SiscoGarcia on 2008-11-18
> **PauB said:**
> Us escric des del meu nou i flamant Ubuntu!

Petonassos a tots!

Enhorabona, PauB, ara només cal que marques el fil com a resolt (Thread Tools > Mark This Thread As Solved), així qui vinga darrere sabrà que aquest tema està solventat i potser li serà d'utilitat ;)

---

