---
title: "tarja ATI monitor extern no va Fn+F8 amb hardy"
date: 2008-10-23
forum: Catalan Team
---

### Post by indiosincracia on 2008-10-23
m'estic barallant amb un segon monitor ara mateix;
la tarja gràfica; VGA compatible controller: ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 02)
sistema hardy 8.04, amb la combinació Fn+F8 d'un Dell c600 m'hauria de rutllar. He substituït l'apartat "monitor" "screen" "server layout" pel xorg de la slax cd-live que si que va, el resultat es que no s'inicien les X.
a veure qui hem pot orientar, mercès.

---

### Post by papapep on 2008-10-23
I amb quin controlador la fas anar?

---

### Post by indiosincracia on 2008-10-23
indiosincracia@tontet:~$ sudo lshw -C Display
[sudo] password for tontet:
  *-display UNCLAIMED
       description: VGA compatible controller
       product: Rage Mobility M3 AGP 2x
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 02
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm vga_controller bus_master cap_list
       configuration: latency=32 mingnt=8

---

### Post by papapep on 2008-10-23
Em referia al controlador de programari :-D (el driver)

---

### Post by indiosincracia on 2008-10-23
si no es això no et segueixo Josep, deixa'm l'ordre de termial i t'ho postejo, merci.
xserver-xorg-video-ati
xserver-xorg-video-ati-dbg

indiosincracia@tontet:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:03.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
00:03.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
00:10.0 Ethernet controller: 3Com Corporation 3c556 Hurricane CardBus [Cyclone] (rev 10)
00:10.1 Communication controller: 3Com Corporation Mini PCI 56k Winmodem (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 02)
02:00.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)

---

### Post by CarlesOriol on 2008-10-25
Cal diferenciar dues coses:

1 - Si el controlador de la gràfica et suporta el multiple monitor

2 - Si existeix l'assignació correcta de la tecla fn+f8

Així que anem per parts: 

TEMA 1 -------------------------------------------------------

1 - Si fas servir el controlador ATI (el lliure) al menu > sistema > preferències >
Resolució de pantalla i prova cada monitor (si t'ho permet).
Si amb això ho aconseguim sempre podem insta&#320;lar un applet de gnome que controla el xrandr per fer el canvi de resolució/monitor.

2 - Si fas servir el controlador privatiu (FGLRX) aquest inclou una opció al menú aplicacions > eines del sistema anomenada catalyst que et permet fer aquests canvis.


TEMA 2 --------------------------------------------------------

npi

---

### Post by quitus on 2008-10-25
> **CarlesOriol said:**
> 
2 - Si fas servir el controlador privatiu (FGLRX) aquest inclou una opció al menú aplicacions > eines del sistema anomenada catalyst que et permet fer aquests canvis.


TEMA 2 --------------------------------------------------------

npi

que no funciona gens be, com a minim amb un sobretaula i una ATI Technologies Inc RV410 [Radeon X700]

jo haig de desconnectar el primer monitor i reiniciar les X amb el segon monitor connectat.

salut

---

### Post by CarlesOriol on 2008-10-25
> **quitus said:**
> que no funciona gens be, com a minim amb un sobretaula i una ATI Technologies Inc RV410 [Radeon X700]

jo haig de desconnectar el primer monitor i reiniciar les X amb el segon monitor connectat.

A veure: en les ati generalitzar no serveix per res. La única cosa segura amb una ati és: problemes.

Però jo tinc algunes que el catalist va de conya ( a d'altres no)

D'altra banda estan fent canvis brutals en les noves versions de controladors (tant els lliures com els privatius) i en el mateix intrepid ibex ja es noten moltes d'aquestes millores.

---

### Post by indiosincracia on 2008-10-25
Salut, s'acaba el dia i les idees, subscric que ati=mal de cap, només cal veure la quantitat de fòrums que parlen del mateix, he arribat a la conclusió que no només es un problema de driver, també de configuració de les X. 

he instal·lat fglrx seguint aquest Manuel:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI?action=fullsearch&context=180&value=ATI+Technologies+Inc+Rage+Mobility+M3+AGP+2x&fullsearch=Text](https://help.ubuntu.com/community/BinaryDriverHowto/ATI?action=fullsearch&context=180&value=ATI+Technologies+Inc+Rage+Mobility+M3+AGP+2x&fullsearch=Text)

Fatal server error:
no screens found
giving up.

podien haver substituït "no screens foud" per "scream found giving up" o "no ice cream found":biggrin::biggrin:

TEMA 1 (d'en Carles)------------------
no m'ho permet.
TEMA 2 ---------------------------------
Si no vaig errat, l'assignació de la tecla fn+f8 ve determinada per la bios, la bios si que m'apareix per la segona pantalla, i el procés de carrega, inclòs el kdm però s'atura quan inicia les X.

També m'he baixat l'iso de la "cabra" 8.10, encara que no es definitiu, de moment la segona pantalla queda fosca.
Com veig que m'he enredat amb la Hardy, puc fer un backup Gutsynià amb l'xorg.conf de la 6.10, que si qu'anava.
Merci a tots.

---

### Post by CarlesOriol on 2008-10-27
> **indiosincracia said:**
> 
1. no m'ho permet.
...
2. fn+f8 ve determinada per la bios
...
3. També m'he baixat l'iso de la "cabra" 8.10 de moment la segona pantalla queda fosca.
...
4. ... fer un backup Gutsynià amb l'xorg.conf de la 6.10, que si qu'anava.


1. Quina part no et permet? Quin controlador tens?

2. No, l'assignació de les tecles especials es realitza per programari

3. Has provat a l'intrepid els dos controladors i les dues opcions d'assignació de monitors que et deia?

4. L'xorg.conf de les versions anteriors (a hardy) normalment no et funcionarà a les noves.

---

