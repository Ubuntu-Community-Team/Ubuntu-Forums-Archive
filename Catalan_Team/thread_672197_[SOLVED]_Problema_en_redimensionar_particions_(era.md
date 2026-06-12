---
title: "[SOLVED] Problema en redimensionar particions (era:Problema GRUB )"
date: 2008-01-19
forum: Catalan Team
---

### Post by Joan Marc on 2008-01-19
Hola,
En primer lloc no sé si és el lloc indicat o no, però no tinc gaires més sortides per solucionar el problema...
Bé, vaig començar a treure la meva versió d'ubuntu de 64bits, per la catalanitzada de 32.
El cas és que me'n vaig anar des de la sessió Live del CD de 32bits al Partition Editor i vaig eliminar la partició on anteriorment hi havia la de 64bits (no sé si això és una animalada:(). Després, vaig intentar redimensionar la partició on tinc el Windows XP Prof. per poder fer la de l'ubuntu més gran. A mig fer, vaig recordar que no tenia cap copia de seguretat de l'XP, i vaig cancel·lar l'instal·lació.
Vaig reiniciar (traient el Live CD i pitjant enter), i al moment d'arrencar, després de que sortís la casa ASUS amb la musica habitual, em va sortir la pantalla tota negra i unes lletres blanques que deien:
GRUB Loading stage1.5.

GRUB Loading, please wait...
Error 22

I l'ordinador es queda aquí.
He tornat a posar el LIVE CD i es carrega amb normalitat, això m'ha tranquil·litzat una mica.
No sé que he de fer i reconec que estic força espantat...
Algú em pot ajudar?

Gràcies.

PD: Perdoneu la parrafada

---

### Post by patrickfromspain on 2008-01-19
des d'un cd d'insta&#320;lacio de win xp, ves a la consola de recuperació i alla posa fixmbr. No et puc donar més detalls perque ja fa temps que ho vaig fa temps.

Per un altre cop, NO cal borrar cap particio, simplement li dius, desde l'insta&#320;lador, de formatejar la particio on tenies el de 64bits i ho insta&#320;les alla. No cal borrar i crear particio.

Despres, aclareix un dubte que tinc: que es el que vas parar a la meitat? El redimensionar la partició o la insta&#320;lacio d'ubuntu?? Si el que vas cance&#320;lar es el redimensionament: MAL FET. Pots haver perdut totes les dades. M'inclino mes aviat a que vas cance&#320;lar la insta&#320;lacio d'ubuntu, també mal fet: la insta&#320;lacio d'ubuntu no es un proces critic, el que es critic es redimensionar una particio sense fer copia de seguretat.

Salut!

---

### Post by Joan Marc on 2008-01-19
Sí, vaig cancel·lar l'instal·lació de l'ubuntu, però en el moment en que surten les particions, i les pots eliminar, redimensionar, o bé selecciones la que vols instal·lar l'ubuntu. Però el cas es que no vaig arrivar a redimensionar-la, ho vaig cancel·lar quan estava canviant el volum, sense prémer d'acord ni acceptar ni res.

Ara mateix provo el que m'has dit

Moltes gràcies!

---

### Post by Joan Marc on 2008-01-19
He provat el que m'has dit, però tinc algun dubte:
Després de que es carregues el CD, m'han sortit tres opcions:
1. Pitjar Enter per instal·lar.
2. Recuperar una instal·lació de Windows fent servir la consola de recuperació pitjant R.
3. Pitjar F3 per sortir.

He pitjat la segona i m'ha sortit l'imatge que adjunto.

El problema és que no sé quan he de posar fixmbr.

Gràcies.

---

### Post by patrickfromspain on 2008-01-19
**LLEGIR** es la clau!

Posa 1,i despres ja et sortira un ms-dos.


Salut!

---

### Post by Joan Marc on 2008-01-19
Al posar 1, em demana una contrasenya d'administrador. Ho trobo raríssim perquè quan el vaig instal·lar vaig deixar el camp de la contrasenya en blanc (així cada vegada que començaba la sessió, no havia de posar la contrasenya).

No hi deu haver pas una contrasenya per defecte? Esque sinó no sé que posar-hi!!

Gràcies.

---

### Post by patrickfromspain on 2008-01-19
has probat a no posar res?

---

### Post by Joan Marc on 2008-01-19
Si, em diu que la contrasenya no és correcta.

---

### Post by patrickfromspain on 2008-01-19
Tens algun usuari amb privilegis d'admin i contrasenya? Proba-la

No? Busca al google una possible solució?

Encara res? Insta&#320;la l'ubuntu sense fer la particio mes gran i tindras un grub i arrancara.

Salut!

PD: windows... puej

---

### Post by Joan Marc on 2008-01-19
He mirat pel google i un parell de solucions que he trobat s'han de fer des del Windows, però jo no hi puc entrar xD.

Si intal·lo l'ubuntu tornarà a sortir la pantalla per seleccionar el SO? Si es així cap problema :)

Gràcies!

PD: Una pregunta, es pot fer una copia de seguretat del Windows desde l'Ubuntu?

---

### Post by kukat on 2008-01-19
El que pots fer (si es un ordinador d'ús personal) es quan instal.les l'ubuntu, copiar les dades de Windows més importants. Ubuntu pot llegir perfectament les particions NTFS de Windows, així que... Cap Problema!! 

Salutacions!

---

### Post by Joan Marc on 2008-01-19
Es igual, deixaré la partició del findestres tal i com està i instal·laré l'ubuntu a l'espai que queda.

Gràcies!! :)

---

### Post by cortsenc on 2008-01-20
[Llista d'errors del Grub]("http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors")

Per tant, dedueixo que si restaures la instal·lació d'Ubuntu, tot tornarà a estar com abans.

---

### Post by Joan Marc on 2008-01-20
Teniu raó, he instal·lat la versió de 32 bits (ja feia temps que ho volia fer) i tot torna a la normalitat :D

Gràcies a tots!

PD: El meu pare no se n'ha ni adonat ;)!

---

