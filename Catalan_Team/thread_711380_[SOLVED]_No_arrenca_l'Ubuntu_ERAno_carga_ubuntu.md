---
title: "[SOLVED] No arrenca l'Ubuntu ERA:no carga ubuntu"
date: 2008-02-29
forum: Catalan Team
---

### Post by tanques on 2008-02-29
Bones fa pocs dies he passat de win a linux tot molt be, a poc a poc , i bona lletra vaig instala un live ubuntu 7.10 i al final tot molt millor i el vaig instalar tres dies de experimentació sense tocar fitxers del sistema i reinicio el ordenador després de una actualització  comença a xequexar .despres de sortir alguns starting i ok...me parpadeija i  me surt aquest missatge:

Cannot launch graphical configuratión tool because display config-gtk is hot installed.

.Sorry, wit hout this tool  installed you must manually configure xorg

gracies.....

---

### Post by lluisanunez on 2008-02-29
Dóna'ns més informació: quina tarja gràfica tens, i quin sistema?

---

### Post by tanques on 2008-03-01
Hola :

yo creo que es un supratech avalon amd 64 nvidia geforce 6200,

pero para estar más seguros que comandos pongo para mirar exactamente el harware instalado al principio del inicio, 

gracias.

---

### Post by papapep on 2008-03-01
Per la gràfica fes un:

```
lspci |grep Display 
```

i enganxa aquí el resultat.

Pel tema de l'ordinador ens ho has de dir tu correctament.

Per cert, benvingut al fòrum d'Ubuntaires en català. Passa't pel fil de benvinguda i fes-nos cinc cèntims de qui ets :-)

---

### Post by tanques on 2008-03-01
Hola Papapep
escric desde un portatil perque al altre no passo d'aqu'i  per cert gracies, a on es el fil de benvinguts , que em passare més tard , es que estic amb la nena i vaig una mica depresa , fins ara
no se si es aixó lo que em demanes:, 

Usage: lspci [<switches>]
-v  Be verbose
-n  Show numeric ID's
-nn Show both textual and numeric ID's (names &numbers)  
-b   Bus-centric view (PCI addresses and IRQ's instead of those seen by
the CPU)
-x  Show hex-dump of the standard portion of config space
-xxx  Show hex-dump of the whole config space (dangerous ; root only):
-xxx Show hex-dump of the 4096-byte extended config space (root only)
-s [[[[<domain>]:] <bus>]:] [<slot>] [.[<func>]]   Show only devices in selected slots
-d  [<vendor>]: [<device>]           Show only selected devices
-t      Show bus tree
-m      Produce machine-readable output
-i  <file>       Use specified ID database instead of /usr/share/misc/pci.ids.gz
-D     Always show domain numbers
-M     Enable `bus mapping' mode (dangerous; root only)
-P <dir>   Use specified directory instead of /proc/bus/pci
-H <mode> Use direct harware access (<mode>  = 1 or 2)
-F <file>  Read configuration data from given file
-G           Enable PCI access debugging

---

### Post by tanques on 2008-03-01
Hola Papapep
escric desde un portatil perque al altre no passo d'aqu'i  per cert gracies, a on es el fil de benvinguts , que em passare més tard , es que estic amb la nena i vaig una mica depresa , fins ara
no se si es aixó lo que em demanes:, 

Usage: lspci [<switches>]
-v  Be verbose
-n  Show numeric ID's
-nn Show both textual and numeric ID's (names &numbers)  
-b   Bus-centric view (PCI addresses and IRQ's instead of those seen by
the CPU)
-x  Show hex-dump of the standard portion of config space
-xxx  Show hex-dump of the whole config space (dangerous ; root only):
-xxx Show hex-dump of the 4096-byte extended config space (root only)
-s [[[[<domain>]:] <bus>]:] [<slot>] [.[<func>]]   Show only devices in selected slots
-d  [<vendor>]: [<device>]           Show only selected devices
-t      Show bus tree
-m      Produce machine-readable output
-i  <file>       Use specified ID database instead of /usr/share/misc/pci.ids.gz
-D     Always show domain numbers
-M     Enable `bus mapping' mode (dangerous; root only)
-P <dir>   Use specified directory instead of /proc/bus/pci
-H <mode> Use direct harware access (<mode>  = 1 or 2)
-F <file>  Read configuration data from given file
-G           Enable PCI access debugging

---

### Post by lluisanunez on 2008-03-01
Tanques,
has de posar al terminal exactament el que et diu en Papapep. Copia-ho d'aquí i enganxa-ho al terminal per estar més segurs:
```
lspci | grep Display
```

---

### Post by tanques on 2008-03-01
hola gent

si lluisa i ha ho  fet, res la solució la he trobat a aquest enllaç [http://ubuntuforums.org/archive/index.php/t-200598.html](http://ubuntuforums.org/archive/index.php/t-200598.html),


he instalat un paquet gtk per nvidia  i solucionat, gracies per la comprenssió , a tu Lluisa per se la primera , i en papapep per la seva dedicació.
ens tornarem a forejar,

salutacions

---

### Post by menut on 2008-03-01
Com a últim pas, ja que aquest fil del fòrum està sol·lucionat, hauries de fer clic a:
[INDENT]Thread Tools > Mark this thread as solved[/INDENT]

Aquest menú el trobaràs amb una fletxa al costat dins d'aquest fòrum.

---

