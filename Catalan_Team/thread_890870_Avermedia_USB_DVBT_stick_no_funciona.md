---
title: "Avermedia USB DVBT stick no funciona"
date: 2008-08-14
forum: Catalan Team
---

### Post by motor25 on 2008-08-14
**Nota de moderador:** Aquest fil és la continuació d'aquest altre: [http://ubuntuforums.org/showthread.php?t=888476](http://ubuntuforums.org/showthread.php?t=888476)

en el meTV em diu que no detecta la targeta 
No tuner device
algu em pot ajudor i en el mythtv no se em diu algo de configurar una cosa rara
algu em pot ajudar 
gracies

---

### Post by CarlesOriol on 2008-08-14
Crec que hauras de compilar el v4l.

Fes les proves despres amb el me-tv, ja jugaras amb el myth quan tot funcioni.

Descarrega el v4l.
**hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)**

Compila'l
[B]cd v4l-dvb
make[/B]

Insta&#320;la'l
**sudo make install**

És possible que necessitis alguns programes per fer els passos anteriors: *build-essential, mercurial*
fes
**sudo apt-get install build-essential mercurial**
per insta&#320;lar-los.

(referències: [http://linuxtv.org/repo/](http://linuxtv.org/repo/) )

---

### Post by motor25 on 2008-08-15
quin n'hi a molts i un que he donat s'ha m'ha ober una altre pagina hi havia un codi 
com ho haig de fer per compilar
gracies

---

### Post by motor25 on 2008-08-15
es com si no em detectes la targeta usb pero fent lsusb
em surt aixo
aleix@aleix-desktop:~$ lsusb
Bus 005 Device 006: ID 14aa:0160 AVerMedia (again) or C&E 
Bus 005 Device 005: ID 0ace:1215 ZyDAS WLA-54L WiFi
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 045e:00ce Microsoft Corp. Generic PPC Flash device
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0c45:608f Microdia 
Bus 001 Device 001: ID 0000:0000

---

### Post by CarlesOriol on 2008-08-15
Segueix les intruccions del meu post anterior.
El que està en negreta son comandes que has d'escriure al terminal.

---

### Post by papapep on 2008-08-15
Abans que res, quina versió d'Ubuntu tens instal·lat? enganxa'ns el que et mostri l'ordre:

```
cat /proc/version
```

---

### Post by CarlesOriol on 2008-08-16
Fes també el següent en terminal:

(desconnectes el dvb)
[B]sudo dmesg -c
clear[/B]
(connectes)
**dmesg**

i en copies la resposta d'aquesta darrera comanda.

---

### Post by motor25 on 2008-08-16
ho intentare

---

### Post by motor25 on 2008-08-17
Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 23:41:49 UTC 2008

---

### Post by motor25 on 2008-08-17
```
[  302.586544] FAT: Directory bread(block 526) failed
[  302.586562] FAT: Directory bread(block 527) failed
[  302.586573] FAT: Directory bread(block 528) failed
[  302.586585] FAT: Directory bread(block 529) failed
[  302.586596] FAT: Directory bread(block 530) failed
[  302.586609] FAT: Directory bread(block 531) failed
[  302.586620] FAT: Directory bread(block 532) failed
[  302.586632] FAT: Directory bread(block 533) failed
[  302.586644] FAT: Directory bread(block 534) failed
[  302.586655] FAT: Directory bread(block 535) failed
[  302.586667] FAT: Directory bread(block 536) failed
[  302.586679] FAT: Directory bread(block 537) failed
[  302.586690] FAT: Directory bread(block 538) failed
[  322.135877] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[  322.135910] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[  322.135949] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[  322.489911] [drm] Setting GART location based on new memory map
[  322.489927] [drm] Loading R200 Microcode
[  322.489983] [drm] writeback test succeeded in 1 usecs
[  367.596595] FAT: Directory bread(block 507) failed
[  367.596620] FAT: Directory bread(block 508) failed
[  367.596631] FAT: Directory bread(block 509) failed
[  367.596642] FAT: Directory bread(block 510) failed
[  367.596654] FAT: Directory bread(block 511) failed
[  367.596667] FAT: Directory bread(block 512) failed
[  367.596679] FAT: Directory bread(block 513) failed
[  367.596691] FAT: Directory bread(block 514) failed
[  367.596702] FAT: Directory bread(block 515) failed
[  367.596714] FAT: Directory bread(block 516) failed
[  367.596726] FAT: Directory bread(block 517) failed
[  367.596738] FAT: Directory bread(block 518) failed
[  367.596749] FAT: Directory bread(block 519) failed
[  367.596761] FAT: Directory bread(block 520) failed
[  367.596773] FAT: Directory bread(block 521) failed
[  367.596784] FAT: Directory bread(block 522) failed
[  367.596796] FAT: Directory bread(block 523) failed
[  367.596808] FAT: Directory bread(block 524) failed
[  367.596819] FAT: Directory bread(block 525) failed
[  367.596831] FAT: Directory bread(block 526) failed
[  367.596843] FAT: Directory bread(block 527) failed
[  367.596855] FAT: Directory bread(block 528) failed
[  367.596866] FAT: Directory bread(block 529) failed
[  367.596878] FAT: Directory bread(block 530) failed
[  367.596889] FAT: Directory bread(block 531) failed
[  367.596901] FAT: Directory bread(block 532) failed
[  367.596913] FAT: Directory bread(block 533) failed
[  367.596925] FAT: Directory bread(block 534) failed
[  367.596936] FAT: Directory bread(block 535) failed
[  367.596949] FAT: Directory bread(block 536) failed
[  367.596961] FAT: Directory bread(block 537) failed
[  367.596978] FAT: Directory bread(block 538) failed
[  367.597087] FAT: Directory bread(block 507) failed
[  367.597099] FAT: Directory bread(block 508) failed
[  367.597111] FAT: Directory bread(block 509) failed
[  367.597123] FAT: Directory bread(block 510) failed
[  367.597140] FAT: Directory bread(block 511) failed
[  367.597152] FAT: Directory bread(block 512) failed
[  367.597164] FAT: Directory bread(block 513) failed
[  367.597175] FAT: Directory bread(block 514) failed
[  367.597187] FAT: Directory bread(block 515) failed
[  367.597199] FAT: Directory bread(block 516) failed
[  367.597210] FAT: Directory bread(block 517) failed
[  367.597222] FAT: Directory bread(block 518) failed
[  367.597233] FAT: Directory bread(block 519) failed
[  367.597245] FAT: Directory bread(block 520) failed
[  367.597256] FAT: Directory bread(block 521) failed
[  367.597268] FAT: Directory bread(block 522) failed
[  367.597280] FAT: Directory bread(block 523) failed
[  367.597291] FAT: Directory bread(block 524) failed
[  367.597303] FAT: Directory bread(block 525) failed
[  367.597315] FAT: Directory bread(block 526) failed
[  367.597326] FAT: Directory bread(block 527) failed
[  367.597338] FAT: Directory bread(block 528) failed
[  367.597349] FAT: Directory bread(block 529) failed
[  367.597362] FAT: Directory bread(block 530) failed
[  367.597374] FAT: Directory bread(block 531) failed
[  367.597385] FAT: Directory bread(block 532) failed
[  367.597397] FAT: Directory bread(block 533) failed
[  367.597409] FAT: Directory bread(block 534) failed
[  367.597420] FAT: Directory bread(block 535) failed
[  367.597432] FAT: Directory bread(block 536) failed
[  367.597444] FAT: Directory bread(block 537) failed
[  367.597455] FAT: Directory bread(block 538) failed
[  367.597505] FAT: Directory bread(block 507) failed
[  367.597516] FAT: Directory bread(block 508) failed
[  367.597528] FAT: Directory bread(block 509) failed
[  367.597540] FAT: Directory bread(block 510) failed
[  367.597552] FAT: Directory bread(block 511) failed
[  367.597564] FAT: Directory bread(block 512) failed
[  367.597575] FAT: Directory bread(block 513) failed
[  367.597587] FAT: Directory bread(block 514) failed
[  367.597598] FAT: Directory bread(block 515) failed
[  367.597610] FAT: Directory bread(block 516) failed
[  367.597621] FAT: Directory bread(block 517) failed
[  367.597633] FAT: Directory bread(block 518) failed
[  367.597645] FAT: Directory bread(block 519) failed
[  367.597657] FAT: Directory bread(block 520) failed
[  367.597668] FAT: Directory bread(block 521) failed
[  367.597680] FAT: Directory bread(block 522) failed
[  367.597692] FAT: Directory bread(block 523) failed
[  367.597703] FAT: Directory bread(block 524) failed
[  367.597715] FAT: Directory bread(block 525) failed
[  367.597726] FAT: Directory bread(block 526) failed
[  367.597738] FAT: Directory bread(block 527) failed
[  367.597750] FAT: Directory bread(block 528) failed
[  367.597761] FAT: Directory bread(block 529) failed
[  367.597773] FAT: Directory bread(block 530) failed
[  367.597784] FAT: Directory bread(block 531) failed
[  367.597796] FAT: Directory bread(block 532) failed
[  367.597808] FAT: Directory bread(block 533) failed
[  367.597819] FAT: Directory bread(block 534) failed
[  367.597831] FAT: Directory bread(block 535) failed
[  367.597846] FAT: Directory bread(block 536) failed
[  367.597863] FAT: Directory bread(block 537) failed
[  367.597875] FAT: Directory bread(block 538) failed
[  367.597924] FAT: Directory bread(block 507) failed
[  367.597935] FAT: Directory bread(block 508) failed
[  367.597947] FAT: Directory bread(block 509) failed
[  367.597959] FAT: Directory bread(block 510) failed
[  367.597971] FAT: Directory bread(block 511) failed
[  367.597983] FAT: Directory bread(block 512) failed
[  367.597994] FAT: Directory bread(block 513) failed
[  367.598006] FAT: Directory bread(block 514) failed
[  367.598017] FAT: Directory bread(block 515) failed
[  367.598029] FAT: Directory bread(block 516) failed
[  367.598040] FAT: Directory bread(block 517) failed
[  367.598052] FAT: Directory bread(block 518) failed
[  367.598063] FAT: Directory bread(block 519) failed
[  367.598075] FAT: Directory bread(block 520) failed
[  367.598087] FAT: Directory bread(block 521) failed
[  367.598099] FAT: Directory bread(block 522) failed
[  367.598111] FAT: Directory bread(block 523) failed
[  367.598122] FAT: Directory bread(block 524) failed
[  367.598134] FAT: Directory bread(block 525) failed
[  367.598145] FAT: Directory bread(block 526) failed
[  367.598157] FAT: Directory bread(block 527) failed
[  367.598168] FAT: Directory bread(block 528) failed
[  367.598180] FAT: Directory bread(block 529) failed
[  367.598192] FAT: Directory bread(block 530) failed
[  367.598203] FAT: Directory bread(block 531) failed
[  367.598215] FAT: Directory bread(block 532) failed
[  367.598227] FAT: Directory bread(block 533) failed
[  367.598238] FAT: Directory bread(block 534) failed
[  367.598250] FAT: Directory bread(block 535) failed
[  367.598262] FAT: Directory bread(block 536) failed
[  367.598273] FAT: Directory bread(block 537) failed
[  367.598285] FAT: Directory bread(block 538) failed
[  367.598333] FAT: Directory bread(block 507) failed
[  367.598345] FAT: Directory bread(block 508) failed
[  367.598357] FAT: Directory bread(block 509) failed
[  367.598369] FAT: Directory bread(block 510) failed
[  367.598381] FAT: Directory bread(block 511) failed
[  367.598392] FAT: Directory bread(block 512) failed
[  367.598404] FAT: Directory bread(block 513) failed
[  367.598421] FAT: Directory bread(block 514) failed
[  367.598433] FAT: Directory bread(block 515) failed
[  367.598445] FAT: Directory bread(block 516) failed
[  367.598456] FAT: Directory bread(block 517) failed
[  367.598468] FAT: Directory bread(block 518) failed
[  367.598480] FAT: Directory bread(block 519) failed
[  367.598492] FAT: Directory bread(block 520) failed
[  367.598503] FAT: Directory bread(block 521) failed
[  367.598515] FAT: Directory bread(block 522) failed
[  367.598532] FAT: Directory bread(block 523) failed
[  367.598544] FAT: Directory bread(block 524) failed
[  367.598556] FAT: Directory bread(block 525) failed
[  367.598567] FAT: Directory bread(block 526) failed
[  367.598579] FAT: Directory bread(block 527) failed
[  367.598591] FAT: Directory bread(block 528) failed
[  367.598602] FAT: Directory bread(block 529) failed
[  367.598620] FAT: Directory bread(block 530) failed
[  367.598632] FAT: Directory bread(block 531) failed
[  367.598644] FAT: Directory bread(block 532) failed
[  367.598655] FAT: Directory bread(block 533) failed
[  367.598667] FAT: Directory bread(block 534) failed
[  367.598679] FAT: Directory bread(block 535) failed
[  367.598690] FAT: Directory bread(block 536) failed
[  367.598702] FAT: Directory bread(block 537) failed
[  367.598714] FAT: Directory bread(block 538) failed
[  367.598763] FAT: Directory bread(block 507) failed
[  367.598775] FAT: Directory bread(block 508) failed
[  367.598787] FAT: Directory bread(block 509) failed
[  367.598804] FAT: Directory bread(block 510) failed
[  367.598816] FAT: Directory bread(block 511) failed
[  367.598828] FAT: Directory bread(block 512) failed
[  367.598842] FAT: Directory bread(block 513) failed
[  367.598853] FAT: Directory bread(block 514) failed
[  367.598865] FAT: Directory bread(block 515) failed
[  367.598882] FAT: Directory bread(block 516) failed
[  367.598894] FAT: Directory bread(block 517) failed
[  367.598905] FAT: Directory bread(block 518) failed
[  367.598921] FAT: Directory bread(block 519) failed
[  367.598932] FAT: Directory bread(block 520) failed
[  367.598944] FAT: Directory bread(block 521) failed
[  367.598956] FAT: Directory bread(block 522) failed
[  367.598968] FAT: Directory bread(block 523) failed
[  367.598979] FAT: Directory bread(block 524) failed
[  367.598991] FAT: Directory bread(block 525) failed
[  367.599003] FAT: Directory bread(block 526) failed
[  367.599015] FAT: Directory bread(block 527) failed
[  367.599026] FAT: Directory bread(block 528) failed
[  367.599038] FAT: Directory bread(block 529) failed
[  367.599050] FAT: Directory bread(block 530) failed
[  367.599061] FAT: Directory bread(block 531) failed
[  367.599073] FAT: Directory bread(block 532) failed
[  367.599085] FAT: Directory bread(block 533) failed
[  367.599101] FAT: Directory bread(block 534) failed
[  367.599113] FAT: Directory bread(block 535) failed
[  367.599124] FAT: Directory bread(block 536) failed
[  367.599136] FAT: Directory bread(block 537) failed
[  367.599148] FAT: Directory bread(block 538) failed
[  367.599195] FAT: Directory bread(block 507) failed
[  367.599207] FAT: Directory bread(block 508) failed
[  367.599219] FAT: Directory bread(block 509) failed
[  367.599231] FAT: Directory bread(block 510) failed
[  367.599242] FAT: Directory bread(block 511) failed
[  367.599254] FAT: Directory bread(block 512) failed
[  367.599266] FAT: Directory bread(block 513) failed
[  367.599278] FAT: Directory bread(block 514) failed
[  367.599289] FAT: Directory bread(block 515) failed
[  367.599301] FAT: Directory bread(block 516) failed
[  367.599319] FAT: Directory bread(block 517) failed
[  367.599330] FAT: Directory bread(block 518) failed
[  367.599342] FAT: Directory bread(block 519) failed
[  367.599353] FAT: Directory bread(block 520) failed
[  367.599365] FAT: Directory bread(block 521) failed
[  367.599377] FAT: Directory bread(block 522) failed
[  367.599388] FAT: Directory bread(block 523) failed
[  367.599400] FAT: Directory bread(block 524) failed
[  367.599411] FAT: Directory bread(block 525) failed
[  367.599423] FAT: Directory bread(block 526) failed
[  367.599435] FAT: Directory bread(block 527) failed
[  367.599452] FAT: Directory bread(block 528) failed
[  367.599464] FAT: Directory bread(block 529) failed
[  367.599475] FAT: Directory bread(block 530) failed
[  367.599487] FAT: Directory bread(block 531) failed
[  367.599498] FAT: Directory bread(block 532) failed
[  367.599510] FAT: Directory bread(block 533) failed
[  367.599527] FAT: Directory bread(block 534) failed
[  367.599539] FAT: Directory bread(block 535) failed
[  367.599551] FAT: Directory bread(block 536) failed
[  367.599562] FAT: Directory bread(block 537) failed
[  367.599574] FAT: Directory bread(block 538) failed
[  367.599623] FAT: Directory bread(block 507) failed
[  367.599634] FAT: Directory bread(block 508) failed
[  367.599646] FAT: Directory bread(block 509) failed
[  367.599657] FAT: Directory bread(block 510) failed
[  367.599669] FAT: Directory bread(block 511) failed
[  367.599681] FAT: Directory bread(block 512) failed
[  367.599692] FAT: Directory bread(block 513) failed
[  367.599704] FAT: Directory bread(block 514) failed
[  367.599716] FAT: Directory bread(block 515) failed
[  367.599739] FAT: Directory bread(block 516) failed
[  367.599751] FAT: Directory bread(block 517) failed
[  367.599762] FAT: Directory bread(block 518) failed
[  367.599778] FAT: Directory bread(block 519) failed
[  367.599789] FAT: Directory bread(block 520) failed
[  367.599801] FAT: Directory bread(block 521) failed
[  367.599812] FAT: Directory bread(block 522) failed
[  367.599824] FAT: Directory bread(block 523) failed
[  367.599842] FAT: Directory bread(block 524) failed
[  367.599853] FAT: Directory bread(block 525) failed
[  367.599865] FAT: Directory bread(block 526) failed
[  367.599877] FAT: Directory bread(block 527) failed
[  367.599889] FAT: Directory bread(block 528) failed
[  367.599906] FAT: Directory bread(block 529) failed
[  367.599918] FAT: Directory bread(block 530) failed
[  367.599929] FAT: Directory bread(block 531) failed
[  367.599941] FAT: Directory bread(block 532) failed
[  367.599962] FAT: Directory bread(block 533) failed
[  367.599973] FAT: Directory bread(block 534) failed
[  367.599985] FAT: Directory bread(block 535) failed
[  367.599996] FAT: Directory bread(block 536) failed
[  367.600008] FAT: Directory bread(block 537) failed
[  367.600026] FAT: Directory bread(block 538) failed
[  367.600104] FAT: Directory bread(block 507) failed
[  367.600122] FAT: Directory bread(block 508) failed
[  367.600133] FAT: Directory bread(block 509) failed
[  367.600145] FAT: Directory bread(block 510) failed
[  367.600157] FAT: Directory bread(block 511) failed
[  367.600168] FAT: Directory bread(block 512) failed
[  367.600180] FAT: Directory bread(block 513) failed
[  367.600191] FAT: Directory bread(block 514) failed
[  367.600203] FAT: Directory bread(block 515) failed
[  367.600215] FAT: Directory bread(block 516) failed
[  367.600226] FAT: Directory bread(block 517) failed
[  367.600238] FAT: Directory bread(block 518) failed
[  367.600250] FAT: Directory bread(block 519) failed
[  367.600261] FAT: Directory bread(block 520) failed
[  367.600272] FAT: Directory bread(block 521) failed
[  367.600284] FAT: Directory bread(block 522) failed
[  367.600296] FAT: Directory bread(block 523) failed
[  367.600307] FAT: Directory bread(block 524) failed
[  367.600319] FAT: Directory bread(block 525) failed
[  367.600330] FAT: Directory bread(block 526) failed
[  367.600357] FAT: Directory bread(block 527) failed
[  367.600369] FAT: Directory bread(block 528) failed
[  367.600381] FAT: Directory bread(block 529) failed
[  367.600392] FAT: Directory bread(block 530) failed
[  367.600404] FAT: Directory bread(block 531) failed
[  367.600415] FAT: Directory bread(block 532) failed
[  367.600427] FAT: Directory bread(block 533) failed
[  367.600439] FAT: Directory bread(block 534) failed
[  367.600451] FAT: Directory bread(block 535) failed
[  367.600463] FAT: Directory bread(block 536) failed
[  367.600480] FAT: Directory bread(block 537) failed
[  367.600491] FAT: Directory bread(block 538) failed
[  367.600581] FAT: Directory bread(block 507) failed
[  367.600593] FAT: Directory bread(block 508) failed
[  367.600605] FAT: Directory bread(block 509) failed
[  367.600622] FAT: Directory bread(block 510) failed
[  367.600634] FAT: Directory bread(block 511) failed
[  367.600646] FAT: Directory bread(block 512) failed
[  367.600657] FAT: Directory bread(block 513) failed
[  367.600669] FAT: Directory bread(block 514) failed
[  367.600680] FAT: Directory bread(block 515) failed
[  367.600692] FAT: Directory bread(block 516) failed
[  367.600704] FAT: Directory bread(block 517) failed
[  367.600715] FAT: Directory bread(block 518) failed
[  367.600727] FAT: Directory bread(block 519) failed
[  367.600739] FAT: Directory bread(block 520) failed
[  367.600750] FAT: Directory bread(block 521) failed
[  367.600762] FAT: Directory bread(block 522) failed
[  367.600773] FAT: Directory bread(block 523) failed
[  367.600785] FAT: Directory bread(block 524) failed
[  367.600797] FAT: Directory bread(block 525) failed
[  367.600808] FAT: Directory bread(block 526) failed
[  367.600820] FAT: Directory bread(block 527) failed
[  367.600831] FAT: Directory bread(block 528) failed
[  367.600843] FAT: Directory bread(block 529) failed
[  367.600854] FAT: Directory bread(block 530) failed
[  367.600866] FAT: Directory bread(block 531) failed
[  367.600878] FAT: Directory bread(block 532) failed
[  367.600889] FAT: Directory bread(block 533) failed
[  367.600901] FAT: Directory bread(block 534) failed
[  367.600912] FAT: Directory bread(block 535) failed
[  367.600924] FAT: Directory bread(block 536) failed
[  367.600936] FAT: Directory bread(block 537) failed
[  367.600947] FAT: Directory bread(block 538) failed
[  367.601013] FAT: Directory bread(block 507) failed
[  367.601025] FAT: Directory bread(block 508) failed
[  367.601037] FAT: Directory bread(block 509) failed
[  367.601048] FAT: Directory bread(block 510) failed
[  367.601060] FAT: Directory bread(block 511) failed
[  367.601072] FAT: Directory bread(block 512) failed
[  367.601083] FAT: Directory bread(block 513) failed
[  367.601095] FAT: Directory bread(block 514) failed
[  367.601106] FAT: Directory bread(block 515) failed
[  367.601118] FAT: Directory bread(block 516) failed
[  367.601129] FAT: Directory bread(block 517) failed
[  367.601141] FAT: Directory bread(block 518) failed
[  367.601153] FAT: Directory bread(block 519) failed
[  367.601165] FAT: Directory bread(block 520) failed
[  367.601176] FAT: Directory bread(block 521) failed
[  367.601188] FAT: Directory bread(block 522) failed
[  367.601199] FAT: Directory bread(block 523) failed
[  367.601211] FAT: Directory bread(block 524) failed
[  367.601222] FAT: Directory bread(block 525) failed
[  367.601234] FAT: Directory bread(block 526) failed
[  367.601245] FAT: Directory bread(block 527) failed
[  367.601257] FAT: Directory bread(block 528) failed
[  367.601269] FAT: Directory bread(block 529) failed
[  367.601281] FAT: Directory bread(block 530) failed
[  367.601292] FAT: Directory bread(block 531) failed
[  367.601309] FAT: Directory bread(block 532) failed
[  367.601321] FAT: Directory bread(block 533) failed
[  367.601332] FAT: Directory bread(block 534) failed
[  367.601345] FAT: Directory bread(block 535) failed
[  367.601357] FAT: Directory bread(block 536) failed
[  367.601368] FAT: Directory bread(block 537) failed
[  367.601380] FAT: Directory bread(block 538) failed
[  368.599581] FAT: Directory bread(block 507) failed
[  368.599604] FAT: Directory bread(block 508) failed
[  368.599616] FAT: Directory bread(block 509) failed
[  368.599627] FAT: Directory bread(block 510) failed
[  368.599639] FAT: Directory bread(block 511) failed
[  368.599658] FAT: Directory bread(block 512) failed
[  368.599670] FAT: Directory bread(block 513) failed
[  368.599681] FAT: Directory bread(block 514) failed
[  368.599693] FAT: Directory bread(block 515) failed
[  368.599705] FAT: Directory bread(block 516) failed
[  368.599717] FAT: Directory bread(block 517) failed
[  368.599735] FAT: Directory bread(block 518) failed
[  368.599747] FAT: Directory bread(block 519) failed
[  368.599758] FAT: Directory bread(block 520) failed
[  368.599770] FAT: Directory bread(block 521) failed
[  368.599782] FAT: Directory bread(block 522) failed
[  368.599794] FAT: Directory bread(block 523) failed
[  368.599805] FAT: Directory bread(block 524) failed
[  368.599817] FAT: Directory bread(block 525) failed
[  368.599829] FAT: Directory bread(block 526) failed
[  368.599840] FAT: Directory bread(block 527) failed
[  368.599852] FAT: Directory bread(block 528) failed
[  368.599864] FAT: Directory bread(block 529) failed
[  368.599876] FAT: Directory bread(block 530) failed
[  368.599887] FAT: Directory bread(block 531) failed
[  368.599899] FAT: Directory bread(block 532) failed
[  368.599910] FAT: Directory bread(block 533) failed
[  368.599922] FAT: Directory bread(block 534) failed
[  368.599934] FAT: Directory bread(block 535) failed
[  368.599946] FAT: Directory bread(block 536) failed
[  368.599958] FAT: Directory bread(block 537) failed
[  368.599969] FAT: Directory bread(block 538) failed
[  368.616881] FAT: Directory bread(block 507) failed
[  368.616914] FAT: Directory bread(block 508) failed
[  368.616925] FAT: Directory bread(block 509) failed
[  368.616935] FAT: Directory bread(block 510) failed
[  368.616946] FAT: Directory bread(block 511) failed
[  368.616959] FAT: Directory bread(block 512) failed
[  368.616971] FAT: Directory bread(block 513) failed
[  368.616983] FAT: Directory bread(block 514) failed
[  368.616995] FAT: Directory bread(block 515) failed
[  368.617007] FAT: Directory bread(block 516) failed
[  368.617019] FAT: Directory bread(block 517) failed
[  368.617031] FAT: Directory bread(block 518) failed
[  368.617049] FAT: Directory bread(block 519) failed
[  368.617061] FAT: Directory bread(block 520) failed
[  368.617073] FAT: Directory bread(block 521) failed
[  368.617085] FAT: Directory bread(block 522) failed
[  368.617097] FAT: Directory bread(block 523) failed
[  368.617109] FAT: Directory bread(block 524) failed
[  368.617120] FAT: Directory bread(block 525) failed
[  368.617132] FAT: Directory bread(block 526) failed
[  368.617143] FAT: Directory bread(block 527) failed
[  368.617155] FAT: Directory bread(block 528) failed
[  368.617173] FAT: Directory bread(block 529) failed
[  368.617184] FAT: Directory bread(block 530) failed
[  368.617196] FAT: Directory bread(block 531) failed
[  368.617207] FAT: Directory bread(block 532) failed
[  368.617219] FAT: Directory bread(block 533) failed
[  368.617230] FAT: Directory bread(block 534) failed
[  368.617242] FAT: Directory bread(block 535) failed
[  368.617254] FAT: Directory bread(block 536) failed
[  368.617266] FAT: Directory bread(block 537) failed
[  368.617277] FAT: Directory bread(block 538) failed
[  368.617390] FAT: Directory bread(block 507) failed
[  368.617402] FAT: Directory bread(block 508) failed
[  368.617414] FAT: Directory bread(block 509) failed
[  368.617426] FAT: Directory bread(block 510) failed
[  368.617437] FAT: Directory bread(block 511) failed
[  368.617448] FAT: Directory bread(block 512) failed
[  368.617460] FAT: Directory bread(block 513) failed
[  368.617472] FAT: Directory bread(block 514) failed
[  368.617483] FAT: Directory bread(block 515) failed
[  368.617495] FAT: Directory bread(block 516) failed
[  368.617506] FAT: Directory bread(block 517) failed
[  368.617518] FAT: Directory bread(block 518) failed
[  368.617529] FAT: Directory bread(block 519) failed
[  368.617541] FAT: Directory bread(block 520) failed
[  368.617553] FAT: Directory bread(block 521) failed
[  368.617565] FAT: Directory bread(block 522) failed
[  368.617577] FAT: Directory bread(block 523) failed
[  368.617595] FAT: Directory bread(block 524) failed
[  368.617606] FAT: Directory bread(block 525) failed
[  368.617618] FAT: Directory bread(block 526) failed
[  368.617629] FAT: Directory bread(block 527) failed
[  368.617641] FAT: Directory bread(block 528) failed
[  368.617652] FAT: Directory bread(block 529) failed
[  368.617664] FAT: Directory bread(block 530) failed
[  368.617676] FAT: Directory bread(block 531) failed
[  368.617693] FAT: Directory bread(block 532) failed
[  368.617704] FAT: Directory bread(block 533) failed
[  368.617716] FAT: Directory bread(block 534) failed
[  368.617727] FAT: Directory bread(block 535) failed
[  368.617739] FAT: Directory bread(block 536) failed
[  368.617750] FAT: Directory bread(block 537) failed
[  368.617762] FAT: Directory bread(block 538) failed
[  368.617804] FAT: Directory bread(block 507) failed
[  368.617816] FAT: Directory bread(block 508) failed
[  368.617828] FAT: Directory bread(block 509) failed
[  368.617840] FAT: Directory bread(block 510) failed
[  368.617857] FAT: Directory bread(block 511) failed
[  368.617868] FAT: Directory bread(block 512) failed
[  368.617880] FAT: Directory bread(block 513) failed
[  368.617892] FAT: Directory bread(block 514) failed
[  368.617904] FAT: Directory bread(block 515) failed
[  368.617915] FAT: Directory bread(block 516) failed
[  368.617927] FAT: Directory bread(block 517) failed
[  368.617938] FAT: Directory bread(block 518) failed
[  368.617956] FAT: Directory bread(block 519) failed
[  368.617967] FAT: Directory bread(block 520) failed
[  368.617979] FAT: Directory bread(block 521) failed
[  368.617996] FAT: Directory bread(block 522) failed
[  368.618009] FAT: Directory bread(block 523) failed
[  368.618021] FAT: Directory bread(block 524) failed
[  368.618032] FAT: Directory bread(block 525) failed
[  368.618044] FAT: Directory bread(block 526) failed
[  368.618056] FAT: Directory bread(block 527) failed
[  368.618067] FAT: Directory bread(block 528) failed
[  368.618079] FAT: Directory bread(block 529) failed
[  368.618090] FAT: Directory bread(block 530) failed
[  368.618102] FAT: Directory bread(block 531) failed
[  368.618125] FAT: Directory bread(block 532) failed
[  368.618136] FAT: Directory bread(block 533) failed
[  368.618148] FAT: Directory bread(block 534) failed
[  368.618162] FAT: Directory bread(block 535) failed
[  368.618173] FAT: Directory bread(block 536) failed
[  368.618185] FAT: Directory bread(block 537) failed
[  368.618197] FAT: Directory bread(block 538) failed

```

---

### Post by motor25 on 2008-08-17
hi amb el altre comanda no amb surt res

---

### Post by motor25 on 2008-08-17
el probleme era que no abia desconectat el usb
aqui et deixo el resultat de la segonda comanda
[ 2132.769784] usb 5-2: new high speed USB device using ehci_hcd and address 6
[ 2132.903634] usb 5-2: configuration #1 chosen from 1 choice

---

### Post by motor25 on 2008-08-17
no puc compilar el que em dius ajudam si l'haig de compilar

---

