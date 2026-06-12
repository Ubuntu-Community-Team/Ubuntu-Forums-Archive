---
title: "Problema al intentar instal·lar ubuntu."
date: 2007-12-03
forum: Catalan Team
---

### Post by lo gambusí on 2007-12-03
Salut!

Estic intentant instal"·lar ubuntu a una amiga. És un ordinador on originalment hi havia windows vista, després va haver-hi xp i ara volem posar-hi ubuntu. 

Posem lo CD al lector en la sessió windows, lo llig i després reiniciem l'ordinador. Mos surt lo menú principal. F2, català. Li donem a instal·lar. Llavors apareix la barra taronja de carregar-se i de repent se queda penjat a este punt. Alguna idea de per què pot ser això?

EDITO: per si pot ser útil, és un Core 2 duo amb una targeta gràfica ATI.

Gràcies!

---

### Post by jodufi on 2007-12-03
A mi em passava el mateix. 
En aquest fòrum hi ha varis fils que expliquen com resoldre aquest problema. Bàsicament diuen d'engegar utilitzant el driver VESA o utilitzar el CD alternate.
Jo ho he aconseguit triant la resolució a la primera pantalla (no recordo si era F4 o F5).

---

### Post by lo gambusí on 2007-12-03
He provat lo de canviar la resolució i res: un cop carregada la barra taronja de l'inici de l'ubuntu se'm posa una pantalla negra amb lletres, rotllo MS-DOS, i on posa ubuntu@ubuntu-laptop i me dixa escriure.

Ara estic descarregant l'ubuntu alternate a vore què. ;)

---

### Post by CarlesOriol on 2007-12-06
Cerca pels fils del fòrum. Ja he explicat un parell de cops com fer una insta&#320;lació en aquests  casos. Tot i que et recomano calma per que no serà senzill.

---

### Post by lo gambusí on 2007-12-09
He instal·lat l'ubuntu alternate este, i en principi no hi ha hagut problema. A l'hora d'iniciar-lo, però, la primera vegada se m'ha quedat trabat a la barra de càrrega, on diu ubuntu amb la barra taronja. He apagat l'ordinador, i he reiniciat. La segona vegada m'ha passat la barra taronja, però se m'ha quedat amb la pantalla negra, rotllo consola, carregant-se, dient allò de "process X.... [OK]" i així.

i d'aquí no el trac. 

algú sap què pot passar? :(

---

### Post by papapep on 2007-12-09
Gambusí, ens demanes un autèntic exercici d'adivinació...

Si no ens poses les últimes línies que mostra abans del moment que esmentes no podem saber en quin punt estàs.

---

### Post by lo gambusí on 2007-12-10
Pantalla negra i este text:

> * Starting anac(h)ronistic cron anacron
* Starting deferred execution scheduler atd
* Starting periodic command scheduler crond
* Checking battery state...
* Running local boot scripts (/etc/rc.local)

I aquí se queda fregit i no puc fer res, excepte apagar l'ordinador a lo bèstia.

---

### Post by papapep on 2007-12-10
Prova passant-li el paràmetre:

```
acpi=off
```

al kernel al moment de l'arrancada.

---

### Post by lo gambusí on 2007-12-10
I com ho faig, això? 

Li he donat a esc quan es carregava i m'ha sortit el menú que (crec) és el kernel. Llavors li dono a la lletra *c* per editar, escric això de acpi=off i me diu "Error 27: Unrecognized command". Llavors li dono a *e*, per a "edit the commands before booting" i me surt lo següent:
> root (hf0,0)
kernel /boot/vnlinuz-2.6.22-14-generic root=VVID=22f877af-3329-47b9-->
initrd /boot/initrd.img-2.6.22-14-generic
quieti també me diu si vull donar-li a "*b* to boot, *e* to edit the selected command in the boot sequence, *c* for a command line, *d* to remove the selected line"

---

### Post by lluisanunez on 2007-12-11
```
root (hf0,0)
kernel /boot/vnlinuz-2.6.22-14-generic root=VVID=22f877af-3329-47b9-->
initrd /boot/initrd.img-2.6.22-14-generic
quiet
```
Això és la comanda que carrega el kernel. Amb el cursor, baixa fins a la darrera línia (quiet), pica "e" per editar-la, i al final, després de "quiet" afegeix "acpi=off"

---

### Post by lo gambusí on 2007-12-11
ho faig així, però no se'm guarda. m'explico:

edito i li dono a enter, i me torna al menú anterior en > root (hf0,0)
kernel /boot/vnlinuz-2.6.22-14-generic root=VVID=22f877af-3329-47b9-->
initrd /boot/initrd.img-2.6.22-14-generic
quiet acpi=offfins aquí bé, sembla. però lo problema és que si li dono a esc per tirar enrere no se'm guarda la nova línia. i si li dono a b per a iniciar lo sistema, se'm queda penjat igualment i al reiniciar no me surt la nova línia. :(

---

### Post by patrickfromspain on 2007-12-11
quan ho poses darrere quiet i apretes be el kernel es carrega amb aquest parametre. Es normal que no es guardi. De totes formes.. haurem de seguir probar, perque es penja igualment. prova posant-hi irqpoll o no noapic o les 2 a la vegada.

salut

---

### Post by lo gambusí on 2007-12-11
Res, no funciona ni un ni l'altre :(

No ho he comentat abans, però just abans d'aparèixer la barra de càrrega de l'ubuntu em surt un missatge: > Starting up...MP BIOS bug 8254: timer not connected to BIOS-APIC (més o menys, potser m'equivoque en alguna xifra o així). Pot tenir alguna cosa a veure?

És una llàstima, perquè porto mesos convencent la companya per a que se passe a Ubuntu i ara que ho fem mos surt en lo drama este. Sort que s'ho ha pres com una cosa personal i ara l'únic que vol és passar-se per a fotre al Bill Gates xD

---

### Post by papapep on 2007-12-11
Posa-li **noapic** a l'arrencada del kernel. Atenció: cal posar-ho [COLOR="Red"]abans[/COLOR] dels dos guions --.
També seria bo anar a la bios i mirar si hi ha una opció que es diu IOAPIC i inhabilitar-la.

---

### Post by lo gambusí on 2007-12-11
Perdona la meua ignorància, però no trobo on he de posar això de noapic. L'arrencada del kernel seria on diu > root (hd0,0)? No veig pas los dos guions.

Com puc entrar a la bios? Amb allò d'ESC quan es carrega l'ordinador?

---

### Post by Joan Marc on 2007-12-12
La majoria d'ordinadors s'hi entra pitjant F2 o alguns Suprimir (Delete) avans de que es carregui l'ubuntu o el finestres.

Salut!

---

### Post by lo gambusí on 2007-12-12
I un cop allí on hauria de posar això de "noapic"?

---

### Post by papapep on 2007-12-12
No, a la bios has de buscar la opció **IOAPIC** i deshabilitar-la, si és que hi és.
Respecte on és, doncs cal que busquis, cada bios és una mica diferent.

---

### Post by lo gambusí on 2007-12-12
He estat buscant la opció i no la trobo, i mira que he regirat tota la BIOS tres vegades... :( Pot ser que no hi sigue? Alguna alternativa?

---

### Post by papapep on 2007-12-13
Clar que pot ser que no hi sigui. Aleshores, prova primer si et funciona passant la opció a l'arrencada i, si funciona, ja ho posarem on toca per que et quedi definitiu.

---

### Post by lo gambusí on 2007-12-14
I com faig això de passar-la a l'arrencada? xD

---

### Post by lo gambusí on 2007-12-17
hola?

---

### Post by papapep on 2007-12-17
Quina versió concreta de CD estàs fent servir per a instal·lar? 7.10 Desktop o Alternate?

---

### Post by lo gambusí on 2007-12-18
alternate.

---

### Post by papapep on 2007-12-18
En aquests moments només tinc a mà una iso de la versió server, però crec que no han de diferir molt al moment de l'arrencada.

Quan et surt la pantalla que adjunto, prems F6 i afegeixes el paràmetre a la línia que et surt a sota, abans dels dos guions.

---

### Post by lo gambusí on 2007-12-21
Res, ho he fet tal com heu dit i seguix quedant-se'm penjat.... :(

---

### Post by lo gambusí on 2007-12-22
:(

---

