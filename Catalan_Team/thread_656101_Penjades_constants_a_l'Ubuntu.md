---
title: "Penjades constants a l'Ubuntu"
date: 2008-01-02
forum: Catalan Team
---

### Post by lluisalguero on 2008-01-02
Hola amics,
començo a estar una mica desesperat amb el meu Ubuntu, se'm penja molt sovint, hi ha cops que només es queda "penjada" la pantalla, ja que puc moure el ratolí, i es torna a "despenjar" tot sol, però hi ha cops que es penja tot i només em queda el remei de reiniciar el portàtil "a lo bruto".

Pel que he anat veient, crec que o bé és del Firefox o bé del Thunderbird, que son les dos aplicacions que faig servir gairebé el 90% de les vegades.

També m'he adonat, que les "penjades" cada cop son més sovint, aquest matí (4 cops en 1 hora) i fins i tot s'ha reiniciat sol 1 cop.

Per si és d'ajuda les característiques del portàtil son:

- Intel Centrino Duo T5500 @ 1.66 GHz
- 1 Gb de RAM
- 120 Gb de HD
- 3 particions (XP, Ubuntu i Dades)

Hi ha algún programari que faci un testeig dels components del portàtil per veure si hi ha alguna cosa que està fallant?

Gràcies per la vostra ajuda

---

### Post by papapep on 2008-01-02
Inicialment jo miraria la RAM, ja que les penjades no són normals, però els reinicis espontanis ja són autènticament Plutonians....
Al menú d'arrencada del sistema, veuràs que la últiima opció és el Memtest que et farà totes les marranades possibles amb la RAM a fi de poder-la verificar.

---

### Post by lluisalguero on 2008-01-02
> **papapep said:**
> Inicialment jo miraria la RAM, ja que les penjades no són normals, però els reinicis espontanis ja són autènticament Plutonians....
Al menú d'arrencada del sistema, veuràs que la últiima opció és el Memtest que et farà totes les marranades possibles amb la RAM a fi de poder-la verificar.

Faré això que m'has dit, a veure si veig algún missatge. Gràcies

---

### Post by CarlesOriol on 2008-01-02
Quina gràfica tens?

---

### Post by lluisalguero on 2008-01-02
> **CarlesOriol said:**
> Quina gràfica tens?

Segons Sistema->Preferències->Informació de maquinari

tinc una GeForce Go 7600

He fet allò del memtest que m'heu dit i ha fet dos cops sencers els tests i no m'ha donat cap missatge d'error ni res

---

### Post by papapep on 2008-01-02
Una altra opció, que a mi m'ha passat algun cop, és treure la targeta gràfica, netejar ben bé contactes de la placa i l'slot on la poses i tornar-la a posar que quedi ferma.
Algun cop, pel que sigui, es movia i portava problemes.

---

### Post by lluisalguero on 2008-01-02
> **papapep said:**
> Una altra opció, que a mi m'ha passat algun cop, és treure la targeta gràfica, netejar ben bé contactes de la placa i l'slot on la poses i tornar-la a posar que quedi ferma.
Algun cop, pel que sigui, es movia i portava problemes.

És un portàtil....:biggrin:

---

### Post by papapep on 2008-01-02
És que se us ha de dir tot, eh!!, doncs fica'l a la rentadora! :-D

---

### Post by pespin on 2008-01-02
Uses tarjeta wifi? a mi se'm penjava el portàtil ma buna tarja wifi USB...

---

### Post by lluisalguero on 2008-01-02
> **pespin said:**
> Uses tarjeta wifi? a mi se'm penjava el portàtil ma buna tarja wifi USB...

La wifi està integrada..

---

### Post by CarlesOriol on 2008-01-02
Tens algun tipus de connexions de xarxa tipus samba o nfs permanents?

Uses els efectes compiz d'escriptori?

---

### Post by pespin on 2008-01-02
Has mirat als logs del sistema si hi ha quelcom extrany?

Sistema ->Administració-> Registre del sistema

---

### Post by lluisalguero on 2008-01-02
> **CarlesOriol said:**
> Tens algun tipus de connexions de xarxa tipus samba o nfs permanents?

Uses els efectes compiz d'escriptori?

Apart del portàtil, a la xarxa que tinc montada hi han 3 pc's mes, tots tres amb XP, i si de tant en tant miro alguna carpeta compartida. Suposo que deu ser això el que preguntaves.

Ara tinc desactivat el compiz  també

---

### Post by lluisalguero on 2008-01-02
> **pespin said:**
> Has mirat als logs del sistema si hi ha quelcom extrany?

Sistema ->Administració-> Registre del sistema

Ho acabo de mirar i veig que constantment es repeteixen aquestos missatges

Jan  2 00:00:59 lluis-laptop kernel: [  278.276000]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
Jan  2 00:01:04 lluis-laptop kernel: [  283.316000] ata2: port is slow to respond, please be patient (Status 0xd0)
Jan  2 00:01:09 lluis-laptop kernel: [  288.300000] ata2: device not ready (errno=-16), forcing hardreset
Jan  2 00:01:09 lluis-laptop kernel: [  288.300000] ata2: soft resetting port
Jan  2 00:01:10 lluis-laptop kernel: [  288.832000] ata2.01: configured for UDMA/33
Jan  2 00:01:10 lluis-laptop kernel: [  288.832000] ata2: EH complete
Jan  2 00:01:52 lluis-laptop kernel: [  330.932000] ata2.01: limiting speed to UDMA/25:PIO4
Jan  2 00:01:52 lluis-laptop kernel: [  330.932000]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)

---

### Post by jordilin on 2008-01-02
> **lluisalguero said:**
> Ho acabo de mirar i veig que constantment es repeteixen aquestos missatges

Jan  2 00:00:59 lluis-laptop kernel: [  278.276000]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
Jan  2 00:01:04 lluis-laptop kernel: [  283.316000] ata2: port is slow to respond, please be patient (Status 0xd0)
Jan  2 00:01:09 lluis-laptop kernel: [  288.300000] ata2: device not ready (errno=-16), forcing hardreset
Jan  2 00:01:09 lluis-laptop kernel: [  288.300000] ata2: soft resetting port
Jan  2 00:01:10 lluis-laptop kernel: [  288.832000] ata2.01: configured for UDMA/33
Jan  2 00:01:10 lluis-laptop kernel: [  288.832000] ata2: EH complete
Jan  2 00:01:52 lluis-laptop kernel: [  330.932000] ata2.01: limiting speed to UDMA/25:PIO4
Jan  2 00:01:52 lluis-laptop kernel: [  330.932000]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)

Aixo sona a falla del disc dur. Si et torna a passar, surt a consola virtual prenent control+Alt F1 entra i executa dmesg. 
Jo botaria amb un Live Cd i faria un fsck del disc dur per veure si hi ha algun problema. Perdoneu accents, estic amb teclat English.
salut ;)

---

### Post by CarlesOriol on 2008-01-03
+1 per jordilin

Disc dur o dispositiu ata "cascat".

Desconnecta tots els sistemes d'emmagatzenament que tinguis a més del disc dur principal. 
Comprova que no tinguis un CD amb errors.

---

### Post by lluisalguero on 2008-01-03
> **CarlesOriol said:**
> +1 per jordilin

Disc dur o dispositiu ata "cascat".

Desconnecta tots els sistemes d'emmagatzenament que tinguis a més del disc dur principal. 
Comprova que no tinguis un CD amb errors.

No hi ha cap disc dur/memory stick ni res semblant connectat, ni cap CD/DVD a la disquetera

---

### Post by jordilin on 2008-01-03
> **lluisalguero said:**
> No hi ha cap disc dur/memory stick ni res semblant connectat, ni cap CD/DVD a la disquetera
Si que en tens de disc dur. Tu mateix ho dius en el primer post 
> Per si és d'ajuda les característiques del portàtil son:

- Intel Centrino Duo T5500 @ 1.66 GHz
- 1 Gb de RAM
- 120 Gb de HD
- 3 particions (XP, Ubuntu i Dades)
Tens 120 Gb de disc dur. Bota amb un livecd i executa fsck (si tens algun dubte fes man fsck, fas un google o ens preguntes), comana que et dira si el teu disc dur esta en plena forma o esta definitivament mort. Fa anys vaig tenir el mateix problema i el Linux s'em quedava clavat degut a falles de disc dur. Tambe pots entrar amb el XP i baixarte alguna utilitat que et faci un test del disc dur. Hi han fabricants que ho proveeixen.
Que tinguis sort.

---

### Post by lluisalguero on 2008-01-03
> **jordilin said:**
> **Si que en tens de disc dur. Tu mateix ho dius en el primer post **

Tens 120 Gb de disc dur. Bota amb un livecd i executa fsck (si tens algun dubte fes man fsck, fas un google o ens preguntes), comana que et dira si el teu disc dur esta en plena forma o esta definitivament mort. Fa anys vaig tenir el mateix problema i el Linux s'em quedava clavat degut a falles de disc dur. Tambe pots entrar amb el XP i baixarte alguna utilitat que et faci un test del disc dur. Hi han fabricants que ho proveeixen.
Que tinguis sort.

Em referia a cap** disc dur extern** :lolflag:

Provaré això que m'has dit...quan tingui un moment...

---

### Post by CarlesOriol on 2008-01-03
Doncs si sols hi ha un disc... molt em temo que com diu en jordilin està en mal estat.

---

### Post by Miquel Ubuntero on 2008-01-06
Hola.
tot i superar el mem test, com vas comentar, jo provaria de treure i posar de nou la memòria ram. Et puc dir per experiència que ho he fet moltes vegades amb bon resultat. Important! sempre que manipulis algún component o circuit, primer has de descarregar el teu cos de estàtica. Pots fer-ho tocant una aixeta o tocant el terra amb les mans, i no ho dic de coña.
Per verificar si el teu sistema operatiu està defectuós, també pots provar el pc fen correr una live-sesion amb el cd d'Ubuntu, a veure si també es penja o no.
Amb paciència i amb proves tot es soluciona.
Molta sort.

---

