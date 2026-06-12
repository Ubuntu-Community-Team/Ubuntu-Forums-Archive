---
title: "No es suspèn el portàtil"
date: 2008-02-25
forum: Catalan Team
---

### Post by Joan Marc on 2008-02-25
Hola,
Ja fa alguns dies que quan intento posar en mode suspens el portàtil, es queda de color negre (com si estigués en realitat en suspens), però ni el ventilador ni les llumetes que indiquen el Wifi i la bombeta no s'aturen, com ho fan quan està suspès, i no respon a res, l'única solució que queda és fer la salvatjada de parar-lo amb el botó.
He provat el que diuen en aquest [post]("http://ubuntuforums.org/showthread.php?t=676422&highlight=gutsy+suspend") ,però no m'ha funcionat :(.

Em podeu ajudar?
Gràcies!

---

### Post by papapep on 2008-02-25
Si no ens dius el model exacte del portàtil i versió d'Ubuntu instal·lada, no :-)

---

### Post by Joan Marc on 2008-02-25
:)
És un Asus F3JR, poso les característiques tècniques (tot i que no sé si és això el que demanaves papapep)
Especificaciones Técnicas

    * Procesador
    * Intel CORE 2 DUO T2350 (1.86 Ghz / 533 Mhz / 2MB L2)
    * Memoria RAM
    * 2 GB DDR2 SDRAM 533 Mhz (Máx. 2GB)
    * Disco Duro
    * 120GB SATA
    * CD/DVD
    * DVD±RW (+R DL) /DVD-RAM
    * Pantalla (Pulgadas)
    * 15.4" WXGA (1280x800)
    * Conectividad Ethernet - Fast Ethernet - Gigabit Ethernet - IEEE 802.11a/b/g - EDR - Módem
    * Sistema Operativo
    * Microsoft Windows Vista Premium :mad::mad:
    * Salida de vídeo / Procesador gráfico/ fabricante ATI Mobility Radeon X2300 External 128MB VRAM (DDRII VRAM*4) Hyper Memory: 384M with 1G System Memory / 896M with 2G System Memory
    * Placa principal / Tipo conjunto de chips Mobile Intel 945 PM Express
    * Interfaz proporcionada / Tipo 1x IEEE1394 (FIREWIRE / 4 PIN) - 1x Salida Audio (Auriculares) - 1x Micrófono - 1x Line-in -
    * 1x Módem (RJ-11) - 1x Red (RJ-45) - 4x USB High Speed 2.0 tipo A / 4 PIN - 1x VGA - 1x DVI -1x S-Video
    * Ranura suministrada / Tipo 1x Express Card - 2x Memoria
    * Lector de tarjetas / Tipo 4 in 1 Card Reader
    * Lector de tarjetas / Tarjetas de memoria flash compatibles (AB) MMC Card - SD - Mini SD - Memory Stick - Memory Stick
    * Pro /Duo - Memory Stick Duo - Memory Stick Pro Duo
    * Audio salida / Tipo Intel High Definition Audio, compatible con Sound Blaster Pro
    * Caja (chasis) / Dispositivos incorporados (AB) Altavoces stereo Integrados (1.5W) , Antena LAN inalambrica
    * Audio entrada / Tipo Microfono Incorporado - Line in
    * Módem / Tipo Fax / módem 56Kbps
    * Módem / Protocolos y especificaciones ITU V.90 - ITU V.92
    * Teclado / Localización y diseño Standard 83 Teclas + 5 Función rapida (Power4 Gear +, Bluetooth, Wireless, Splendid, Instant Fun Plus)
    * Batería / Tecnología Ion-Litio 6 celdas (4800mAh)
    * Baterï¿½a / Duraciï¿½n (hasta) 3 Horas (Aprox.)
    * Dimensiones y peso / Altura 28mm - 40.5mm
    * Dimensiones y peso / Anchura 365mm
    * Dimensiones y peso / Profundidad 269.5mm
    * Dimensiones y peso / Peso
    * 2.95 Kg    
    * Sistema / Dispositivos de seguridad BIOS Booting / Password de protección de usuario HDD y cierre de seguridad -
    * Cierre Kensington
    * Cámara de portátil / Propiedades de cámara Webcam integrada
    * Cámara de portátil / Resolución del sensor 1.3 Megapixels

Tinc l'Ubuntu 7.10 Gutsy Gibbon, i la versió del Kernel és: ```
gami@gami:~$ uname -a
Linux gami 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux
```

Gràcies!

---

### Post by Joan Marc on 2008-02-28
ah! per cert, tinc la versió de 32bits

---

### Post by papapep on 2008-02-28
Sembla que pugui ser un problema entre el controlador de la gràfica i el model del portàtil...: [http://terenzioberni.blogspot.com/2007/10/ubuntu-710-gusty-gibbon-on-asus-z53jr.html](http://terenzioberni.blogspot.com/2007/10/ubuntu-710-gusty-gibbon-on-asus-z53jr.html)

---

### Post by Joan Marc on 2008-02-28
Si que hi deu tenir alguna cosa a veure.
He des habilitat el controlador restringit ATI (que el tenia amb una resolució de 1280x800) i l'he posat al màxim que permès sense el controlador (1024x768 ).
Després de fer això, l'he intentat suspendre, i s'ha sospès amb normalitat, però a l'hora de tornar a posar-lo en marxa (polsant qualsevol tecla) es queda engegat però amb la pantalla negra i sense possibilitat de fer res més que apagar-lo pel botó.
La veritat és que no sé què fer, fins i tot, he provat de treure això:
```
# defoptions=quiet splash [COLOR="Red"]vga=794[/COLOR]
```

Que ho havia posat per intentar solucionar el fil de "Problemes iniciant l'ubuntu".

No ho sé, però crec que la marca Asus i les targetes ATI, i l'Ubuntu no lliguen gaire bé, ja que tot el que són gràfics, els resultats són bastant deficients...:(

Bé, si no hi ha solució, prefereixo la resolució el controlador ATI de 1280x800, tot i que la funció de suspens també la feia servir molt.

Salutacions.

---

### Post by pablinsfc on 2008-02-29
Recentment, un professor nostre que també usa ubuntu ens va comentar que no podia suspendre sessió perquè no li recuperava, es penjava, i havia de reiniciar. Va deixar anar el comentari de que ubuntu no gestionava bé el tema de suspendre/hibernar.

És cert això o és problema de controladors i targetes gràfiques? Sincerament, no em vagi acabar de creure gaire que fos problema del  SO...

Salut!

Pau.

---

