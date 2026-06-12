---
title: "La ethernet va boja"
date: 2008-05-01
forum: Catalan Team
---

### Post by pespin on 2008-05-01
He instal·lat una Hardy des de 0 amb el CD del Hardy Server. (Utilitzo el server perquè em permet després instal·lar diferents gestors gràfics i tota la pesca).

Doncs ha acabat la instal·lació sense cap problema, he reiniciat i he vist que no tenia connexió a internet (els pings tornaven unknown host crec recordar). Al iniciar sortien les 3 primeres linies d'això, que després queda imprés al dmesg:

"dmesg | grep eth":

```
[   21.075940] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   21.076322] forcedeth 0000:00:07.0: Invalid Mac address detected: 79:2a:e0:8f:13:00
[   21.076325] forcedeth 0000:00:07.0: Please complain to your hardware vendor. Switching to a random MAC.
[   21.595888] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x20 @ 1, addr 00:00:6c:b1:bf:32
[   21.595894] forcedeth 0000:00:07.0: highdma pwrctl mgmt timirq lnktim msi desc-v3
[   22.470918] Driver 'sr' needs updating - please use bus_type methods
[   23.281620] Driver 'sd' needs updating - please use bus_type methods
[   34.201207] udev: renamed network interface eth0 to eth5
[  100.244519] eth5: no IPv6 routers present
```

M'he fixat que muntava l'ethernet en un altra número, així que he anat al '/etc/network/interfaces' i he canviat el eth0 per ethX (el que fos en aquell moment). Després he fet un "sudo /etc/init.d/networking restart" i ja funcionava.

Per suposat, al rearrancar tornem a la situació inicial xD

Posteriorment he instal·lat el kernel generic, i utilitzant-lo ja, he instal·lat el KDE4 (escrivint des de dins d'ell en aquests moments).

Ara al reiniciar tinc internet, però el problema que he posat del dmesg persisteix. El que passa és que el kde deu fer dinàmicament el que feia jo manualment jeje.

Cada cop que reinicio sembla que, si abans de reiniciar tenia ethX, al reiniciar tinc ethX+1.


Més informació:

"lspci | grep Ethernet":
```
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
```

"lsmod | grep eth":
```
forcedeth              51980  0
```

---

### Post by pespin on 2008-05-01
Söc tan bó que em responc a mi mateix... he trobat la resposta en un bug del launchpad: [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/153727]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/153727")

> 1. edit /etc/udev/rules.d/70-persistent-net.rules

2. remove all the existing entries and add a new one, something like

SUBSYSTEM=="net", DRIVERS=="forcedeth", NAME="eth0"

Al reiniciar ja no fa coses rares al forçar sempre que ho munti igual. Ara, el problema inicial en veritat de cara als desenvolupadors segueix sent-hi segons el dmesg:

"dmesg | grep eth":
```
[   17.371914] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   17.372296] forcedeth 0000:00:07.0: Invalid Mac address detected: 79:2a:e0:8f:13:00
[   17.372299] forcedeth 0000:00:07.0: Please complain to your hardware vendor. Switching to a random MAC.
[   17.891982] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x20 @ 1, addr 00:00:6c:9c:b4:1b
[   17.891987] forcedeth 0000:00:07.0: highdma pwrctl mgmt timirq lnktim msi desc-v3
[   18.768526] Driver 'sr' needs updating - please use bus_type methods
[   19.577610] Driver 'sd' needs updating - please use bus_type methods
[   77.949513] eth0: no IPv6 routers present
```

---

