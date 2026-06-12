---
title: "conky + datos do tempo Meteogalicia"
date: 2009-09-05
forum: Galician LoCo Team
---

### Post by pikamoku on 2009-09-05
son un usuario común do Ubuntu. Teño posto varios Conky no escritorio e un deles ten un script deses que dan datos meteorolóxicos.
Normalmente os scripts que aparecen nos manuais pois pillan os datos de yahoo, microsoft,.... pero en galicia temos Meteogalicia que proporciona, actualizados cada 20' , os datos das estacións meteorolóxicas espalladas pola nosa terra. E son un lote: [http://www.meteogalicia.es/galego/observacion/estacions/estacions.asp](http://www.meteogalicia.es/galego/observacion/estacions/estacions.asp)
Se vives, por exemplo en Fisterra, seguramente non teña moito que ver cos datos que pode ter a estación de Santiago ou Coruña.

Esta intro é para dicir que fixen un popurrí de varios scripts para que no conky apareza esa información.

Mellor que facer un copy/paste dos scritps, fago este anuncio e ireino editando con **explicación pormenorizada e capturas de pantaia**

Creo que este LoCo é o lugar axeitado para contribuir. Ahí vai (Ver.1.0)

Vamos a Sistema->Administración->Xestor de paquetes Synaptic instalamos **w3m** e **conky** (se é que aínda non o están. Vale igoal ```
sudo apt-get install w3m conky
```.
w3m é un "navegador" de internet a través do Terminal. Leerá os datos de Meteogalicia.

nun terminal, creamos a carpeta que conterá o script (por ter ordenado o asunto, podela usar para meter outras cousas) e o script.
```
mkdir .scripts
cd .scripts
sudo gedit meteo.sh
```

copia e pega nel

> #!/bin/sh
## datos meteoroloxicos de meteogalicia
#arquivo creado
arquivo=~/letura
#estación de medida
#exemplo: Celanova  10112
estacion=10112

##  primeiro imos á paxina de meteogalicia
## e collemos os datos a partir de "Instante da lectura"
## e metemolo no arquivo "letura" (situado en home)
w3m http://www.meteogalicia.es/galego/observacion/estacions/estacionsActual.asp?Nest=$estacion | grep -A28 "Instante da lectura" > $arquivo

## e vamos definindo os parámetros que interesan dentro dese arquivo creado
#temperatura actual
temp=`cat $arquivo | grep "Temperatura Media" | cut -b 37-44`
#humidade relativa media do aire
humid=`cat $arquivo | grep "Humidade Relativa" | cut -b 37-41`
# vento
vento=`cat $arquivo | grep "Velocidade do Vento" | cut -b 37-54`
dirvento=`cat $arquivo | grep "Dirección do Vento" | cut -b 37-50`
# choiva
choiva=`cat $arquivo | grep "Choiva" | cut -b 1-25`

## e escribimolos
echo Temperatura: $temp
echo Humidade: $humid
echo Vento: $vento $dirvento
echo $choiva

explicase nas liñas comentadas o que fai cada anaco.

dámoslle permiso de execución ó meteo.sh

```
chmod +x /home/USUARIO/.scripts/meteo.sh
```

Imos á web de Meteogalicia para saber o CODIGO DA ESTACIÓN QUE NOS INTERESA:
 Clicas no listado de estacións, buscas a que queres, entras na súa info e miras na barra de direccións do teu navegador buscando o anaco **Nest=**:
[http://www.meteogalicia.es/galego/observacion/estacions/estacionsActual.asp?Nest=10112](http://www.meteogalicia.es/galego/observacion/estacions/estacionsActual.asp?Nest=10112)  
O número 10112 é o que nos interesa para poñer no código de *meteo.sh*

Abrimos o arquivo de configuración de conky
```
sudo gedit /etc/conky/conky.conf
```

copiamos e pegamos o seguinte
> # Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048
## anclado ó escritorio
background yes
# Update interval in seconds
update_interval 2

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
#own_window_type desktop
own_window_type override
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 220 0
maximum_width 220

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 5

# border width
border_width 0

# Default colors and also border colors
default_color white
#default_shade_color black
#default_outline_color white
own_window_colour white

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 35
gap_y 50

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none


TEXT
${voffset 4}O TEMPO en Celanova ${hr 2}
${voffset 4}${execi 300 /home/USUARIO/.scripts/meteo.sh }

O que está despois  de TEXT é o que realmente escribe a información. O resto é configuración gráfica.
Substitúe **Celanova**  polo nome do sitio onde está a estación.
Substitúe **USUARIO** polo nome de usuario da túa sesión (ou a ruta completa ó script que debe executar.

se xa tes un conky rulando pois copias/pegas o que está dentro de TEXT.


Executamos conky con arquivo de configuración creado.

```
conky -c /etc/conky/conky.conf
```

se tes varios conkys é necesario o parámetro -c que indica á ruta ó conky concreto que queres ter.

Se todo foi ben, verás esto:
[[IMG]http://img193.imageshack.us/img193/4286/fondoconky.th.jpg[/IMG]](http://img193.imageshack.us/img193/4286/fondoconky.jpg/)

**se non se ve** o conky no escritorio:
 mira o que se pon no terminal dende onde o lanzaches por se tes problemas de permisos, rutas incorrectas ou che falta algo.

Podes preguntar neste mesmo fío.

Xa sei que hai outros xeitos e a sintase pode non ser moi ortodoxa, pero é o que hai :P

Espero que vos sirva ;)

[COLOR="Red"]**NOTAS**[/COLOR]

1.
para que funcione fai falta conexión a internet. Para evitar problemas metemoslle un if

> ${if_existing /proc/net/route eth0}

${voffset 4}O TEMPO en Celanova ${hr 2}
${voffset 4}${execi 300 /home/USUARIO/.scripts/meteo.sh }
${endif}
sendo **eth0** o nome da interface de rede coa que te soes conectar a internet. Pódelo saber poñendo nun terminal

> ifconfig

onde verás o nome e configuración das interfaces de rede (wlan0, rausb0, wlan1, ppp0, ...)

2. a páxina de meteogalicia da máis información da que poño neste howto, engadir ou quitar datos é cuestión de editar *meteo.sh*
para ver TODOLOS datos que envía podes facer nun terminal
> cat letura
co que aparece o contido do arquivo onde volcamos os datos.
3. 
se tes problemas co arquivo *letura*, pois creas un arquivo baldeiro con ese nome, no HOME, e daslle permisos para que o lea e escriba sen problema
> gedit letura
gardas> 
sudo chmod 775 letura
4.
o conky hai que engadilo ó inicio do sistema para que se cargue automáticamente cada vez que inicias sesión.
5.
non lle podo agradecer a meteogalicia máis que a información **sexa pública**. Pois a sinxelas consultas técnicas (cómo tiñan organizada a información, refresco da  info,...) non me fixeron caso ningún.

---

### Post by felipexil on 2009-09-07
Paréceme unha idea moi boa (en canto teñas o titorial, se queres créoche unha conta na web de [ubuntuengalego.org]("http://www.ubuntuengalego.org") para que tamén quede alí unha copia).

---

### Post by pikamoku on 2009-09-07
xa vou eu por alí  ;)

edito:

pero si veño dalí¡¡¡  :D  :D  Non me rexistrei pero deille a *Foro* e parei neste.

Sí, creame unha conta e por favor díme como debe actuar para deixar a miña colaboración

Saúdos.

---

### Post by felipexil on 2009-09-07
> **pikamoku said:**
> xa vou eu por alí  ;)

Sí, creame unha conta e por favor díme como debe actuar para deixar a miña colaboración




Tés que ir [http://ubuntuengalego.org/rexistrate-aqui]("http://ubuntuengalego.org/rexistrate-aqui") e crear unha conta. Logo avísame para que che dea permisos

P.S: O *hosting* non bota moi lonxe, así que a páxina seguramente che vaia lenta... de momento só me queda pedir paciencia :(

---

