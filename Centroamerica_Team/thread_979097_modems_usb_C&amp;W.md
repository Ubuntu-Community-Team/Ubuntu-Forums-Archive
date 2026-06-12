---
title: "modems usb C&amp;W"
date: 2008-11-11
forum: Centroamerica Team
---

### Post by Icehawk on 2008-11-11
Soy un usuario de linux ya con mas de un año de usarlo. Siempre en los foros de ubuntu o cualquier otro distro de linux siempre escucho el problema que los modems usb de C&W no funcionan con linux.

He pasado un tiempo averiguando y resulta que ninguna de las soluciones que se ofrecen en los foros de linux sirven para aquellas personas que tienen internet de C&W ya que ellos no usan PPPoE ni PPPoA (salvo ciertos casos de gente q se conecta a C&W y paga por tiempo) sino un protocolo llamado MER (MAC Encapsulation Routing) y hasta la fecha no he visto algun software en linux que pueda administrar este protocolo.

Por ahora la unica solucion es tener un router ADSL ethernet o pasarse a Cable Onda... por lo menos hasta que alguien desarrolle un software/driver para este protocolo

---

### Post by black_master on 2008-11-11
bueno si es verdad, una vez, logre conectar mi modem usb, y funciono, pero se caia mucho, dedici y me cambie al router :lolflag:

---

### Post by greer on 2008-11-11
> **Icehawk said:**
> Soy un usuario de linux ya con mas de un año de usarlo. Siempre en los foros de ubuntu o cualquier otro distro de linux siempre escucho el problema que los modems usb de C&W no funcionan con linux.

He pasado un tiempo averiguando y resulta que ninguna de las soluciones que se ofrecen en los foros de linux sirven para aquellas personas que tienen internet de C&W ya que ellos no usan PPPoE ni PPPoA (salvo ciertos casos de gente q se conecta a C&W y paga por tiempo) sino un protocolo llamado MER (MAC Encapsulation Routing) y hasta la fecha no he visto algun software en linux que pueda administrar este protocolo.

Por ahora la unica solucion es tener un router ADSL ethernet o pasarse a Cable Onda... por lo menos hasta que alguien desarrolle un software/driver para este protocolo

De que hablas hermano ?  yo antes mi internet me lo suministraba C&W y era/es PPPoE. Y meses despues me pase a PPPoA que es coneccion directa sin contraseñas ni usuario, claro con su modem ese! en los dos casos. Ahora estan dando unos nuevos modem que son por Ethernet (que siguen siendo PPPoA)

Es mas por la red y en mi blog ahi varios temas sobre eso...

---

### Post by black_master on 2008-11-11
jeje greers, cual es el link d tu blog, t puedo agregar a mi blogrool y tu a mi si kieres

---

### Post by meldon12 on 2008-11-12
Claro que se puede, ahora mismo estoy desde Ubutu Hardy con un modem USB Zyxel Prestige 630 C-Series, sin ningún problema, claro que la primera vez fue un dia entero para instalarlo, pero gracias a la ayuda de greer lo logré, ahora en 5 minutos lo instalo cada vez que formateo (de la costumbre xD) y wala!!, internet feliz.

Por si acaso, aquí dejo lo q yo hago cada vez con ubuntu 8.04 y creo que es lo mismo con el 8.10 (descarguen el archivo que adjunto y descomprimir):

1. copiar el firmware del modem, cxacru-fw.bin a /lib/firmware:
> cp cxacru-fw.bin /lib/firmware
2. supuestamente no necesita reinicar pero yo siempre tengo q hacerlo porq o sino no carga el firmware, ais q:
> sudo reboot
3. Instalamos el paquete br2684ctl_20040226-1_i386.deb:
> sudo dpkg -i br2684ctl_20040226-1_i386.deb
4. Ahora cargamos el module br2684 en el kernel:
> sudo modprobe br2684
5. configuramos la interfaz nas0 usando el VPI y VCI (esto lo consiguen en windows, en el panel de control del modem, en mi caso, vpi=1 y vci=32):
> sudo br2684ctl -c 0 -b -a 1.32
Si todo va bn, aparecera el siguiente mensaje:
> br2684ctl[5566]: Interface "nas0" created sucessfully
br2684ctl[5566]: Communicating over ATM 0.1.32, encapsulation: LLC
br2684ctl[5566]: Interface configured

6. luego montamos la interfaz, usando ip, netmask, gateway y las dns (tambn desde windows, ejecutar>>cmd>>ipconfig/all)
> sudo ifconfig nas0 <ip> netmask <eso mismo xD> up
sudo add default gw <gateway>
7. por ultimo se van a Sistema>>Administracion>>Red y en la pestaña DNS, añaden las 2 dns de su coneccion.
8. listo solo disfrutar de internet.

PD: para que se inicie con ubuntu, hacecemos los siguiente:
> sudo gedit /etc/rc.local
y antes del exit 0 escribimos:
> sudo modprobe br2684
sudo br2684ctl -c 0 -b -a 1.32
sudo ifconfig nas0 <ip> netmask <netmask> up
sudo route add default gw <gateway>
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop
las 2 ultimas lineas son para q en el firefox no salga, al inicarlo, eso de q esta sin conexion a red y tener q estar a cada rato desactivando ese modo en el menu Archivo.

saludos

meldon12

---

### Post by greer on 2008-11-12
> **black_master said:**
> jeje greers, cual es el link d tu blog, t puedo agregar a mi blogrool y tu a mi si kieres

[http://greer.nodolinux.com](http://greer.nodolinux.com)

y para Icehawk:

[http://greer.nodolinux.com/menos-paquetes/](http://greer.nodolinux.com/menos-paquetes/)

[http://greer.nodolinux.com/coneccion-a-internet-con-modem-usb-en-linux/](http://greer.nodolinux.com/coneccion-a-internet-con-modem-usb-en-linux/)

---

