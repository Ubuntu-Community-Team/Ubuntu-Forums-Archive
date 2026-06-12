---
title: "problem hp pavilio dv6 6180la"
date: 2013-01-03
forum: Colombia Team - Colombia
---

### Post by leyes1989 on 2013-01-03
PC portátil de entretenimiento HP Pavilion dv6-6180la 
Número de Serie:   5CH1382ARY 
Número de Producto:   A2U69LA 

el problema consiste en que recientemente me he instalado el ubuntu en su ultima version de la pagina, me he enamorado de su entorno, sencilles y facilidad de uso, su rapidez y funcionamiento pero he tenido una serie de problemas con la tarjeta grafica y el rendieminto de mi portatil los pronlemas son los siguientes:

se recalienta mucho, y el ventilador permanece en funcionamiento
la tarjeta de video no la reconoce
el brillo no se puede manejar es decir no oscurece ni aumenta esta fijo en su maximo lo cual
me descarga sumado el constante funcionamiento del ventilador y recalenatamiento termina por darme menos
de media hora de uso

la verdad el problema de la tarjeta no es tan grave pues anque quiero desprenderme del windows es obio que lo necesito para jugar o pues si me ayudan con ese problema tambien seria perfecto la verdad no quiero saber de windows nunca mas en mi vida.

encuanto al uso de mi portatil si extraño drives para que funcione por ejemplo el lector de huellas, o el manejo de graficos intercambiables les dejo la version de mi tarjeta es una
radeon hd 6770m

---

### Post by leyes1989 on 2013-01-03
bueno el problema del brillo ya le he dado solucion pero es importante tener en cuenta que dependio de buscar primero que todo la version que se esta usando de ubuntu y el tipo de portatil ya que hay una gran cantidad de soluciones diferentes en mmi caso tengo un hp pavilion dv6 y utilizo ubuntu 12.04 bueno empezemos:

abrimos la terminal con ctrl+alt+t y tecleamos lo siguiente
*sudo gedit /etc/default/grub*

se nos abrira una nueva ventana, buscamos la linea que dice lo siguiente:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

y lo cambiamos de forma que quede asI:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"

guardamos los cambios y cerramos, volvemos de nuevo a la terminal y
escrivimos lo siguiente

sudo update-grub

esperamos esto es para actualizar y luego solo cerramos reiniciamos y listo.

con esto ya deberia de funcionarles los botones de control de brillo

en caso de que no les funciones les recomiendo dejar todo cual estaba abriendo nuevamente la terminal y dejando la linea que cambiaron nuevamente como estaba y probar alguna de las soluciones que plantean en el siguiente link:

[http://www.ubuntu-es.org/node/144451#.UOV9uVLFsUR](http://www.ubuntu-es.org/node/144451#.UOV9uVLFsUR)

---

