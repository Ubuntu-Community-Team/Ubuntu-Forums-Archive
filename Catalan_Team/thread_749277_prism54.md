---
title: "prism54"
date: 2008-04-08
forum: Catalan Team
---

### Post by raukonak on 2008-04-08
Hola a tots!

Bé, fa un parell de dies vaig trobar un vell adaptador wifi usb marca amper que m'està donant una mica de maldecaps i us escric una mica per aviam si em podeu orientar i una mica per fer terapia i deixar constància de la mare que va parir els drivers privatius només per a windows.

Bé, començo el relat.

El primer que faig intentar averiguar quin model és. Els nostres amics de la telefonica s'ho ha currant una vegada més i com a model, en una etiqueta al darrera, només consta "MOD. adaptador usb inalàmbrico". Bé, però això ja ho podria haver deduit jo, no té gaire pinta de torradora o de guitarra. Pas dos, si no ho posa a l'etiqueta ho miraré al lsusb. Em dona això:

```
Bus 003 Device 007: ID 09aa:1000 Intersil Corp. Prism GT 802.11b/g Adapter

```

Bé googlejant busco a intersil aviam si tenen algun driver. Ni tan sols soc capaç de trobar la pàgina del adaptador. Cremat aquest cartutx busco aviam si algú s'ha trobat en la mateixa situació que jo. Com que ho vaig buscar ahir no recordo ben bé que deien, però em vaig anar encaminant cap a un projecte que desenvolupa un driver lliure que es diu [www.prism54.org](www.prism54.org). Es veu, pel que he sigut capaç d'entendre amb el meu anglès mediocre, que el prism gt en realitat es diu prism 54. Perfecte, com si no fos ja prou complicat. La qüestió  es que miro de baixarme el driver. Però n'hi han tres i no acabo d'entedre ni la diferencia entre ells ni quin m'he de baixar ni si el meu adaptador es compatible. Així que googlejant trobo que si que ho és i que em toca el sotfMAC :confused: 

```
09AA	1000	Spinnaker Proto board	GW3887
``` 

Ho dedueixo perque té el mateix id que em sortia al lsusb, no se si l'estic cagant...I no entenc perque ara el chipset es diu GW3887.

Segueixo amb la historia. Mirant pel google, en un howto que no recordo l'adressa descobreixo que el driver ja està inclós al kernel que ve amb l'ubuntu, i que el módul es diu prism54. Llavors miro al dmesg si surt alguna cosa i em trobo amb això.

```
[ 1166.549835] usb 3-2: new high speed USB device using ehci_hcd and address 7
[ 1166.681145] usb 3-2: configuration #1 chosen from 1 choice
[ 1167.269367] p54: LM86 firmware
[ 1167.269376] p54: FW rev 2.4.3.7 - Softmac protocol 0.1
[ 1169.414063] prism54usb: eeprom read failed!
[ 1169.414105] prism54usb: probe of 3-2:1.0 failed with error -22
[ 1169.414139] usbcore: registered new interface driver prism54usb

```

Com que no pinta massa bé ho miro pel google i veig que hi ha un tiquet al lauchpad, nº90902 ([https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/90902](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/90902)). En teoria posa que ja està solucionat i que era un problema del firmware, i que amb la Gutsy funciona perfectament: Potser no em va per passar-me de llest i utilitzar la Hardy. Em sembla que el que hauria de fer és intentar actualitzar el firmware de l'adaptador, no se. Al reiniciar em detecta l'usb però em dona un error, diria que és aquest:

```
[   89.175229] usb 3-2: device descriptor read/64, error -110
[   89.391019] usb 3-2: new high speed USB device using ehci_hcd and address 4
[   94.406187] usb 3-2: device descriptor read/8, error -110
[   99.521287] usb 3-2: device descriptor read/8, error -110
[   99.736969] usb 3-2: new high speed USB device using ehci_hcd and address 5
[  104.752150] usb 3-2: device descriptor read/8, error -110
[  109.867250] usb 3-2: device descriptor read/8, error -110
[  110.494519] usb 1-2: new low speed USB device using ohci_hcd and address 3
[  110.708493] usb 1-2: configuration #1 chosen from 1 choice
[  110.886038] usbcore: registered new interface driver hiddev

```

Bé, us deixo un parell de sortides de rigor:

```
tail /var/log/messages
Apr  8 15:18:37 carles-desktop kernel: [  115.236020] [fglrx] enable ID = 0x00000005
Apr  8 15:18:37 carles-desktop kernel: [  115.236028] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
Apr  8 15:19:03 carles-desktop kernel: [  141.699942] UDF-fs: No VRS found
Apr  8 15:36:09 carles-desktop kernel: [ 1166.549835] usb 3-2: new high speed USB device using ehci_hcd and address 7
Apr  8 15:36:09 carles-desktop kernel: [ 1166.681145] usb 3-2: configuration #1 chosen from 1 choice
Apr  8 15:36:10 carles-desktop kernel: [ 1167.269367] p54: LM86 firmware
Apr  8 15:36:10 carles-desktop kernel: [ 1167.269376] p54: FW rev 2.4.3.7 - Softmac protocol 0.1
Apr  8 15:36:12 carles-desktop kernel: [ 1169.414105] prism54usb: probe of 3-2:1.0 failed with error -22
Apr  8 15:36:12 carles-desktop kernel: [ 1169.414139] usbcore: registered new interface driver prism54usb
Apr  8 15:49:22 carles-desktop syslogd 1.5.0#1ubuntu1: restart.

```

```
 dpkg -l | grep linux-restricted-modules-`unam -r`
bash: unam: command not found
ii  linux-restricted-modules-2.6.24-12-generic 2.6.24.11-12.31                                    Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-14-generic 2.6.24.12-14.32                                    Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.12-14.32                                    Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.14.16                                       Restricted Linux modules for generic kernels

```

```
lsmod
Module                  Size  Used by
p54usb                 16512  0 
p54common              13824  1 p54usb
mac80211              165652  2 p54usb,p54common
cfg80211               15112  1 mac80211
isofs                  36388  1 
udf                    88612  0 
binfmt_misc            12808  1 
joydev                 13120  0 
usbhid                 31872  0 
hid                    38784  1 usbhid
ipv6                  267780  10 
af_packet              23812  2 
rfcomm                 41744  0 
l2cap                  25728  3 rfcomm
bluetooth              61156  2 rfcomm,l2cap
ppdev                  10372  0 
speedstep_lib           6532  0 
cpufreq_stats           7104  0 
cpufreq_ondemand        9740  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
cpufreq_powersave       2688  0 
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
video                  19856  0 
output                  4736  1 video
dock                   11280  0 
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
nls_iso8859_1           4992  1 
nls_cp437               6656  1 
vfat                   14464  1 
fat                    54556  1 vfat
ac                      6916  0 
lp                     12324  0 
snd_intel8x0           35356  3 
snd_ac97_codec        101028  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_mixer_oss          17920  1 snd_pcm_oss
fglrx                1555468  23 
snd_seq_dummy           4868  0 
snd_mpu401              9448  0 
snd_mpu401_uart         9728  1 snd_mpu401
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
button                  9232  0 
snd_rawmidi            25760  2 snd_mpu401_uart,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
evdev                  13056  4 
i2c_sis96x              6148  0 
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
shpchp                 34452  0 
snd                    56996  19 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_dummy,snd_mpu401,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_core               24832  1 i2c_sis96x
soundcore               8800  1 snd
pci_hotplug            30880  1 shpchp
sis_agp                10116  1 
agpgart                34760  2 fglrx,sis_agp
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
pcspkr                  4224  0 
ext3                  136712  2 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  1 
cdrom                  37408  1 sr_mod
sd_mod                 30720  5 
ata_generic             8324  0 
floppy                 59588  0 
sis900                 24320  0 
mii                     6400  1 sis900
pata_sis               15236  5 
ehci_hcd               37900  0 
pata_acpi               8320  0 
libata                159344  3 ata_generic,pata_sis,pata_acpi
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
ohci_hcd               25348  0 
usbcore               146028  5 p54usb,usbhid,ehci_hcd,ohci_hcd
thermal                16796  0 
processor              36872  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 

```

```
 modprobe -l | grep prism54
/lib/modules/2.6.24-14-generic/kernel/drivers/net/wireless/prism54/prism54.ko

```

```
 uname -a
Linux 2.6.24-14-generic #1 SMP Thu Apr 3 04:49:29 UTC 2008 i686 GNU/Linux

```

Bé, merci per tot! Que vaig bé

---

### Post by raukonak on 2008-04-08
EEEh, com sempre, el error que fa que falli és sempre el més estupid i ridicul. He canviat el cable del usb i de cop m'ha sortit això.
```

[  390.590484] usb 3-4: USB disconnect, address 5
[  415.617203] usb 3-4: new high speed USB device using ehci_hcd and address 6
[  415.749567] usb 3-4: configuration #1 chosen from 1 choice
[  415.758510] p54: LM86 firmware
[  415.758519] p54: FW rev 2.4.3.7 - Softmac protocol 0.1
```
Coses de la vida. Per cert acabo d'actualitzar:
 uname -a
Linux 2.6.24-15-generic #1 SMP Tue Apr 8 00:33:51 UTC 2008 i686 GNU/Linux

Sigui com sigui encara no em surt al iwconfig, ho  hauria de posar a mà?

---

### Post by jodufi on 2008-04-08
No m'he llegit tot el post (m'ha espantat tanta informació) però et puc dir que amb la nova versió 8.04 la detecció d'aquests tipus de dispositius ha millorat molt. Perquè no proves com et va amb la beta?

---

### Post by Frealof on 2008-04-08
Ei bones...

No sé si [ [COLOR="Sienna"]això[/COLOR]]("http://ubuntuforums.org/showthread.php?t=695561&highlight=Amper") et pot ser útil.

A mi de moment em va funcionant :)

Apa, salut!

---

### Post by patrickfromspain on 2008-04-08
> **jodufi said:**
> No m'he llegit tot el post (m'ha espantat tanta informació) però et puc dir que amb la nova versió 8.04 la detecció d'aquests tipus de dispositius ha millorat molt. Perquè no proves com et va amb la beta?
ja la fa servir ;)

Sembla extrany, que sembla que et detecta i carrega els moduls, pero no el registra com adaptador de xarxa..

---

### Post by jodufi on 2008-04-08
Això em passa per no llegir :)

Per cert, i una mica fora de tema, com es posa un quotes d'un missatge anterior?

---

### Post by Joan Marc on 2008-04-08
posant (QUOTE)(/QUOTE) però en comptes de parèntesis claudators[ ].

---

### Post by lluisanunez on 2008-04-08
Per mandrosos: cliques al botó [IMG]http://ubuntuforums.org/images/uf/buttons/quote.gif[/IMG] de sota el missatge que vols citar

---

### Post by raukonak on 2008-04-09
Bé, jo segueixo amb la meva batalla amb el adaptador:

Primer de tot, l'altre dia sembla que me la trobava (que malament sona això) però tal i com va venir ha marxat, avui em torna a sortir el:
```

[   41.709931] prism54usb: eeprom read failed!
[   41.709959] prism54usb: probe of 3-5:1.0 failed with error -22
[   41.709983] usbcore: registered new interface driver prism54usb
[  132.986231] prism54usb: eeprom read failed!
[  132.986278] prism54usb: probe of 3-5:1.0 failed with error -22
```

Que depriment!

Merci pel link, Frealof, però de moment m'agradaria intentar fer servir el driver natiu, entre altres coses perquè es pot posar en mode monitor. Si no m'ensurto llavors si que utilitzaré el ndiswrapper.

He provat un parell de distros que tenia per aqui, una kubuntu 7.04, una dsl 3.3 (que ve amb el kernel 2.4 i no em serveix) i una altra però amb cap ha funcionat. Amb la kubuntu em sortia una altra vegada el maleit error -22, o sigui que no deu ser cosa del kernel, deu ser de la targeta o del ubuntu.

Finalment ho he provat amb el windows i ha funcionat, o sigui que no pot ser que sigui la targeta que no funciona, igual es cosa del firmware.

Ahir vaig intentar instalar el firmware, em vaig baixar uns arxius *..arm i els vaig posar a /usr/lib/hotplug (cito de memoria) però tampoc ha fet res.

Per cert, he descobert que malgrat a l'etiqueta posi amper i al lsusb posi intersil, és de la marca senao (o sigui que ja ha sopat).

Bé, ja us explicaré si m'ensurto.

Merci per tot!

---

### Post by patrickfromspain on 2008-04-09
be, si no aconsegueixes res.. bugs.ubuntu.com ;)

---

### Post by Frealof on 2008-04-09
Iep! No hi ha de què, però es que jo no faig servir el ndiswrapper, el vaig provar i res de res :(

La solució la vaig trobar una mica més avall fent això...

lsusb

Bus 002 Device 002: ID 09aa:3642 Intersil Corp. Prism 2.x 802.11b Adapter

dmesg | grep prism
[ 50.049896] prism2usb_init: prism2_usb.o: 0.2.5 Loaded
[ 50.049902] prism2usb_init: dev_info is: prism2_usb

apt-get installl linux-wlan-ng

modprobe prism2_usb prism2_doreset=1 

wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable

authtype=opensystem

A partir d'aquí... seleccionar la xarxa desitjada, entrar weps i el què faci falta i... vualà, el PC funcionant via xarxa inalàmbrica :)

Salut!

---

### Post by Frealof on 2008-04-30
Iep!

Com ho tenim? Hem pogut solucionar-ho?

Jo al actualitzar a Hardy Heron (instal·lació neta) vaig rebre una grata sorpresa perquè ell solet ja va configurar el dispositiu i esta operatiu i sense problemes desde llavors.

Salut!

---

### Post by raukonak on 2008-05-25
Bones!

Primer de tot em vull disculpar per no haver contestat, però he estat una mica liat i fins ara no li he pogut dedicar una mica de temps al wifi.

Comentaré una mica el que he fet per si algú li pogués servir d'alguna cosa, és pel Senao NL3054ub5, amb el chipset PrismGT d'Intersil 09aa:1000, que ve amb telefonica.

El driver que ve amb l'ubuntu i un parell de distribucions més que vaig provar te la versió del firmware (jo pensava que el firmware era el que estava gravat a la flash de la targeta) 2.4.6 (diria). Per saber-ho cal mirar al dmesg, pero no funciona, et dona un error 22 (ni idea).
Es veu que és un problema conegut i que es va solucionar amb la Feisty, concretament un paio va descobrir que canviant el firmware solucionava el problema. ([http://jbnote.free.fr/prism54usb/PrismFirmwares.html](http://jbnote.free.fr/prism54usb/PrismFirmwares.html)). 
Els firmwares els estan fent la gent de [www.prism54.org](www.prism54.org). Hi han tres tipus de firmwares per al chipset prism54 (que es com es diu el prismGT) el Fullmac, el Softmac i el Freemac. El Fullmac és el que tenen les targetes més antigues, i sembla que es el que estava més ben fet. Més tard van fer el Softmac, que es com una versió més simple per estalviar quartos i finalment hi ha el Freemac que es un que estan fent a base d'enginyeria inversa per aprofitar tot el que poden donar de si aquests catxarros. El que interessa es el Softmac.

A més i han varies generacions de targetes usb, la primera i la segona. El nl3054 es de la segona, per tant interessa el driver  2.5.8.0. Cal baixar-se el driver i canviar-li el nom i posar-lo a /lib/firmware/`uname -r`/isl3890usb.
A dia d'avui puc dir que detecta la targeta i la posa com a wlan0 al iwconfig, pero fent un iwlist no surt res, i el que es pitjor, al cap de minuts es penja l'ordinador. Si algú té una idea de com puc mirar perquè es penja intentaré arreglar-ho.

De moment la faig servir amb el ndiswrapper, pero m'agradaria fer-la servir amb el p54 i trastejar-la i posar-la en monitor, crackejar-me la wep o posar-la en mode master.

#Frealof:

Vaig mirar el que em vas dir però la teva targeta porta el chipset prism2 i la meva té el prism54, per això no em funciona. Igualment merci per l'interés.

Doncs bé, si algun dia l'aconsegueixo fer funcionar ja faré un tutorial, que es veu que hi ha molta gent intentant-ho.

P.D: Ara tinc el ndiswrapper i per posar-lo vaig haver de posar els moduls p54, p54usb, que son els que gestionen la targeta amb el driver nadiu, al blacklisted. El que em passa es que voldria seguir experimentant, podria carregar-los amb un insmod? Hauria de treure primer el ndiswrapper amb un rmmod? Merci per adelantat.

P.D: Perdoneu les meva deficient estructuració del text.

Apa, que vagi de gust!

---

