---
title: "Modem Claro Alcatel X060 en Ubuntu 9.10 (Karmic Koala)"
date: 2009-11-19
forum: Centroamerica Team
---

### Post by alexishevia on 2009-11-19
Hola gente, 

Recientemente conseguí un modem usb de Claro, marca Alcatel One Touch X060A, y pasé muchos problemas tratando de hacerlo funcionar en una netbook con Ubuntu Netbook Remix 9.10 (Karmic Koala). 

Estuve apunto de desistir y usar el Windows 7 que vino con la pc, pero afortunadamente econtré un par de posts que me fueron de gran ayuda y logré que funcionara. Aquí les dejo mi solución:


[LIST=1]
[*]Ejecutar lo siguiente para actualizar el paquete "modemmanager":
sudo add-apt-repository ppa:jmartinj/x060-karmic
sudo apt-get update
sudo apt-get upgrade
[*]Ejecutar lo siguiente para instalar el paquete usb-modeswitch:
sudo apt-get install usb-modeswitch
[*]Conectar el Modem y configurar la conexión de Banda Ancha en el Network Manager.
[/LIST]
Para configurar la conexión de Banda Ancha, usamos los siguientes parámetros:
País: Panama
Proveedor: Claro  (como solo está la opción de Cable & Wireless y Movistar, debemos seleccionar la opción de introducir manualmente y escribir "Claro")
Tecnología: GSM
APN (Access Point Name): web.claro.com.pa 
Número: *99#
Username y Password en blanco

También pueden intentar usando 
Número: +99#
Username:CLARO
Password:CLARO

Si todo ha salido bien, deben poder navegar sin problemas. Espero que les sirva de algo el post, y agradezco mucho a los autores de los siguientes posts:

[http://potrerohacaido.blogspot.com/2009/11/simyo-alcatel-x060-ubuntu-910-karmic.html](http://potrerohacaido.blogspot.com/2009/11/simyo-alcatel-x060-ubuntu-910-karmic.html)

[http://www.ubuntu-pa.org/foroubuntu/weblog/6317.html](http://www.ubuntu-pa.org/foroubuntu/weblog/6317.html)

---

### Post by eivar on 2009-11-20
Hola alexishevia, muchas gracias por este aporte.
Saludos.

---

### Post by ScrewBaxster on 2010-01-10
Gracias alexishevia por la ayuda. Me ha servido para poder utilizar mi MODEM con mi ubuntu 9.10. 

Gracias!!

---

### Post by Noelito3 on 2010-06-02
Si quereis hacerlo funcionar en Ubuntu 10.04, aquí hay un tutorial que lo explica muy clarito:

[_http://felinfo.blogspot.com/2010/05/modem-alcatel-x060s-symio-en-ubuntu.html_]("http://felinfo.blogspot.com/2010/05/modem-alcatel-x060s-symio-en-ubuntu.html")

---

