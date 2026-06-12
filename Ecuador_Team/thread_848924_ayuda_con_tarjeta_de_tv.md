---
title: "ayuda con tarjeta de tv"
date: 2008-07-03
forum: Ecuador Team
---

### Post by gargoleor on 2008-07-03
Saludos compañeros

Necesito ayuda para poder instalar y hacer funcionar una tarjeta de tv en Kubuntu.

la tarjeta es segun el comando:

$ sudo lshw

description: Multimedia controller
                product: SAA7133/SAA7135 Video Broadcast Decoder
                vendor: Philips Semiconductors
                physical id: 1
                bus info: pci@0000:03:01.0
                version: d1
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=saa7134 latency=64 maxlatency=38 mingnt=15 module=saa7134

He tratado instalando programas para ver tv-cable tales como: tvtime, xawtv .......... y no he podido hacer que se vea por ninguno. He googleado y no he encontrado nada al respecto (no seria nada raro que no supiese buscar). Asi pues que recurro a vuestros conocimientos al respecto

Alguna sugerencia?

Gracias

---

### Post by estebandid0 on 2008-07-04
revisate estos links

[http://www.google.com.ec/search?hl=es&q=SAA7133%2FSAA7135+Video+Broadcast+Decoder+ubuntu&btnG=Buscar+con+Google&meta=]("http://www.google.com.ec/search?hl=es&q=SAA7133%2FSAA7135+Video+Broadcast+Decoder+ubuntu&btnG=Buscar+con+Google&meta=")

---

### Post by gargoleor on 2008-07-05
Gracias por tu respuesta, estebandid0.

Me sugirieron trabajar con un programa llamado KDETV. Lo he instalado, me captura los canales por cable, se ven dichos canales, pero no le funciona el audio. trabajare en este aspecto ahora. Pero YA PUEDO VER TV, porque desde que conoszo a linux, nunca habia podido hacerla funcionar

---

### Post by gargoleor on 2008-07-05
Al fin he podido hacer que funcione:popcorn:

Instale KDETV, escannee los canales y configure el sonido teniendo en cuenta que el sonido entra al pc desde la tarjeta por LINE.


Listo y solucionado:guitar:

Gracias

---

### Post by estebandid0 on 2008-07-05
genial, siempre es bueno poder compartir cuando resuelves algo, talvez podrías detallar más que es lo que hicisite o en que página buscar, de esa forma alguién que pudiera tener el mismo error lo puede resolver con mayor rapidez

---

### Post by gargoleor on 2008-07-08
Como ya comente, el proceso fue:

1 instalar Kdetv
2 escanear los canales (canales - asistente de canales) (seguir los pasos del asistente)
3 para el sonido (preferencias, configurar kdetv, sonido, en seleccionar el controlador para el mezclador, en la opcion configurar el mezclador) escoger elemento del mezclador: LINE
4 Aplicar
5 disfrutarlo
:guitar::popcorn::guitar:

---

### Post by joelpietersen on 2009-02-13
nice one here. thanks. :D

---

