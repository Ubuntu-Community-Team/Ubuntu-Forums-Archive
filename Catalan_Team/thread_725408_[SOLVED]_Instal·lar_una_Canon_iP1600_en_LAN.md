---
title: "[SOLVED] Instal·lar una Canon iP1600 en LAN"
date: 2008-03-15
forum: Catalan Team
---

### Post by Frealof on 2008-03-15
Hola a tothom!

Avui m'he decidit a provar d'instal·lar la impressora que tinc en xarxa amb un PC amb windows. 

Fa un temps la tenia connectada directament al PC (via USB) que utilitzo ara mateix (té Gutsy instal·lat) i m'anava perfectament.

El cas es que avui he tornat a agafar els "apunts" que ja tenia. 

Aquests són a grans trets els passos que he seguit:

1. Descarregar el controlador
2. Descomprimir el paquet
3. "Transformar" els paquets desitjats (els que recomanaven els qui en saben més que jo) a .deb utilitzant alien
4. Instal·lar els paquets .deb
5.Tancar terminal, i obrir al Firefox la plana [http://localhost:631](http://localhost:631) per poder accedir a l'assistent per configurar impressores de CUPS.
6.Anar seguint els passos, buscant la impressora al grup de treball de whindows; Sel·leccionant el controlador de la iP2200 (com es recomana per tot arreu), etc.

L'he trobat, i si bé sembla que la impressora esta detectada i instal·lada, com mostro a la captura de pantalla... no funciona :( no em permet ni imprimir una plana de prova... La tinc engegada i amb compartida (si més no es el que diu el windows)

Alguna idea de què pot estar fallant?

Gràcies per endavant!

[ATTACH]62695[/ATTACH]

---

### Post by Frealof on 2008-04-08
Hola de nou... 

Avui m'hi he tornat a posar,m'hi he passat bona part del matí i nanai de la xina... no me'n surto. L'he desinstal·lat del CUPS i he provat de fer-ho via gnome.

Sistema>administració>impressió

La busco a Windows Printer Via Samba.
La busco al grup de treball, PC i endavant.
Poso la casa de l'impresora (Canon) i el controlador que m'he descarregat (Canon iP2200 Ver.2.60).

Tiro endavant i em demana la contrasenya per a guillem a localhost.

Poso la contrasenya d'usuari i després de pensar una estoneta i apareixer "S'esta afegint la impressora"... aquí em quedo, me la va demanat tota l'estona, he provat les diverses contrasenyes que tinc (no fos cas que en fes servir una altra...) amb un èxit nul. :(

Hi ha alguna manera de poder saber quina contrasenya es? Queden registrades a algun lloc? Més que res perquè em sembla que es l'única cosa que em falta per poder fer servir la impressora.
 
Al cap d'una estona se m'ha acudit de provar-ho des del CUPS posant la direcció que em sortia amb el gnome a l'apartat de samba... smb://... i res, tampoc funciona.

Abans quan la tenia endollada directament via USB anava tot bé, però ara per raons d'espai no la hi puc tenir. A algú se li acud res?

Salut!

---

### Post by Frealof on 2008-04-08
He decidit començar de cap i de nou desinstal·lant la impressora del PC amb el Güindous i tornant a iniciar tot el procés des de zero entre el "panel de control" i l'aplicació del Gnome.

Aquesta vegada tot ha anat com una seda, la impressora funciona des d'ambdós ordinadors, i amb tots els usuaris que corren per casa ;)

Salut!

---

### Post by papapep on 2008-04-08
Enhorabona! :-)

---

