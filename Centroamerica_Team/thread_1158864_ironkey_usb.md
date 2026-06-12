---
title: "ironkey usb"
date: 2009-05-14
forum: Centroamerica Team
---

### Post by hoplita666 on 2009-05-14
Hola. Soy nuevo en esto de Ubuntu, acabo de dejar el windows y todavía estoy un poco despistado. [IMG]http://www.forosubuntu.com/images/smilies/icon_e_confused.gif[/IMG]
Tengo un problema que espero que los usuarios más expertos me sepan resolver.
Tengo una memoria usb Ironkey. Este tipo de memoria es especial, ya que en cuanto se conectan en windows sale una consola donde debes poner una clave y así puedes acceder a la información encriptada dentro.
Pues bien, cuando probé Ubuntu con el live CD no tuve problemas ya que la memoria cuando la introduces monta como una unidad de CD rom y en el aparece un ejecutable para Linux. Si le daba doble click aparecia una ventana del terminal donde me pedía la clave y así me daba acceso al interior. Pero en cuanto instalé por completo Ubuntu en el ordenador en el momento de ejecutar el archivo mencionado me sale esto:

sh: cannot create /proc/scsi/device_info: Permission denied
unable to add IronKey entry to /proc/scsi/device_info
please try re-running as root
Hit return to exit

No sé que hacer ya que he intentado todo para poder ejecutarlo, incluido el intentarlo abrir con sudo, pero nada.
Bueno, espero que alguien me pueda ayudar.
Gracias y un saludo.

---

### Post by eivar on 2009-05-15
Hola hoplita,

> **hoplita666 said:**
> Hola. Soy nuevo en esto de Ubuntu, acabo de dejar el windows y todavía estoy un poco despistado. 
[IMG]http://www.forosubuntu.com/images/smilies/icon_e_confused.gif[/IMG]
Bienvenido y espero que te adaptes rápidamente.

> **hoplita666 said:**
> 
Tengo un problema que espero que los usuarios más expertos me sepan resolver.
Podemos guiarte para encuentres la solución pero queda en tí aplicarla.

> **hoplita666 said:**
> 
Tengo una memoria usb Ironkey. Este tipo de memoria es especial, ya que en cuanto se conectan en windows sale una consola donde debes poner una clave y así puedes acceder a la información encriptada dentro.
Pues bien, cuando probé Ubuntu con el live CD no tuve problemas ya que la memoria cuando la introduces monta como una unidad de CD rom y en el aparece un ejecutable para Linux. Si le daba doble click aparecia una ventana del terminal donde me pedía la clave y así me daba acceso al interior. Pero en cuanto instalé por completo Ubuntu en el ordenador en el momento de ejecutar el archivo mencionado me sale esto:

sh: cannot create /proc/scsi/device_info: Permission denied
unable to add IronKey entry to /proc/scsi/device_info
please try re-running as root
Hit return to exit

No sé que hacer ya que he intentado todo para poder ejecutarlo, incluido el intentarlo abrir con sudo, pero nada.
Bueno, espero que alguien me pueda ayudar.
Gracias y un saludo.

Conozco lo que son las iron key, en su página dice que soportar GNU/Linux: [https://support.ironkey.com/article/50150000000Dx1iAAC](https://support.ironkey.com/article/50150000000Dx1iAAC)

¿a qué te refieres con que lo has intentado todo?
¿qué comandos usaste? danos más detalles.

Aca hay un post (en ingles) de alguien que comenta sobre el uso de iron keys en ubuntu: [http://ubuntuforums.org/showthread.php?t=885167](http://ubuntuforums.org/showthread.php?t=885167)

---

### Post by hoplita666 on 2009-05-16
Hola. Gracias por contestar.
El artículo que me has referido ya lo había visto, pero no funciona. Es una cosa extraña, porque cuando probé mi ironkey al probar ubuntu con el liveCD, este funcionaba con sólo hacer doble click sobre el ejecutable especial para linux que trae el usb, pero, una vez instalé por completo Ubuntu en el ordenador (y me dehize por fin del windows), entonces dejó de funcionar y me salia esto:

sh: cannot create /proc/scsi/device_info: Permission denied
unable to add IronKey entry to /proc/scsi/device_info
please try re-running as root
Hit return to exit

No sé como hacerlo funcionar. Espero que se te pueda ocurrir alguna manera.
Gracias por tu ayuda y un saludo.

---

