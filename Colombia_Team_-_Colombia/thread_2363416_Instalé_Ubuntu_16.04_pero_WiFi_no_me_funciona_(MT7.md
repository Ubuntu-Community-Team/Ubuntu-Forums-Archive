---
title: "Instalé Ubuntu 16.04 pero WiFi no me funciona (MT7630E)"
date: 2017-06-09
forum: Colombia Team - Colombia
---

### Post by andres69 on 2017-06-09
[COLOR=#111111][FONT=Liberation Serif]Saludos a todos y agradecimientos por toda su ayuda brindada.[/FONT][/COLOR]

[COLOR=#111111][FONT=Liberation Serif]Amigos, tengo un equipo Asus S301LA que compré en 2015, con Win 8.1 y atualicé a Win 10. Hace varios días le instalé un arranque dual con Ubuntu 16.04 LTS (Unity) con kernel 4.8.0-54-generic (x86_64). Lo demás funciona pero <b>no tengo acceso a Internet WiFi</b>.[/FONT][/COLOR]

[COLOR=#111111][FONT=Liberation Serif]El dispositivo es: **Mediatek MT7630E 802.11bgn Wi-Fi Adapter**[/FONT][/COLOR]

[COLOR=#111111][FONT=Liberation Serif]1. Al ejecutar ifconfig sólo me muestra el adaptador Ethernet para comunicación por cable y el lo.[/FONT][/COLOR]
[COLOR=#111111][FONT=Liberation Serif]2. Al ejecutar iwconfig me aparece:[/FONT][/COLOR]
```

[COLOR=#111111][FONT=&amp]root@ubuntu-pc:/home/atlas# iwconfig[/FONT][/COLOR]
[COLOR=#111111][FONT=&amp]enp2s0 no wireless extensions.[/FONT][/COLOR]

[COLOR=#111111][FONT=&amp]lo no wireless extensions.[/FONT][/COLOR][COLOR=#111111][FONT=Liberation Serif]
[/FONT][/COLOR]
```[COLOR=#111111][FONT=Liberation Serif]
[/FONT][/COLOR]
[COLOR=#111111][FONT=Liberation Serif]3. Al listar con lspci me aparece:[/FONT][/COLOR]
[COLOR=#111111][FONT=Liberation Serif]03:00.0 Network controller: MEDIATEK Corp. MT7630e 802.11bgn Wireless Network Adapter[/FONT][/COLOR]

[COLOR=#111111][FONT=Liberation Serif]4. Al ejecutar lshw me lista el dispositivo así:
[/FONT][/COLOR]```

[COLOR=#111111][FONT=Liberation Serif]*-network NO RECLAMADO[/FONT][/COLOR]
[COLOR=#111111][FONT=Liberation Serif]descripción: Network controller[/FONT][/COLOR]
[COLOR=#111111][FONT=Liberation Serif]producto: MT7630e 802.11bgn Wireless Network Adapter[/FONT][/COLOR]
[COLOR=#111111][FONT=Liberation Serif]fabricante: MEDIATEK Corp.[/FONT][/COLOR]
[COLOR=#111111][FONT=Liberation Serif]id físico: 0[/FONT][/COLOR]
[COLOR=#111111][FONT=Liberation Serif]información del bus: pci@0000:03:00.0[/FONT][/COLOR]
[COLOR=#111111][FONT=Liberation Serif]versión: 00[/FONT][/COLOR]
[COLOR=#111111][FONT=Liberation Serif]anchura: 32 bits[/FONT][/COLOR]
[COLOR=#111111][FONT=Liberation Serif]reloj: 33MHz[/FONT][/COLOR]
[COLOR=#111111][FONT=Liberation Serif]capacidades: pm msi pciexpress bus_master cap_list[/FONT][/COLOR]
[COLOR=#111111][FONT=Liberation Serif]configuración: latency=0[/FONT][/COLOR]
[COLOR=#111111][FONT=Liberation Serif]recursos: memoria:f7c00000-f7cfffff[/FONT][/COLOR]

```
[COLOR=#111111][FONT=Liberation Serif]5. Al listar los dispositivos con "hardinfo", a este no le aparece asociado ningún driver.[/FONT][/COLOR]

[COLOR=#111111][FONT=Liberation Serif]He buscado mucho en diferentes blogs, foros, etc. y apliqué algo, que no funcionó y es lo siguiente:[/FONT][/COLOR]
```

[COLOR=#111111][FONT=Liberation Serif]sudo su[/FONT][/COLOR]
[COLOR=#111111][FONT=Liberation Serif]apt-get update[/FONT][/COLOR]
[COLOR=#111111][FONT=Liberation Serif]apt-get install linux-headers-generic[/FONT][/COLOR]
[COLOR=#111111][FONT=Liberation Serif]apt-get install git [/FONT][/COLOR]
[COLOR=#111111][FONT=Liberation Serif]apt-get install dkms [/FONT][/COLOR]
[COLOR=#111111][FONT=Liberation Serif]apt-get install build-essential  [/FONT][/COLOR]
[COLOR=#111111][FONT=Liberation Serif]git clone [https://github.com/neurobin/MT7630E.git](https://github.com/neurobin/MT7630E.git)[/FONT][/COLOR]
[COLOR=#111111][FONT=Liberation Serif]cd MT7630E/[/FONT][/COLOR]
[COLOR=#111111][FONT=Liberation Serif]chmod +x install test uninstall[/FONT][/COLOR]
[COLOR=#111111][FONT=Liberation Serif]sudo make dkms[/FONT][/COLOR]

```

[COLOR=#111111][FONT=Liberation Serif]Con esto ya apareció el controlador mt7630e asociado al dispositivo, pero no se arregló el WiFi ni reiniciando el servicio de redes ni el PC. El ifconfig y el iwconfig continuaron iguales que al principio. Me tocó remover lo que hice con dkms y ya no se qué más hacer, porque leí que el NDISwrapper sólo funciona con controladores diseñados para Win XP y este controlador vino para Win 8 y Win 8.1.[/FONT][/COLOR]

[COLOR=#111111][FONT=Liberation Serif]Estoy tratando de no abandonar el impulso por tener Ubuntu, por lo que pido su gran ayuda, estimados amigos. Quiero no seguir siendo Windows-dependiente. Estudio Ing. de Sistemas (Colombia) y quiero promover Linux en mi entorno. De antemano muchas gracias.[/FONT][/COLOR]

[COLOR=#111111][FONT=Liberation Serif]Andres.[/FONT][/COLOR]

---

