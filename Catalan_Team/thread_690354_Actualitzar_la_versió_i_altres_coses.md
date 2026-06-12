---
title: "Actualitzar la versió i altres coses"
date: 2008-02-07
forum: Catalan Team
---

### Post by almogabber on 2008-02-07
Hola nois i noies!!

Primer post per aquí, després de la presentació, i us volia preguntar algunes cosetes. Sé que no és la manera: un post per cada problema, però tampoc volia inundar el foro a la primera.

Abans que res, estic veient que això amb l'ubuntu ha estat un amor a 'primera' vista. Havia provat i usat el suse, però d'això ja fa molt (massa) temps. I l'últim intent va ser la Catix, que tenia molt bona pinta però mai va voler ser amiga del meu pc i no va passar de LiveCD.

Alguna cosa semblant em va passar amb l'Ubuntu. Primer vaig instal·lar-lo en un portàtil mitjatnçant Wubi (no em treguis el windows! sentia de fons.. jejeje); i bé, em va fer tant bona pinta que vaig netejar de cap i de nou el pc per posar-hi la GutsyGibbon, però oh! sorpresa: tant el LiveCD com amb la instal·lació se'm quedaven penjades al principi on posava ' (initramfs) ', i em donava unes comandes opcionals.. però no vaig passar d'aquí.
En fi, vaig tirar a provar la DrapperDrake, i de conya. Com la seda. Suposo que devia ser problema de hardware. Com que anava sense SO (havia formatejat a saco, com he dit), no m'ho vaig mirar massa més perquè havia petat la 7.10.

Amb la 6.06 m'he anat apanyant: conexió a internet, impresora, codecs de musica i videos, HD estern, gravadora externa, mldonkey, xarxa wifi i compartir carpetes (i la impresora).. li vaig pillant també (o això crec) el truquillo al sinaptic (que em sembla una idea marevellosa per gestionar les aplicacions, com és possible que aquesta manera d'adquirir aplicacions i complements no sigui l'estàndar per tots els SO???!! win.. #-o. Ah, i el terminal, cuant de temps des de l'MS-DOS!!, entre alguns manuals i demés foros també li vaig pillant el truc, tot i el que em costa! :D

Bé, m'enrollo que dona gust.. ho sento..

Al que anava: una altra de les coses que em van deixar els ulls com plats va ser la de actualitzar la versió sense haver ni tant sols de reiniciar! (o si havia de reiniciar al final..?) Tot i llegir algun comentari de que podia ser 'perillós' o no del tot recomanable, vaig actualitzar per posar-me de cap i de nou a la EdgyEft, que és sobre la que escric ara. Jo no he notat que res vagi malament o hagi deixat de funcionar: de hardware (periferics i xarxes) tot va igual de bé, els programes també.. l'únic que m'ha petat algun cop ha estat el firefox, però avans també petava, i de vegades se m'en va la mà amb les pestanyes.. i tot i ajuda. Que tampoc em molesta, vaja.

Però volia saber: què en penseu sobre actualitzar la versió d'aquesta manera, sense reinstalar res? Hi ha alguna manera de revisar el sistema en busca d'errors que es puguin haver creat (o els hagi pogut provocar jo, és clar!!) Com cuan comproves els erros que hi ha a una web, que tot i ser-hi no fan que res vagi malament, però que hi són. M'explico? :)

I l'altre questió, només dos, va.. a l'iniciar, amb el GRUB, m'apareixen 8 opcions!!! 
a la part superior n'hi han 6: tres son iguals, i els altres tres són les seves respectives 'opcions a prova d'errors', diguem-ne. Per tant, en el fons només n'és una i la seva prova d'errors; però per triplicat.
A la part de sota, que és on posa 'altres sistemes' hi ha el windows (el vaig tornar a posar, necessito el photoshop nois.. jejeje) i un altre ubuntu.
Sé que hauria d'haver posat bé el nom, versió i tal, tot el que apareixi; ara no puc reiniciar, després o copio o li faig una foto (juas que freak!) aviam si sabeu a què pot ser degut i com se soluciona (el fitxer del GRUB es pot editar oi??)

Tot això ha vingut perquè ahir, o abans d'ahir, em va saltar el missatge de que tenia actualitzacions disponibles, entre elles, o la primera, la de 'linux-image-2.6.17-12-386', i també la de la versió, per passar a la FeitsyFawn, què faig, m'hi passo?? :D

Gràcies per tot!!!

Independència i lluita, i ara: també ubuntu!! jeje ;)

---

### Post by papapep on 2008-02-07
Si que t'enrotlles, si!!! :-D (cap problema)

Resposta a pregunta 1: Al meu portàtil no instal·lo a pèl des de Dapper (per tant ha passat per Dapper, Edgy, Feisty i Gutsy) sense cap mena de problema. De fet, aquesta ha de ser la manera "normal". Això de reinstal·lar cada cop és una cultura heredada "'d'altres mons" ;-)

Resposta a pregunta 2: Edites el fitxer /boot/grub/menu.lst (primer fes-ne una còpia de seguretat!!!) i comentes (fiques # davant) al que no vulguis que et surti a la pantalla d'arrencada.

Teòrico-pràctic:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu_backup.lst
sudo nano /boot/grub/menu.lst

```

Ostres !!!! Acabo de veure que aquest és el meu missatge número 1000 :-D

---

### Post by almogabber on 2008-02-07
Ei, merci per la rapidesa. No sé perquè però intuia que contestaries tu el primer, després de repassar un xic el foro. jejeje Em costa horrors començar a escriure, però a la que m'hi poso...

ok, ja he localitzat el fitxer que dius, copio el que hi ha:

title		Ubuntu, kernel 2.6.17-12-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-12-386 root=UUID=6c493899-9a22-4133-a2e3-e76cd980c861 ro quiet splash
initrd		/boot/initrd.img-2.6.17-12-386
savedefault
boot

title		Ubuntu, kernel 2.6.17-12-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-12-386 root=UUID=6c493899-9a22-4133-a2e3-e76cd980c861 ro single
initrd		/boot/initrd.img-2.6.17-12-386
boot

title		Ubuntu, kernel 2.6.15-51-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-51-386 root=UUID=6c493899-9a22-4133-a2e3-e76cd980c861 ro quiet splash
initrd		/boot/initrd.img-2.6.15-51-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-51-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-51-386 root=UUID=6c493899-9a22-4133-a2e3-e76cd980c861 ro single
initrd		/boot/initrd.img-2.6.15-51-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=6c493899-9a22-4133-a2e3-e76cd980c861 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=6c493899-9a22-4133-a2e3-e76cd980c861 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
boot


Jo sempre entro pel primer, però, potser que actualitzi abans i llavors l'editi, no fos cas que m'aparegués un altre kernel, no?

edit: per molts anys doncs!! jejeje

---

### Post by papapep on 2008-02-07
Bé, jo el que faria realment és actualitzar fins arribar a Gutsy (si estiguessis a Dapper no t'ho diria, però ara que ja has deixat la LTS no té massa sentit quedar-te a Edgy). Això, evidentment, provocaria un munt de actualitzacions de kernel que després hauries de "netejar".

Tu mateix però, tampoc tens cap obligació a actualitzar. Ara si, tingues present que si algun dia vols passar, diguem-ne, a Gutsy o Hardy només tens dues opcions: o passar per totes les actualitzacions intermitges o començar de cero reinstal·lant.

---

### Post by SiscoGarcia on 2008-02-07
[Off-Topic] [COLOR="Lime"]papapep[/COLOR], suposo que se t'ha de felicitar o semblant oi?
> 
Ostres !!!! Acabo de veure que aquest és el meu missatge número 1000 :)

Endavant!  ;)

---

### Post by almogabber on 2008-02-07
És clar, en el fons ja ho tenia clar que, ja que hi soc, millor posar-me al dia que no quedar-me en abans d'ahir!

Però abans de llançar-m'hi,  sobre el que dius de:> Això, evidentment, provocaria un munt de actualitzacions de kernel que després hauries de "netejar".

Vols dir que hauria d'arreglar jo alguns problemes que podrien aparèixer?? :confused: Perquè això de que les actualitzacions provoquin més problemes que els que reparen em sona de llarg... ;)

Espero resposta i actualitzo.

Merci!!!!

---

### Post by papapep on 2008-02-07
> Vols dir que hauria d'arreglar jo alguns problemes que podrien aparèixer??  Perquè això de que les actualitzacions provoquin més problemes que els que reparen em sona de llarg... 

No, volia dir que hauràs de treure o comentar més línies del fitxer /root/grub/menu.lst.

Això no vol dir que no et trobis amb cap problema actualitzant, normalment no passa però no és impossible. Tot i això, normalment, actualitzant s'obtenen més beneficis que problemes.

---

### Post by almogabber on 2008-02-07
Gràcies per l'aclaració. A l'atac, doncs!!! :D

---

