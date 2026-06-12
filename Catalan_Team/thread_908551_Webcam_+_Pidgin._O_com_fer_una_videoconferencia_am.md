---
title: "Webcam + Pidgin. O com fer una videoconferencia amb un contacte"
date: 2008-09-02
forum: Catalan Team
---

### Post by tanreb20 on 2008-09-02
M'interessaria saber quinprograma fer servir per fer rular la meva camera web.

Tinc un portatil Toshiba A210 con webcam integrada.

us copio el LSPCI per si veieu la webcam.. jo no jeje

[SIZE="2"]00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
14:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
1a:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
1a:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
1a:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
1a:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller[/SIZE]

també m'interesaria sabe si amb el pidgin puc enviar la meva webcam, o veure la dels contactes, he buscat pero no trobo res!


THANKS x adelantata!

---

### Post by patrickfromspain on 2008-09-02
amb el pidgin no podras fer anar la webcam. Si vols fer videoconferencia amb comptes msn hauras d'utilitzar l'amsn.

Respecte a la webcam, enganxan's la sortida de dmesg i lsusb

salut

---

### Post by tanreb20 on 2008-09-02
**[SIZE="3"]dmesg:[/SIZE]**

[SIZE="3"]**lsusb**[/SIZE]


Us deixo les informacions més avall

---

### Post by papapep on 2008-09-02
Et comento el mateix que a l'altre fil, quan el que s'ha d'enganxar és tan llarg és aconsellable crear un fitxer de text i adjuntar-lo, en vers d'enganxar.

---

### Post by tanreb20 on 2008-09-02
Ok fet:

---

### Post by pespin on 2008-09-02
A quina xarxa vols fer la videoconferencia?

Alguns exemples (xarxa -> programa):

msn -> Amsn, Kopete(?)
Jabber -> Empathy(?)
SIP -> Ekiga

---

### Post by tanreb20 on 2008-09-03
en principi msn

---

### Post by patrickfromspain on 2008-09-03
sudo apt-get install cheese

i obre'l, a veure si et veus per la webcam.

salut

---

### Post by tanreb20 on 2008-09-03
Uo!!!!!! Si sóc jo! jajaja

I per fer videoconferencia o poder veure la camera de un contacte del m sn.. he de instalar el AMSN n?

---

### Post by pespin on 2008-09-03
Sí, que jo sàpiga Amsn és l'únic que estic segur que deixa enviar imatges via webcam (Kopete i Empathy no n'etic segur).

---

### Post by sebastia2000 on 2008-10-20
Heu tastat el openwengo?

Durant un temps jo l'utilitzava per que conecta amb les xarxes yahoo, msn, jabber, gmail i d'altres... encara que video i so  només amb els contactes de la xarxa propia.

Supera a l'Ekiga en quant a configuració de xarxa (lan transversal?) i pots tenir un compte com amb l'skype i parlar per telèfon i enviar sms (aquestes coses no les he provades)
A més té una "versiò windowsera" pels vostres amics que encara estiguen al "lado oscuro".

Evidentment codi obert. [www.openwengo.org](www.openwengo.org) ups!! perdó, ara [http://www.qutecom.org/](http://www.qutecom.org/)

Salut i sort!!

---

### Post by lo gambusí on 2008-10-20
> **sebastia2000 said:**
> Heu tastat el openwengo?

Durant un temps jo l'utilitzava per que conecta amb les xarxes yahoo, msn, jabber, gmail i d'altres... encara que video i so  només amb els contactes de la xarxa propia.

Supera a l'Ekiga en quant a configuració de xarxa (lan transversal?) i pots tenir un compte com amb l'skype i parlar per telèfon i enviar sms (aquestes coses no les he provades)
A més té una "versiò windowsera" pels vostres amics que encara estiguen al "lado oscuro".

Evidentment codi obert. [www.openwengo.org](www.openwengo.org) ups!! perdó, ara [http://www.qutecom.org/](http://www.qutecom.org/)

Salut i sort!!

Home, mira, precisament anava a obrir un fil d'este tema. L'OpenWengo ha mort, no? El qutecoem este me dóna algun problema... he descarregat la versió per FC9, l'he convertit a .deb amb l'alien i l'he instal·lat. Quan l'inicio, però, em diu > qutecom: error while loading shared libraries: libboost_program_options.so.3: cannot open shared object file: No such file or directory
:?

---

### Post by PatrickVogeli on 2008-10-20
sudo apt-get install libboost-program-options1.35.0 libboost-program-options1.34.1 

prova aixo, a veure si aixi et deixa obrir-lo

---

### Post by lo gambusí on 2008-10-20
doncs no, em dóna el mateix missatge.

---

