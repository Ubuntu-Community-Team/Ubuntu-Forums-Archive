---
title: "Una forma alternativa de editar una tabla de particiones"
date: 2011-05-15
forum: Comunidad
---

### Post by EnriqueK on 2011-05-15
Aquí expongo la forma que empleé para editar completamente mi tabla de particiones, estimo que es un método muy seguro ya que solo se trata de empaquetar y restarar archivos tar.gz , de la misma forma que se haría con cualquier directorio.

**A.- Lo que se pretende hacer**
La situación que tenía era la siguiente :
sda1 --> / de Ubuntu 15Gb
sda2 --> Extendida de unos 120Gb
sda5 --> Lógica que era la partición home de Ubuntu
sda6 ..> Lógica de datos de unos 90 Gb
sda7 --> swap
sda3 --> / de Debian

El reto era reformar totalmente esta tabla de particiones y modificar el espacio asignado a cada una de ellas para que quede de la siguiente manera
sda1--> /de Ubuntu de 20 Gb
sda2--> /de Debian de 20 Gb
sda3--> Extendida
sda5 --> swap
sda6 --> partición Home de Ubuntu
sda7 --> Partición de datos
Hacer todo esto solamente con Gpaparted sería muy complicado y sobretodo inseguro ya que las probabilidades de sufrir un corte de energía en pleno proceso sería mayor.
**B.-Los elementos requeridos son_**
1.- Live Cd de Ubuntu
2.- Disco duro de respaldo, puede ser interno o externo de capacidad suficiente para almacenar una copia comprinida de cada paerición, yo empleé uno interno.
3.- Descargar y quemar en un CD el Super Grub2 Disk.
[http://www.bootproblems.com/category/download/supergrub2diskdownload/](http://www.bootproblems.com/category/download/supergrub2diskdownload/)
4.- Opcionalmente sería coveniente contar con un pendrive para llevar los comandos y así ejecutarlos sin pérdida de tiempo, conviene hacer notar que si bien este método es muy seguro, no puede evitarse comentan errores de digitación, por lo que recomiendo es que se creen script revisados a todo detalle y así ejecutarlos con toda confianza cuando llegue el momento.
**C.- Procedimiento**
1- Arrancamos con el Live CD de Ubuntu, y abrimos Gparted, nos va a mostrar la tabla de particiones actual , lo que debemos hacer en esta etapa es ponerle una etiqueta o Label a cada partición , en mi caso le puse
Ubuntu a sda1
Casa a sda5
Datos a sda6
Debian a sda3
Respaldo al DD externo o interno que se tenga
Todo esto es la clave del método ya que este en realidad es muy simple ya que solo se trata de crear un archivo tar.gz de cada partición y que luego restauraremos en la nueva tabla de particiones.
2.- Cerramos Gparted, vamos al menú Lugares y montamos todas las particiones y ademas el DD de respaldo , si vamos a /media, veremos que todas estas están montadas allí y con el nombre que se definió al crear la etiqueta, esto es muy importante comprobarlo
3.- Creamos los respaldos, para el caso del ejemple mediante
sudo -i
cd /media/Respaldo
tar -zcvf Ubu.tar.gz /media/Ubuntu
tar -zcvf Debi.tar.gz /media/Debian
tar -zcvf Cas.tar.gz /media/Casa
tar -zcvf Dat.tar.gz /media/Datos
Este paso si bien es muy seguro, demora bastante, por eso sugiero meter estos comandos en un script y ejecutar a este como root.
4.- Terminado el respaldo, entrar nuevamente a Gparted pero esta vez para borrar todas las particiones, definir la nueva tabla, formatear las particiones y ponerle las mismas etiquetas que tenía cada partición en la tabla original.
5.- Ahora toca reponer los respaldos mediante los siguiente comandos
sudo -i
cd /media/Respaldo
tar -zxvf Ubu.tar.gz --directory /
tar -zxvf Debi.tar.gz --directory /
tar -zxvf Cas.tar.gz --directory /
tar -zxvf Dat.tar.gz --directory /

6.- Ya casi está listo, toca ahora entrar a los detalles, editando el fstab de cada distro , por ejemplo ponemos
sudo gedit /media/Ubuntu/etc/fstab
a allí veremos por ejemplo que la partición donde tiene su /home pasó de sda5 a sda6, lo lo que debemos corregir este valor, para el caso de Debian su partició / pasó de estar en sda3 a sda2 , corregomos , luego en otro terminal ejecutamos
sudo blkid
y corregimos el valor de UUID de cada partición en el fstad de cada distro.
7.- ya terminamos, ahora arrancamos el equipo con el "Super Grub2 Disk" elegimos la opción que muestre todos los SO , elegimos uno de ellos y cuando arranque ejecutamos los siguientes comandos
sudo -i
grub-mkconfig
grub-install /dev/sda
update-grub
Luego ejecutamos en otro terminal
sudo blkid esta vez para corregir el valor de UUID de la swap de cada distro, si no hacemos estom la swap no funcuinará.
Repetimos esto con el otro SO y se terminó la historia
Solo recalco que al menos en mi opinión, el método es muy seguro, cualquiera sea el problema que se tenga en cada etapam simplemente se repite la operación.
Esto sería un caso extremo, pero este método sirve por ejemplo para crear un respaldo que puede instalarse en otra PC , en mi caso los resaldos de las particiones / de Ubuntu y de Debian, rondaban por los 3.6 Gb , lo que perfectamente caben en un DVD, Otro lugar de aplicación seía cuando clonamos el DD a otro mayor, en estos caso el uso del comando DD dejaría un espacio sin asignar por la diferencua de tamaño, el acomodar los epacios se vuelve en una tarea muy pesada y hasta peligrosa para los datos, las posibllidades son variadas.

---

### Post by z37a on 2011-05-17
No entendí bien si lo tenes o no así, pero en caso que no te tiro un tip (y no no se te venga a la cabeza al auto de la publicidad!).

El /home de Ubuntu puede ser el mismo que el /home de Debian, de esta manera cuando inicies sesión con el usuario vas a mantener tus mismas configuraciones de usuario en los programas, fondo de escritorio y demas sin importar que uses, si Debian o Ubuntu.

PD: Por que Debian y Ubuntu juntos y no Ubuntu/Debian con CentOS/Fedora/OpenSuSe u otro? Solo por curiosidad nomas!

---

