---
title: "Ubuntu Pendrive Persistent"
date: 2008-04-18
forum: Catalan Team
---

### Post by MorlanXaos on 2008-04-18
Hola tots,

Porto uns dies intentant instalar l'Ubuntu en un Pendrive.
Despres de rebuscar molt per la web, vaig trobar unes instruccions molt clares a la pagina:

[http://www.pendrivelinux.com/2007/09/21/usb-ubuntu-704-persistent-install-for-linux-users/]("http://www.pendrivelinux.com/2007/09/21/usb-ubuntu-704-persistent-install-for-linux-users/")

Es tracta de crear dues partcions al pendrive, una amb l'Ubunto i l'altre amb el casper r-w.
Fins aqui tot be.

L'unic problema es que al arrancar l'odinador amb el pendrive amb l'Ubuntu modo persistent, la particio del casper rw no es monta i per tant no soc capaç de guardar-hi documents. He repetit el proces varies vegades pensant que feia alguna cosa malament, pero sempre obtinc el mateix resultat.

Finalment, he instal.lat l'Ubunto des de el CD al pendrive (desconectant tots els disc durs, perque el grub s'instal.li al pendrive) D'aquesta manera si que funciona, pero sols en aquest ordinador. He probat amb altres 3 ordinadors que poden arrancar amb USB, i en ningún d'ells arranca correctament. Un es queda clavat en una pantalla negra. Amb l'altre surt un missatge d'error que diu que not pot continuar carregant degut a error de microcode, etc. Tots aquest altres ordinadors si que arranquen correctament amb el Live CD, pero no amb el pendrive. 

Per tant, crec que al fer el muntatje al pendrive des de un ordinador determinat, nomes es deuen instal.lar els archius necesaris perque funcioni en aquell ordinador, potser?, hi ha alguna posibilitat de que a la instal.lacio es carreguin TOTS el archius del CD al pendrive?

Estoc provant-ho amb Ubuntu 7.10 i un pendrive de 4GB
:confused:
Xavier
Un aprenent de Ubuntu

---

### Post by crazyserver on 2008-04-18
Bones! Jo vaig serguri aquestes instruccions i em van funcionar genial:
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
EL problema que tens amb l'arranc a tots els pc's...
A mi em funcionava a casa i a la universitat no, per tant vaig fixar-me en la distro Slax i vaig personalitzar un script.
A la wiki diu que per fer-ho bootable cal fer:
```
syslinux -s /dev/sdX1
```Però si vols que funcioni a tot arreu, cal instal·lar lilo al Boot del pendrive:
Cal copiar tots els arxius de la carpeta syslinux a l'arrel del pendrive. (ara no recordo si això era necessari)
Descomprimir el tar adjunt al pendrive  i executar el bootinst,sh

VIGILA MOLT (és un xic perillòs tot i que a mi no m'ha passat mai res).
L'script et detecta des d'on ho executes i instal·la el lilo en el dispositiu (demana primer confirmació, comprova que estigui tot bé!)
TORNA A VIGILAR: si ho executes des del teu disc dur... malament! Comprova que els fitxers estiguin a la carpeta boot del pendrive i executa-ho des d'allà!

Per si no queda suficientment clar, jo al meu pinxo tinc els següents arxius:
```
boot/
boot/lilo
boot/bootinst.sh
boot/mbr.bin
boot/syslinux
casper/
casper/vmlinuz
casper/initrd.gz
casper/filesystem.squashfs
casper/filesystem.manifest-desktop
casper/filesystem.manifest
preseed/
preseed/cli.seed
preseed/ubuntu.seed
syslinux.cfg
splash.rle
splash.pcx
README.diskdefines
ldlinux.sys
langlist
it.tr
isolinux.txt
isolinux.bin
es.tr
es.hlp
en.tr
en.hlp
ca.tr
bootlogo
boot.cat
16x16.fnt
.disk/
.disk/casper-uuid-generic
.disk/info
.disk/release_notes_url
```que són els estrictament necessaris per bootar amb la meva configuració (he tret idiomes i arxius inútils)

Espero que et sigui útil. Pots mirar-te com està fet l'SLAX per tenir-ho més clar;)

Si necessites algun detall de com es fa qualsevol cosa només cal que ho demanis!

---

### Post by crazyserver on 2008-04-18
He trobat una mica de documentació de quan ho vam fer a la uni:

Al directori arrel del pendrive copiarem el cd, hi ha molts arxius inservibles que esborrarem i altres que hem de canviar de lloc:
 - Els directoris útils són: casper, presseed, .disk i isolinux (aquest últim l'acabarem esborrant)
 - De la carpeta arrel només mantindrem l'arxius README.diskdefines, la resta l'esborrem.
- Ara movem els segúents arxius de la carpeta isolinux a l'arrel (la resta juntament amb el directori ho podem esborrar):
16x16.fnt, boot.cat, bootlogo, XX.tr, XX.hlp (on XX es el codi d'idioma que volem conservar [nosaltres hem conservat ca, en, es i it]) isolinux.bin, isolinux.txt, langlist (on, al seu interior només deixarem els codis dels idiomes copiats), ldlinux.sys, splash.pcx, splash.rle y isolinux.cfg (aquest últim cal reanomenar-lo a syslinux.cfg)
 - A més hem reusat la carpeta boot d'SLAX per poder arrencar amb LILO (per pc's on no funcioni syslinux. En aquesta només hem conservat els arxius: lilo bootinst.sh mbr.bin i syslinux) bootinst.sh l'hem personalitzat.

---

### Post by MorlanXaos on 2008-04-18
Moltes Gracies Crazy,

Donare un cop d'ull a les instruccions de la pagina que has possat, i si no m'ensurto probare amb el Slax.
:)
Xavi

---

### Post by MorlanXaos on 2008-04-19
Be, al final i despres de fer moltes proves, m'he decidit a instal.lar l'Ubuntu una altre vegada. Com que on el fare servir es al portatil de la feina, doncs he fet l'istal.lacio des de el CD Live al pendrive (previament he desconnectat el disc dur)

Ha anat de conya, l'Ubuntu practicament ha reconegut tot a la primera, el wifi, el bluetooth, la red, la grafica....(excepte la tageta de so, encara que no es un problema ja que tinc els drivers i cuan tingui un moment acabare de instal.larlos)

El portatil es un Dell Latitude D630
:)

Crazy, el Slax no m'acaba de fer el pes, ja que preferixo el GNOME, el KDE em recorda el Windows...

---

### Post by papapep on 2008-04-19
> el Slax no m'acaba de fer el pes, ja que preferixo el GNOME, el KDE em recorda el Windows... 

Doncs pots provar [Wolvix]("http://wolvix.org/node/614"), que té gnome com a una de les opcions, si no ho tinc mal entès.

---

### Post by crazyserver on 2008-04-20
Sabia que no et faria el pes..XD A mi tampoc mel fa... KDE i massa poc suport de paquets! Però el tema de l'SLAX te'l deia pq miressis com s'instal·la en un pendrive i així tenir una idea de com instal·lar l'ubuntu al pendrive!
Salut!

---

