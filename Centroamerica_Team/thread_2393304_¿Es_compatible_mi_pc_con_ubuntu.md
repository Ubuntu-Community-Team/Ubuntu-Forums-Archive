---
title: "¿Es compatible mi pc con ubuntu?"
date: 2018-06-01
forum: Centroamerica Team
---

### Post by kembus20 on 2018-06-01
Hola a todos,  hace mucho que no me muevo por el mundo de linux y ubuntu. Y tampoco recuerdo si alguna vez me presente por aqui.

Si no es asi, pues aqui estoy con ganas de probar con ubuntu de nuevo.

Pues bien mi pc tiene:

Cpu: Intel  Pentium 4 HT 3,20Ghz (procesador de 32bits)
Ram: 4Gb Ddr2
Disco Duro: 1Tb
Tarjeta Grafica: Nvidia Gforce 8600GT
Placa Base, MotherBoard, Mainboard: Asrock G41c-Gs R2.0

¿Que version de ubuntu podria probar?

¿Podria ver bien peliculas en calidad normal y youtube, sin tener que activar ninguna aceleracion ?

---

### Post by mörgæs on 2018-06-03
Hi, I hope it's OK to answer in English - better than no answer at least. 

Yes, your hardware looks compatible. I suggest that you try a live boot of X/Lubuntu 18.04 and see how it works.

---

### Post by kembus20 on 2018-06-18
> **mörgæs said:**
> Hi, I hope it's OK to answer in English - better than no answer at least. 

Yes, your hardware looks compatible. I suggest that you try a live boot of X/Lubuntu 18.04 and see how it works.

Gracias por responder a mi pregunta, y no te preocupes por utilizar el inglés. Aunque no entiendo del todo el idioma ingles, por lo que he podido entender al principio y luego gracias al traductor google translator, he podido entender del todo lo que me estabas diciendo.


Pues bien, como bien me decias, la version de Lubuntu 18.04 probando su version live, funcionó a la perfecccion en mi pc.


Me sorprendió que todo el pc funcionase bien, solo que hubo dos cosas que no me llegaron a gustar.


1º La resolución de la pantalla no era la adecuada, la resolucion maxima en lubuntu linux 1152 X 864, cuando en realidad deberia de ser resolucion maxima en windows 1366 X 798.


En lubuntu hice tests, con el driver libre de lubuntu y tambien con el driver privativo de nvidia, en ninguno de las dos opciones la resolucion no pasaba de 1152 X 864.


La consecuencia era que todas las ventadas se veian deformadas a lo ancho, la experiencia no era del todo buena.


Al final no pude solucionar nada en relacion de la resolucion de la pantalla.


2º Tengo una antigua impresora canon lbp 810 que despues de probar varias configuraciones, no ha funcionado.

--------------------
google translator
--------------------

Thank you for answering my question, and do not worry about using English. Although I do not fully understand the English language, from what I could understand at the beginning and then thanks to the translator Google translator, I was able to fully understand what you were saying.


Well, as you told me, the version of Lubuntu 18.04 testing its live version, worked perfectly on my pc.


I was surprised that all the pc worked well, only that there were two things that I did not like.


1º The resolution of the screen was not adequate, the maximum resolution in lubuntu linux 1152 X 864, when in reality it should be maximum resolution in windows 1366 X 798.


In lubuntu I did tests, with the free driver of lubuntu and also with the privative driver of nvidia, in neither of the two options the resolution did not exceed 1152 X 864.


The consequence was that all the windows were distorted in width, the experience was not entirely good.


In the end I could not solve anything in relation to the resolution of the screen.


2º I have an old printer canon lbp 810 that after trying several configurations, it has not worked.

---

### Post by mörgæs on 2018-06-18
Please run the command ```
xrandr -q
``` and post the results in CODE tags.

---

### Post by kembus20 on 2018-06-30
> **mörgæs said:**
> Please run the command ```
xrandr -q
``` and post the results in CODE tags.

lubuntu@lubuntu:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1152 x 864, maximum 8192 x 8192
DVI-I-1 connected primary 1152x864+0+0 (normal left inverted right x axis y axis) 410mm x 230mm
   1152x864      75.00* 
   1024x768      75.03    70.07    60.00  
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   640x480       75.00    72.81    66.67    59.94  
   720x400       70.08  
DVI-I-2 disconnected (normal left inverted right x axis y axis)

---

