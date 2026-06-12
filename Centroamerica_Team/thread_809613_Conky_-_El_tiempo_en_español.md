---
title: "Conky - El tiempo en español"
date: 2008-05-27
forum: Centroamerica Team
---

### Post by Bruce M. on 2008-05-27
Conky - El tiempo en español para Buenos Aires (ARBA0009)

[CENTER][[IMG]http://img138.imageshack.us/img138/7382/3conkysij1.th.jpg[/IMG]](http://img138.imageshack.us/my.php?image=3conkysij1.jpg)[/CENTER]

Usted puede verlo [aquí - #216]("http://ubuntuforums.org/showpost.php?p=5053708&postcount=216")

Localización - para cambiar el código de localización para su ciudad el URL siguiente se debe utilizar, substituye NORWICH por su ciudad:

[http://xoap.weather.com/search/search?where=NORWICH](http://xoap.weather.com/search/search?where=NORWICH)

Cambie "ARBA0009" para el código que usted encuentra en el URL arriba en "conkyForecast.py".

La fuente de weather.ttf y de arrows.ttf [está aquí]("http://ubuntuforums.org/showthread.php?t=760527"). La fuente de moon.ttf [está aquí]("http://www.dafont.com/moon-phases.font")

La escritura del email [es aquí]("http://ubuntuforums.org/showpost.php?p=4962990&postcount=154") si usted la quiere.

Que usted tenga un buen día
Bruce

PD: Pardon mi español, yo están utilizando [Yahoo! Babelfish]("http://ca.babelfish.yahoo.com/translate_txt") a traducir de inglés-español.

---

### Post by eivar on 2008-05-27
Hi Bruce M.
Thanks for share this with us.

greetings

---

### Post by Bruce M. on 2008-05-27
> **eivar said:**
> Hi Bruce M.
Thanks for share this with us.

greetings

De nada, no es mi trabajo solamente, muchos ha trabajado en esto.
Estoy aprendiendo español de modo que sea porqué hice esto.

Have a nice day.
Bruce

---

### Post by Bruce M. on 2008-05-28
Hola gente....

[Hay ayuda paso a paso aquí en español.]("http://ubuntuforums.org/showpost.php?p=5063066&postcount=6")

---

### Post by eivar on 2008-05-28
Hola a todos, como bien nos dice Bruce M. se puede obtener el código Zip cambiando en la siguiente dirección:
[> http://xoap.weather.com/search/search?where=NORWICH]("http://xoap.weather.com/search/search?where=NORWICH")
NORWICH por la ciudad que te interesa pero para obtener correctamente los datos de  la Ciudad de Panamá se debe colocar **Panama city**, así la dirección anterior nos quedaría de la siguiente forma:
[> http://xoap.weather.com/search/search?where=Panama%20city]("http://xoap.weather.com/search/search?where=Panama%20city")

De cualquier forma les dejo el código Zip de *Ciudad de Panamá, Panamá*: ```
PMXX0004
```Adjunto una  captura de pantalla de mi escritorio :guitar:
[URL="http://ubuntuforums.org/attachment.php?attachmentid=71998&stc=1&d=1212036245"]
[/URL]

---

### Post by Bruce M. on 2008-05-29
> **eivar said:**
> De cualquier forma les dejo el código Zip de *Ciudad de Panamá, Panamá*: ```
PMXX0004
```Adjunto una  captura de pantalla de mi escritorio :guitar:
[URL="http://ubuntuforums.org/attachment.php?attachmentid=71998&stc=1&d=1212036245"]
[/URL]

Hola, este código produjo los resultados en la imagen atada. Veo errores en su imagen. Usted necesitará cambiar la fuente.

Nota: He cambiado el Lat: y Long: para emparejar la ciudad de Panamá en el código después de hacer la imagen.

```
TEXT
${color0}${hr 1}$color
${color1}Desde:$color Panamá City, Panamá
${color1}Lat: ${color2}8°58'N          ${color1}Long: ${color2}79°32'W$color
${voffset 5}${color2}${font Zekton:size=10}Hoy:$font ${color3}${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=PMXX0004 --datatype=CC}${alignr 2}${color7}ST: ${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=PMXX0004 --datatype=LT}$color
${color3}${font Weather:size=50}${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=PMXX0004 --datatype=WF}$font$color
${alignr 50}${voffset -55}${font Zekton:size=25}${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=PMXX0004 --datatype=HT}$font
${alignc 20}${voffset -30}${font Arrows:size=20}${color4}${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=PMXX0004 --datatype=BF}$color$font
${alignc 10}${voffset 5}${color4}Viento: ${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=PMXX0004 --datatype=WS}$color
${color1}Humedad: ${color3}${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=PMXX0004 --datatype=HM}${alignr 2}${color1}Precipitación: ${color3}${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=PMXX0004 --datatype=PC}$color
${alignc}${color1}Presión: ${color3}${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=PMXX0004 --datatype=BR} - ${color3}${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=PMXX0004 --datatype=BD}$color
${color4}${hr}$color
${color1}Salida del Sol: ${color3}${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=PMXX0004 --datatype=SR}${alignr 2}${color1}Ocaso: ${color3}${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=PMXX0004 --datatype=SS}$color
${voffset 15}${color1}Luna:${color4}${alignr 2}${color3}${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=PMXX0004 --datatype=MP}$color
${voffset -20}${offset 80}${color4}${font moon phases:size=20}${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=PMXX0004 --datatype=MF}$font$color
${color0}${hr}$color
```

¿Cómo es la traducción española de BabelFish?
Have a nice day
Bruce

---

### Post by eivar on 2008-05-29
Thanks.
I have checked the data from Panama seems that the latitude and longitude that you have are not correct.
[http://www.mapsofworld.com/lat_long/panama-lat-long.html](http://www.mapsofworld.com/lat_long/panama-lat-long.html)

And by the way, BabelFish translation's is good.

---

### Post by Bruce M. on 2008-05-29
> **eivar said:**
> Thanks.
I have checked the data from Panama seems that the latitude and longitude that you have are not correct.
[http://www.mapsofworld.com/lat_long/panama-lat-long.html](http://www.mapsofworld.com/lat_long/panama-lat-long.html)

And by the way, BabelFish translation's is good.

But I copied it from your image above.
Your English is not BabelFish is it.  :)

---

### Post by srlinux on 2008-07-07
imagenes de mi conky XD espero les guste :)


[IMG]http://img399.imageshack.us/img399/105/pantallazogl2.png[/IMG]

[IMG]http://img59.imageshack.us/img59/1918/pantallazo1gm2.png[/IMG]

[IMG]http://img396.imageshack.us/img396/8232/pantallazo2nd1.png[/IMG]


despues pongo mas :lolflag:

---

### Post by Bruce M. on 2008-07-07
> **srlinux said:**
> imagenes de mi conky XD espero les guste :)

despues pongo mas :lolflag:

¿Qué fuente usted utilizó para la primera imagen?

¿Puede usted demostrarnos el código?

Gracias, que tengas un buen día
Bruce

---

### Post by srlinux on 2008-07-07
hola Bruce M. bueno primero tienes q descargar las fuetes aqui esta el link [http://www.mediafire.com/?jg3hd13l3ng]("http://www.mediafire.com/?jg3hd13l3ng") despues lo pasas al directorio /usr/share/fonts/truetype

aqui esta una linea del mio para  lo veas 

${font GothicFlames:style=Bold:pixelsize=20}Srinux Desktop ${font Snap.se:size=8}${hr 1}

:) suerte por sierto me puedes desir como conseguir los diestros de ubuntu 8.04 quiero tener los discos XD porfa

---

### Post by srlinux on 2008-07-07
aqui puedes descargar mas fuentes [http://www.dafont.com/](http://www.dafont.com/)

chau

---

### Post by Bruce M. on 2008-07-07
> **srlinux said:**
> hola Bruce M. bueno primero tienes q descargar las fuetes aqui esta el link [http://www.mediafire.com/?jg3hd13l3ng]("http://www.mediafire.com/?jg3hd13l3ng") despues lo pasas al directorio /usr/share/fonts/truetype

aqui esta una linea del mio para  lo veas 

${font GothicFlames:style=Bold:pixelsize=20}Srinux Desktop ${font Snap.se:size=8}${hr 1}

:) suerte por sierto me puedes desir como conseguir los diestros de ubuntu 8.04 quiero tener los discos XD porfa

> **srlinux said:**
> aqui puedes descargar mas fuentes [http://www.dafont.com/](http://www.dafont.com/)

chau


Gracias, me encanta esa fuente.

Ahora tengo un problema, no entiendo lo que usted significa:

> suerte por sierto me puedes desir como conseguir los diestros de ubuntu 8.04 quiero tener los discos XD porfa

> Babel Fish - Spanish-English:
luck by sierto you can desir to me as to obtain the matadors of ubuntu 8,04 I want to have discs XD porfa

Babel Fish: Si usted puede explicar mejor, ayudaré.

Me: Si podes explicar mejor, voy a ayduarte. :)

Have a nice day.
Que tengas un buen día.
Bruce

---

### Post by srlinux on 2008-07-07
descuida ya solucione lo de la pregunta de los disco XD gracias de todas formas
yo tengo los diestros descargados de la pagina pero queria los discos q dan pero ya me los mandaron Xd ahora toca esperar los pedi por medio del shipit

---

### Post by Bruce M. on 2008-07-07
> **srlinux said:**
> descuida ya solucione lo de la pregunta de los disco XD gracias de todas formas
yo tengo los diestros descargados de la pagina pero queria los discos q dan pero ya me los mandaron Xd ahora toca esperar los pedi por medio del shipit

ahh, OK.
Suerte

Bruce

---

### Post by srlinux on 2008-07-07
por que no usan el canal irc nunk hay nadie orita estoy en el canal XD me la paso en el ubuntu-es por q si me meto enel ubuntu-pa parec el mismo desierto jajajja hay q animar mas a las personas a ver si entran

---

### Post by Bruce M. on 2008-07-08
> **srlinux said:**
> por que no usan el canal irc nunk hay nadie orita estoy en el canal XD me la paso en el ubuntu-es por q si me meto enel ubuntu-pa parec el mismo desierto jajajja hay q animar mas a las personas a ver si entran

No uso IRC, y mi idioma no es español. Soy canadiense.
Pero gracias.
Bruce

---

