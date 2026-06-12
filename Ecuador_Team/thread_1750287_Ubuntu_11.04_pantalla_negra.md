---
title: "Ubuntu 11.04 pantalla negra"
date: 2011-05-05
forum: Ecuador Team
---

### Post by jmbarberan on 2011-05-05
Hola a todos

He instalado ubuntu 11.04 en mi pc la instalacion se ha realizado sin novedad pero una vez que apague la pc normalmente al volver a encenderla ahora la pantalla parece no recibir señal esto digo por que el sonido se escucha cuando inicia la pc e incluso si pulso ENTER y digito mi contraseña pareceria que ubuntu esta iniciando asi mismo suena la musica de inicio pero no se ve nada.

En la misma pc en otra partición del tengo instalado ubuntu 10.04 y funciona a la perfeccion.

mi pc es una Portatil Acer Aspire 4736z 
Intel Dual Core 2.0
RAM 4 gb
Gráficos Intel Corporation Mobile 4 Series Chipset Integrated

¿Alguien me puede explicar que pasa y/o como se soluciona? :confused:

Saludos

Martin

---

### Post by itahn on 2011-06-14
Ojo: esta solucion la obtube de alpizar84 asi es que el credito es de el que me dio la solucion yo solamente la copie y la pegue para que lo intentes y que trates de solucionarlo...
Debo tambien agregar que cuando la pantall negra me aparecio solamente fue en una de los grubs que tenia, esto es que tenia en grub cuatro opciones para escoger correr ubuntu 11.04 y en las primeras dos opciones de grub la pantalla era completamente negre, pero en las ultimas dos opciones de grub podia ver ubuntu semi normal, asi es que suerte con la solucion.... saludos...


Hola a todos he solucionado mi problema siguiendo los pasos:

Primero abrimos una terminal, y pegamos el siguiente comando:

lspci | grep VGA

esto nos va a arrojar una linea como la siguiente:

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)

aqui en lo que nos debemos fijar es en los numeros que estan antes de VGA en mi caso 00:02.0

posteriormente pegamos esto en la terminal

gedit ./backlight_d.sh

esto nos abrira una ventana, generalmente en blanco, ahi pegaremos lo siguiente:

#!/bin/sh
old_b='0';
while :
do
b=`cat /sys/class/backlight/acpi_video0/brightness`;
if [ $old_b != $b ]; then
old_b=$b
if [ $b = '0' ]; then
setpci -s 00:02.0 F4.B=-10
elif [ $b = '9' ]; then
setpci -s 00:02.0 F4.B=0
elif [ $b != '0' -a $b != '9' ]; then
setpci -s 00:02.0 F4.B=-$b$b
fi
fi
sleep 0.5
done

EN esto que pegamos, en lo que nos debemos de fijar es que despues de la linea que dice setpci -s el numero sea el que les aparecio a ustedes en sus computadoras, una vez que este asi, guardamos y cerramos.

Posteriormente estando de nuevo en terminal accedemos como root. Para los que no saben como aqui una breve explicacion.
Primero definimos una contraseña de root, con el comando

sudo passwd

nos pedira una contraseña, escribimos la que sea, y nos pide que la reescribamos, asi que eso hacemos. Una vez con nuestra contraseña escribimos el comando

su

damos enter y pedira la contraseña

listo, estamos como superusuario o root.

bien, ahora si, pegamos el siguiente codigo que es para copiarlo en la carpeta deseada

cp ./backlight_d.sh /etc/

y despues este otro para hacerlo ejecutable

chmod +x /etc/backlight_d.sh

con esto hemos realizado el script,

ahora lo añadimos a la rc local pegando esto en la terminal

nano /etc/rc.local

esto nos pasara a formato nano, donde al ultimo podemos ver que dice exit 0, pues bien, justo en la linea anterior donde hay un espacio en blanco, pegamos esto:

nohup /etc/backlight_d.sh

y hemos terminado, solo queda guardarlo, precionando la tecla ctrl y la letra O como en Oscar, y dan enter, y para salir ctrl y X. En caso de que Ctrl y letra
O no funcionen para guardar, intenta Ctrl y 0 (cero)
reiniciamos y con esto debemos poder cambiar el brillo de nuestro ubuntu como se supone lo hacemos usualmente, espero haya quedado claro, lo puse lo mas sencillo posible para que no haya complicaciones, saludos a todos.

Fuente:

[http://www.taringa.net/posts/linux/5897510/_Solucion_---Cambio-de-brillo](http://www.taringa.net/posts/linux/5897510/_Solucion_---Cambio-de-brillo)...

[http://brionescl.blogspot.com/2011/04/ubuntu-1104-y-back-light-en-notebo](http://brionescl.blogspot.com/2011/04/ubuntu-1104-y-back-light-en-notebo)...

---

### Post by ruben_linux on 2011-06-18
probaste a acceder a la partición del linux que no ves, y modificar xorg.conf????

---

