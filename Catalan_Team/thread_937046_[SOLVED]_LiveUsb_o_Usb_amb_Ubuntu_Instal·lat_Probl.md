---
title: "[SOLVED] LiveUsb o Usb amb Ubuntu Instal·lat? Problemes d'execució"
date: 2008-10-03
forum: Catalan Team
---

### Post by LitusMayol on 2008-10-03
ones familia!

Us explico...
Tinc un pendrive nou (per fi!) i hi he instal·lat (amb l'UnetBooting) Ubuntu. Aleshores, com a LivePen (per dir-li d'alguna manera), ha funcionat de conya (excepte en un dels ordinadors de casa, que no m'apareixia l'opció a la BIOS).

Després he pensat que potser seria millor que hi pogués desar coses. Aleshores hi he instal·lat Ubuntu (desde un cd Live típic i tòpic). Després de la instal·lació a /media/disk (el pendrive...) hi havia:

bin   cdrom  etc   initrd      lib         media  opt   root  srv  tmp  var
boot  dev    home  initrd.img  lost+found  mnt    proc  sbin  sys  usr  vmlinuz

En principì bé. Quan he reiniciat l'ordinador, la BIOS no m'ha donat l'opció d'arrencar des del pendrive (consti: ho he fet en l'ordinador on SI ha funcionat com a LivePen).

Aleshores, aquí ve el dubte... Jo vull poder treballar amb Ubuntu vaig on vagi, però m'interessa poder desar els fitxers que  elabori!

   1. Si el torno a convertir en LivePen, un cop estigui arrencat en mode Live... Puc desar-hi fitxers a dins del pen? (vull dir, si puc muntar la partició i crear una carpeta a més de les de la Live que sigui "Memòria" i posar-hi els fitxers de manera que al sortir els preservi -doncs les Live no guarden les dades, oi?-)
   2. O bé és millor que deixi Ubuntu instal·lat... si faig això... com l'arrenco?


Merci!

---

### Post by Miquel Ubuntero on 2008-10-03
Hola company.
Et dic com ho he fet jo i m'ha anat be.
1er he creat 2 particions al Pendrive. Si no saps com fer-ho, pregunta-ho aquí.
2on he instal·lat Ubuntu 8.04 amb unetbootin. O sigui PenLive.
3er Inicio el LivePen, donat que tinc una segona particio lliure, hi puc desar tot el que hem convingui. Per cert, a més de poder dur l'Ubuntu amunt i avall; en el cas de formatar a Fat32, també es pot fer servir per desar dades des de "ruindows".
Continuo fent proves ...
Ja vos informaré.
Salut!

---

### Post by LitusMayol on 2008-10-04
> **Miquel Ubuntero said:**
> Hola company.
Et dic com ho he fet jo i m'ha anat be.
1er he creat 2 particions al Pendrive. Si no saps com fer-ho, pregunta-ho aquí.
2on he instal·lat Ubuntu 8.04 amb unetbootin. O sigui PenLive.
3er Inicio el LivePen, donat que tinc una segona particio lliure, hi puc desar tot el que hem convingui. Per cert, a més de poder dur l'Ubuntu amunt i avall; en el cas de formatar a Fat32, també es pot fer servir per desar dades des de "ruindows".
Continuo fent proves ...
Ja vos informaré.
Salut!

Buaaa sr. **Miquel Ubuntero**!!
Que graan! És molt bona aquesta!

A veure si m'ha quedat clar...

[LIST=1]
[*]**Particiono l'USB.** Amb el **GParted** mateix puc?
[*]**Instal·lo Live** Amb **Unetbootin**(que he de dir-vos, que a mi m'ha anat de conya). Perfecte
[*]**Instal·lo Ubuntu.** O sigui, arrenco amb el LivePen, i instal·lo **Ubuntu** a l'altra partició del pen (però el formato en *Fat32* per poder-hi desar coses? Això no ho he entès... Per instal·lar **Ubuntu** no ha d'estar en *ext3*?)
[/LIST]

D'acord. Fins aquí més o menys. Però aleshores l'arrenco com si la Live fos (prement F11 a la BIOS i especificant que arrenqui des de l'USB? És que ara, que hi tinc **Ubuntu** instal·lat, no el puc arrencar).


Merci!

---

### Post by Miquel Ubuntero on 2008-10-04
Hola de nou. Intentaré explicar-me be.

   1. Particiono l'USB. Amb el GParted mateix puc?

Sí, una eina molt útil.

   2. Instal·lo Live Amb Unetbootin(que he de dir-vos, que a mi m'ha anat de conya). Perfecte

Ok. 

   3. Instal·lo Ubuntu. O sigui, arrenco amb el LivePen, i instal·lo Ubuntu a l'altra partició del pen (però el formato en Fat32 per poder-hi desar coses? Això no ho he entès... Per instal·lar Ubuntu no ha d'estar en ext3?)

De les 2 possibles particions. Una, com tú dius, ext3 per l'Uubntu.
L'altra, deia lo de Fat32 per si vols aprofitar el pendrive i també desar documents quant el conectesis a "ruindows" (volia dir Windows) finestres caca :(


D'acord. Fins aquí més o menys. Però aleshores l'arrenco com si la Live fos (prement F11 a la BIOS i especificant que arrenqui des de l'USB? És que ara, que hi tinc Ubuntu instal·lat, no el puc arrencar).

Correcte, auries de poder arrencar especificant que arrenqui des de USB.
En el cas que no funcioni. Intenta-ho de nou des de el principi. Al tanto!
una cosa important. Quant facis formatar l'USB, cal tindre en comte que la particio on a d'anar Ubuntu a de ser marcada com a "Primaria" i crec que també potser com a "activa".

Espero haber estat clar.
Molta sort!

---

### Post by Miquel Ubuntero on 2008-10-04
Hola de nou.
He estat provant el inetbooting. L'instal·lació és molt fàcil, però li trobo una pega. Tal com he comentat hi ha la possibilitat de desar arxius, però no és pot desar configuració o canvis del s.o. donat que és una sessió "Live".

A mi m'agrada més l'instal·lació tipus "persistent" (+ info a [http://www.pendrivelinux.com](http://www.pendrivelinux.com)) tot i que fer l'instal·lació és més complex, el resultat és més satisfactori. Donat que en poder configurar el s.o. pots posar el teu idioma preferit, afegir programari, ect.

En fi, només volia opinar.
Salut!

---

### Post by LitusMayol on 2008-10-05
Ieeep!

Fet.Però amb problemes.

Potser he sigut massa agosarat. El PenDrive té 4Gb (em marca que en té 3'8...). Suposo que és poc...

El tema és que el Grub funciona de conya. Però després el *login* no em deixa entrar. Escric la contrasenya i l'usuari adequat i es queda en el punt intermig(una pantalla de color crema) però no arriba a entrar a la sessió. Però per contra no ha fet ús de les 4Gb, pensava que potser hi mancaven coses. No: hi "sobren" (mai sobra memòria, no? :)) 1'2Gb lliure.

Havia pensat que una possible solució (ATENCIÓ: potser és una pedrada de les meves!) seria instal·lar-hi **Xubuntu**, a fi de que amb només 4Gb poder-les aprofitar al màxim. A part de poder fer-les servir, perquè ara ja us dic que no em deixa entrar a la sessió...


Algú té una hipotesi o una solució?

Merci de nou!

---

### Post by RainCT on 2008-10-05
> **LitusMayol said:**
> El PenDrive té 4Gb (em marca que en té 3'8...).

Això és perquè realment deu tenir 3.8GB, però per raons de màrqueting el que fan es comptar que "1GB = 1000MB" (en lloc de 1024MB, que és el realment és) i així el número surt més elevat :P.

Si algun cop has vist escrit "GiB" (o "MiB" o el que sigui), això assegura que el nombre està en potències de 1024 (sense la "i" hauria de ser de 1024 també, però hi ha els espavilats aquests que ho fan com si fos 1000).

(Tot això ho sé perquè ara estan discutint sobre si l'Ubuntu hauria de mostrar les mides com a potències de 1024 o de 1000, per no confondre la gent -o per confondre-la més XD- :P).

*Uhm... I no sé perquè ho he escrit tot això ara xDDD.*

---

### Post by LitusMayol on 2008-10-12
Perdoneu,

tanco el fil.


Finalment hi he posat una Live amb **Unetbootin** i ja està... a tot cas, ja instal·laré **Ubuntu** en un HDD extraïble. ;) No patiu que segur que si ho faig caurà algun fil sobre el tema... hehehe

Merci a tots.

(**RainCT**, encara que no t'ho sembli el teu post m'ha estat útil. No ho sabia això del Gib. I no està gens de més saber-ho: merci!)

---

