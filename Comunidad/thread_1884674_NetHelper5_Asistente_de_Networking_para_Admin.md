---
title: "NetHelper5: Asistente de Networking para Admin"
date: 2011-11-21
forum: Comunidad
---

### Post by juancarlospaco on 2011-11-21
**Es un programa para Asistente de Networking para Admin.**

El primero en su estilo, como un prototipo,
una delgada capa de QT para que HTML5 flote Libre en el Escritorio

[IMG]https://lh3.googleusercontent.com/-iuYUxz0FQb4/TsmIwOTSoTI/AAAAAAAAA0s/FCunGAzO6mo/s640/nethelper3.jpg[/IMG]

[IMG]https://lh4.googleusercontent.com/-RWzCishDzk0/TsmJEuriiDI/AAAAAAAAA00/Jqr4RTq0_9w/s640/nethelper1.jpg[/IMG]

[IMG]https://lh5.googleusercontent.com/-0WawB9zcqig/TsmJOfAxvGI/AAAAAAAAA08/aH0s1SPPvlE/s640/nethelper2.jpg[/IMG]

Pero ademas funciona..., 
y es util para los que les da fiaca los Calculos de Redes:

[LIST]
[*]Calculador de Subnetting C.I.D.R.
[*]Conversor de Mascara de Red Decimal a Bits
[*]Conversor de Mascara de Red Bits a Decimal
[*]Calculador de Mascara de Red segun Cantidad de Host requeridos
[*]Conversor de Direcciones IP de Decimal a Binario y Hexadecimal
[*]Conversor de Direcciones IP de Hexadecimal a Binario y Decimal
[*]Calculador de Wildcards Decimales
[*]Calculador de Mascara de Red hacia Cantidad de Direcciones IP Usables
[*]Conversor Multiple de Binario / Decimal / Hexadecimal
[*]Conversor de Hexadecimal a Binario
[*]Rangos de direcciones IP de Multicast / Privadas / Especiales (RFCs)
[*]Rangos de direcciones IP Comunes Standard (no-RFCs)
[*]Generador de Passwords Random Configurable (para Routers y Switchs)
[/LIST]

y la mejor feature, es Libre :)

Pesa 18Kb, Python,
pensado para Ubuntu (usa la Ubuntu-Font-Family),
resolucion minima recomendada 800 X 600 Pixeles,
CTRL + Q es Salir, No necesita Internet, 100% Desktop.


```

[http://tecnicoslinux.com.ar/livecd/nethelper5_1.0_all.deb]("http://tecnicoslinux.com.ar/livecd/nethelper5_1.0_all.deb")

```

---

### Post by mama21mama on 2011-11-21
Hola,

bajando....

edito:
lubuntu 11.10 salio esto

> mama@zeuza:~/Descargas$ sudo dpkg -i *.deb
Seleccionando el paquete nethelper5 previamente no seleccionado.
(Leyendo la base de datos ... 251830 ficheros o directorios instalados actualmente.)
Desempaquetando nethelper5 (de nethelper5_1.0_all.deb) ...
dpkg: problemas de dependencias impiden la configuración de nethelper5:
 nethelper5 depende de libqtwebkit-dev (>= 2.0); sin embargo:
  El paquete `libqtwebkit-dev' no está instalado.
 nethelper5 depende de python-qt4 (>= 4.8); sin embargo:
  El paquete `python-qt4' no está instalado.
dpkg: error al procesar nethelper5 (--install):
 problemas de dependencias - se deja sin configurar
Procesando disparadores para desktop-file-utils ...
Se encontraron errores al procesar:
 nethelper5


edito: 2

> mama@zeuza:~/Descargas$ sudo apt-get install -f
Leyendo listas de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Corrigiendo dependencias... Listo
Se instalarán los siguientes paquetes extras:
  libqt4-dev libqt4-help libqt4-opengl-dev libqt4-scripttools libqt4-test libqtassistantclient4 libqtwebkit-dev libqtwebkit4
  python-qt4 python-sip qt4-linguist-tools qt4-qmake
Paquetes sugeridos:
  libpq-dev qt4-dev-tools qt4-doc unixodbc-dev python-qt4-dbg
Se instalarán los siguientes paquetes NUEVOS:
  libqt4-dev libqt4-help libqt4-opengl-dev libqt4-scripttools libqt4-test libqtassistantclient4 libqtwebkit-dev libqtwebkit4
  python-qt4 python-sip qt4-linguist-tools qt4-qmake
0 actualizados, 12 se instalarán, 0 para eliminar y 0 no actualizados.
1 no instalados del todo o eliminados.
Se necesita descargar 5.314 kB/16,2 MB de archivos.
Se utilizarán 86,5 MB de espacio de disco adicional después de esta operación.


:D

---

### Post by juancarlospaco on 2011-11-21
sudo apt-get install python-qt4 libqtwebkit-dev

No esta relacionado con el programa, dpkg no instala deps

---

### Post by mama21mama on 2011-11-21
Si, paso que en medio de la descaga de paquetes aprete el ctrl+c

> mama@zeuza:~/Descargas$ sudo apt-get remove nethelper5
Leyendo listas de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Los paquetes indicados a continuación se instalaron de forma automática y ya no son necesarios.
  python-qt4 python-sip libqtassistantclient4
Utilice «apt-get autoremove» para eliminarlos.
Los siguientes paquetes se ELIMINARÁN:
  nethelper5
0 actualizados, 0 se instalarán, 1 para eliminar y 0 no actualizados.
Se liberarán 397 kB después de esta operación.
¿Desea continuar [S/n]? s
(Leyendo la base de datos ... 255631 ficheros o directorios instalados actualmente.)
Desinstalando nethelper5 ...
Procesando disparadores para desktop-file-utils ...
mama@zeuza:~/Descargas$ sudo apt-get autoremove 
Leyendo listas de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Los siguientes paquetes se ELIMINARÁN:
  libqtassistantclient4 python-qt4 python-sip
0 actualizados, 0 se instalarán, 3 para eliminar y 0 no actualizados.
Se liberarán 24,7 MB después de esta operación.
¿Desea continuar [S/n]? s
(Leyendo la base de datos ... 255606 ficheros o directorios instalados actualmente.)
Desinstalando python-qt4 ...
Desinstalando libqtassistantclient4 ...
Desinstalando python-sip ...
Procesando disparadores para libc-bin ...
ldconfig deferred processing now taking place
mama@zeuza:~/Descargas$ 


Funciona joya. No se para que se usa, pero funciona.

0/

---

