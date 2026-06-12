---
title: "[SOLVED] No puc connectar amb Intel PRO/Wireless 2200BG [Era:Més problemes amb Intern"
date: 2008-02-04
forum: Catalan Team
---

### Post by SiSTeR on 2008-02-04
Primer de tot, hola a tothom.

Resulta que fa dos dies per fí vaig decidir fer el salt a l'Ubuntu, amb poca idea de com es fa servir i vaig decidir eliminar Windows igualment. A lo kamikaze vaja.

L'assumpte és que no he aconseguit connectar-me amb WIFI.. Quan em connecte m'informa que està connectat però té 0% de cobertura. Diverses persones m'han intentat ajudar però no ha hagut forma i estic connectada ara amb cable.

Pegue el que haveu demanat a un altre fil:

---

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"WLAN_FB"  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality: 0  Signal level: 0  Noise level: 0
          Rx invalid nwid: 0  Rx invalid crypt: 0  Rx invalid frag: 0
          Tx excessive retries: 0  Invalid misc: 0   Missed beacon: 0


---

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:9B:E7:61  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4636 errors: 0 dropped: 0 overruns: 0 frame: 0
          TX packets:4326 errors: 0 dropped: 0 overruns: 0 carrier: 0
          collisions: 0 txqueuelen:1000 
          RX bytes:4070192 (3.8 MB)  TX bytes:843411 (823.6 KB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:13:CE:2C:5E:C8  
          inet addr:192.168.1.54  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2373 errors:0 dropped:0 overruns:0 frame:0
          TX packets:381 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 Base address:0x4000 Memory:b8006000-b8006fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3529 (3.4 KB)  TX bytes:3529 (3.4 KB)

---

iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:13:F7:7E:16:AC
                    ESSID:"YaComE16964"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=65/100  Signal level=-61 dBm  
                    Extra: Last beacon: 336ms ago
          Cell 02 - Address: 00:01:38:87:AE:CE
                    ESSID:"WLAN_01"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=39/100  Signal level=-77 dBm  
                    Extra: Last beacon: 304ms ago
          Cell 03 - Address: 00:01:38:68:14:6A
                    ESSID:"WLAN_82"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=44/100  Signal level=-74 dBm  
                    Extra: Last beacon: 240ms ago
          [B]Cell 04 - Address: 00:16:38:C6:35:CC
                    ESSID:"WLAN_FB"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:12
                    Channel:0
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=92/100  Signal level=-36 dBm  
                    Extra: Last beacon: 124ms ago
                    Extra: Channel flags: INVALID [/B]
          Cell 05 - Address: 00:13:49:D4:FA:9F
                    ESSID:"WLAN_8C"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=25/100  Signal level=-84 dBm  
                    Extra: Last beacon: 148ms ago
          [B]Cell 06 - Address: 00:02:CF:4D:B4:14
                    ESSID:"WLAN_FB"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:12
                    Channel:0
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=44/100  Signal level=-74 dBm  
                    Extra: Last beacon: 144ms ago
                    Extra: Channel flags: INVALID [/B]


Serveix d'alguna cosa?

PS: Una altra cosa, intente canviar la configuració del teclat per poder escriure arrobes i no serveix de res.

---

### Post by papapep on 2008-02-04
Benvinguda al fòrum i al món lliure!

T'animo, abans que res, a passar pel fil de benvinguda i explicar-nos una mica "la teva vida" ;-) 

Sembla que el dispositiu wifi et detecta totes les xarxes que tens al voltant així doncs, sembla que aquest funciona correctament.
Tot i això, no estaria de més que ens posessis què et mostra la comanda:

```
lspci | grep Network
```

També estaria bé saber a quina xarxa pretens connectar-te i amb quina encriptació, de tenir-ne habilitada.
Així mateix, estaria bé que ens expliquessis com configures el diàleg de configuració del dispositiu (una impressió de pantalla aniria de conya).

---

### Post by lo gambusí on 2008-02-04
Jo a tu te conec.:lolflag:

---

### Post by SiSTeR on 2008-02-04
Abans de tot, cosa que hauria d'haver fet i dit abans, no he posat aquesta última acció que m'has dit perquè no em deixa configurar el teclat i no puc escriure l'arroba ni la resta... 

Quan clique Sistema > Preferències > Teclat i elegisc Spain Catalan variant tot queda igual i seguisc sense poder.

Pretenc connectar-me a WLAN_FB, una de les dues que ixen. He provat de canviar el nom i llevar-li la contrassenya però tampoc s'ha connectat, pel que va deduïr una persona que va estar ajudant-me l'encriptació és Ascii.

He provat tant en mode itinerant com escrivint totes les dades com ho tenia abans a Guindous: Configuració, IP, Màscara de subxarxa, passarel·la,..



PS: Moltíssimes gràcies per l'ajuda!

---

### Post by papapep on 2008-02-04
Doncs si no pots posar el pipe "|" fica tota la sortida de:

```
lspci
```

ja buscarem el que és important.

---

### Post by jodufi on 2008-02-04
Pot ser que tinguis el teclat en configurat en anglès? Si es així, per escriure la «|» has d'escriure «¿».

---

### Post by SiSTeR on 2008-02-05
lspci | grep Network
06:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

---

### Post by papapep on 2008-02-06
Aquesta placa t'hauria de funcionar perfectament. De fet és la que tinc jo al R50, o sigui que ja veus.
Fes un 

```
lsmod
```

 i enganxa el que et posa, si us plau. De pas també aniria bé saber quin model d'ordinador tens en concret.

---

### Post by SiSTeR on 2008-02-07
És un Toshiba satellite a80-183
[http://www.precios10.com/toshiba/satellite_A80_183.html]("http://www.precios10.com/toshiba/satellite_A80_183.html")


Module                  Size  Used by
nls_cp437               6784  1 
isofs                  36412  1 
udf                    87204  0 
ipv6                  273892  8 
af_packet              24840  2 
i915                   25856  2 
drm                    83348  3 i915
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
acpi_cpufreq           10568  0 
cpufreq_ondemand        9612  1 
cpufreq_conservative     8072  0 
cpufreq_stats           7232  0 
cpufreq_userspace       5280  0 
cpufreq_powersave       2688  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
container               5504  0 
button                  8976  0 
battery                11012  0 
sbs                    19592  0 
video                  18060  0 
ac                      6148  0 
dock                   10656  0 
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
loop                   19076  0 
joydev                 11328  0 
snd_intel8x0           34972  1 
snd_ac97_codec        100644  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
pcmcia                 41388  0 
snd_seq_midi            9600  0 
ipw2200               149320  0 
snd_rawmidi            25728  1 snd_seq_midi
serio_raw               8068  0 
psmouse                39952  0 
ieee80211              35656  1 ipw2200
ieee80211_crypt         7040  1 ieee80211
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
sky2                   46852  0 
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
snd                    54660  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
intel_agp              25620  1 
agpgart                35016  3 drm,intel_agp
evdev                  11136  5 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sr_mod                 17828  1 
cdrom                  37536  1 sr_mod
sd_mod                 30336  3 
ata_piix               17540  3 
ata_generic             8452  0 
ahci                   23300  0 
libata                125168  3 ata_piix,ata_generic,ahci
scsi_mod              147084  5 sbp2,sg,sr_mod,sd_mod,libata
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  3 ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor

---

### Post by papapep on 2008-02-07
> ipw2200 149320 0 

Sembla que el tens correctament carregat (cosa que ja es veia al detectar les xarxes del teu voltant). 
Jo crec que ha de ser un problema amb el gnome-network manager, el gestor de xarxes que porta per defecte el Gnome. A mi em portava molts problemes.
Pots provar el que faig servir jo que es diu Wicd, i em va de perilles. Se d'altra gent que el té i, per ara i tant, els va bé.

[Aquí]("http://wicd.sourceforge.net/download.php") tens explicació de com instal·lar-lo.

Si et cal ajuda, ja ho diràs.

Quan l'instal·lis, no t'espantis que et demanarà d'esborrar el gnome-network-manager i alguna cosa més (dos o tres paquets). Tira endevant, que és normal.

---

### Post by SiSTeR on 2008-02-07
He  provat d'instal·lar el wicd però resulta que a l'instal·lar-lo no em deixa configurar ja que m'apareix i em desapareix el programa.

A que potser degut?

---

### Post by papapep on 2008-02-07
Executa:

```
/opt/wicd/tray.py
```

i t'hauria d'aparèixer una icona a la barra per a poder configurar-lo.

---

### Post by SiSTeR on 2008-03-16
Després de molt de temps he aconseguit instal·lar el Wicd però, continue amb les mateixes, no em deixa connectar a la xarxa de casa. :cry::cry:

---

### Post by papapep on 2008-03-16
Però quan obres l'interfície del Wicd, veus alguna xarxa inalàmbrica, o no??

---

### Post by SiSTeR on 2008-03-16
Sí, les veig totes. Però no se'm connecta quan pose la contrassenya, he provat amb les IP estàtiques i DNS però tampoc.

---

### Post by papapep on 2008-03-16
Doncs si les veu, és que la placa funciona correctament. Si el Wicd també les mostra, doncs també funciona bé. Si  has repassat que els paràmetres de xarxa i d'encriptació els entris correctament i en el format adeqüat, doncs no queda massa per comprovar...

L'únic que se m'acudeix és que [podries acostar-te a Caldes]("http://ubuntuforums.org/showthread.php?t=712412") el 26 del mes vinent a que li fèssim un cop d'ull a tot plegat (i de pas ens ho passem bé tots plegats :-))

---

### Post by patrickfromspain on 2008-03-16
Estas segur de que estas elegint el tipus de contrasenya correctament? El més habitual es WEP (Hex o Passphrase) o WPA. D'altra banda, a preferències del wicd, on hi posa connector del WPA supplicant, alla pots elegir varies coses, entres ells, IPW (Intel Pro Wireless), ho has provat?

sort i salut!

PD: si vas a caldes.. ves en compte :rolleyes: :biggrin:

---

### Post by papapep on 2008-03-16
> PD: si vas a caldes.. ves en compte  

Ara no sé pas a què et refereixes....:twisted:

---

### Post by SiSTeR on 2008-03-16
He trobat [açò]("http://iruasecas.bitacoras.com/archivos/2005/10/27/linea_adsl_de_telefonica_en_ubuntu_ct_351") que supose em pot anar bé per la connexió (mai es sap).

Però quan estic per la instal·lació ix error i no hi ha manera. Sabeu de que va quan et diu lo següent?

make[1]: *** [eu_main.o] Error 1
make[1]: Leaving directory `/home/immas/Escriptori/eagle-usb-1.9.9.1/driver'
make: *** [build] Error 2
root@cosafriqui:/home/immas/Escriptori/eagle-usb-1.9.9.1# make install
make -C driver install && \
        make -C pppoa install && \
        make -C utils/scripts install && \
        make -C utils/eagleconnect install && \
        make -C doc install && \
        hash -r && \
        echo -e "===============================================================================" && \
        echo -e "\n\nInstallation has finished!\nYou should now run eagleconfig to setup your connexion.\n\n"
make[1]: Entering directory `/home/immas/Escriptori/eagle-usb-1.9.9.1/driver'
make -C ./firmware install
make[2]: Entering directory `/home/immas/Escriptori/eagle-usb-1.9.9.1/driver/firmware'
/usr/bin/install -c -d /etc/eagle-usb/dsp && \
        /usr/bin/install -c -m 0664 dsp_code_pots.bin /etc/eagle-usb/dsp
/usr/bin/install: ha fallat stat() sobre «dsp_code_pots.bin»: No such file or directory
make[2]: *** [install] Error 1
make[2]: Leaving directory `/home/immas/Escriptori/eagle-usb-1.9.9.1/driver/firmware'
make[1]: *** [installdsp] Error 2
make[1]: Leaving directory `/home/immas/Escriptori/eagle-usb-1.9.9.1/driver'
make: *** [install] Error 2

---

### Post by papapep on 2008-03-16
Si no saps què estàs fent és mal assumpte dedicar-te a compilar mòduls. Sobretot si ja et funciona perfectament la placa inalàmbrica. Com a minim pots acabar pitjor que com estàs.

Os es suposa que vols arribar compilant això?? (per cert, l'enllaç que has posat no funciona).

---

### Post by SiSTeR on 2008-04-01
Ja està bé l'enllaç.

---

### Post by papapep on 2008-04-01
Ara sí que m'he perdut (serà el temps que ha passat?). Què te a veure el router amb el problema que tens amb la configuració de la targeta wifi del portàtil???? O és que ho fiques tot al mateix sac?
El Comtrend aquest, té prestacions de router wifi???

---

### Post by SiSTeR on 2008-11-21
Fóra el que fóra, tinc portàtil nou, l'altre va morir, i amb el 8.10 pareix que va perfecte.

Gràcies als que vau ajudar  ;)

---

### Post by SiscoGarcia on 2008-11-21
SiSTeR, consideres que el fil està resolt?

Si és així, sisplau marca'l com a tal,... ja saps, "Thread Tools > Mark This Thread As Solved ;)

---

