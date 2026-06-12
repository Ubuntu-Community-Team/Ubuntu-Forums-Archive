---
title: "[SOLVED] Instalar modem zyxel 600 series"
date: 2008-04-03
forum: Centroamerica Team
---

### Post by meldon12 on 2008-04-03
hola, me lleve una gran sorpresa cuando encontre esta pagina de ubuntu Panamá en google, felicito a los que tuvieron la idea.

Este post es para ver si alguien me podria decir como instalar el modem Zyxel prestige 600 series que te dan los de la C&W (o te daban, porque llevo 3 años con internet) ya que he usado infinidad de guias pero siemrpe tengo peoblemas cuando hay que poner el usaruio y contraseña de la conexion, y que yo sepa a mi no me ideron nada de eso. 

Me gustaria que pudieran ayudarme ya que quiero migrar a ubuntu porque estoy harto del monopolio de "Ya saben quien".

muchas gracias de antemano y de nuvo felicitaciones por esta gran idea.

Atte.

David Villarreal.

---

### Post by mayeco on 2008-04-03
Saludos David,

Te escribo para darte la bienvenida y esperamos que seas un participe activo en nuestra comunidad.

Saludos,

PD// no tengo idea de como ayudarte uso Cable Onda y funciona bastante bien, esperemos que alguien más te pueda ayudar.

---

### Post by eivar on 2008-04-04
Hola y bienvenido a la comunidad, tengo la tristeza de decirte que las únicas dos personas que conozco que lograron hacer funcionar ese módem tuvieron que compilar el kernel... :(
En cuanto al usuario y contraseña por lo que sé lo debes dejar en blanco.
Te puedo recomendar pidas un aparato con salidas de red (RJ45) o te pases a Cable Onda para evitar dolores de cabeza.

Saludos y cuenta nos ¿cómo te termina de ir con este asunto?
Eivar.

---

### Post by meldon12 on 2008-04-04
Muchas gracias por la bienvenida, pasare lo mas posible por aqui.

He logrado hacer que el modem sincronice con ubuntu (las luces parpadearon y luego quedaron fijas, osea que voy bn) pero parace que todavia me falta algo, porque cuando mando a ejecutar me dice "The interface is not configured". Creo que esto es por el user y pass, tambn llegue a pensar lo que me acabas de decir, Eivar, de dejarlos en blanco, lo intentare haber si me logra compilar.

Respecto a lo de clable onda, con ellos es que iba a poner internet cuando se acabo mi contrato de CW pero lastimosamente para mi área (Nuevo Arraiján, Arraiján) aun no esta disponible su servicio.

Si lo llego a hacer funcionar pongo aqui como lo hice para que les sirva a otros.

Saludos

meldon12

---

### Post by demogar on 2008-04-10
Pues lei este mensaje en el foro y sinceramente me parece gracioso, no porque cuente algun chiste, sino porq me ha pasado lo mismo que al usuario meldon12..... llegue a este foro por mera casualidad de google, tengo un modem zyxel prestige 630, hace poco he tratado con mucho esfuerzo de instalarlo en ubuntu pero no lo he logrado de ninguna manera y ademas, vivo en el Area Oeste tambien, en donde no hay servicio de Cable Onda....

Lo curioso es que en donde he leido muestra que es casi imposible instalar un modem de este tipo, siempre y cuando utilice IPoA (puenteador de RFC 1483), lo que significa q el modem no necesita nombre de usuario y contraseña...

Luego de leer mucho, he entendido q casi la unica solucion es cambiar el modem por un modem de 4 puertos ethernet, y al llamar a CWP, luego de pasarse la pelota entre mas de 5 personas porque no entendian lo q les pedia... me informaron q el cambiode modem q antes cobraban 20.00  ahora estan cobrando 30.00 (no me pregunten por que)...

Quisiera saber si has podido tu solucionar el problema este, sino creo q ambos seremos nuevos estafados de CWP....

Saludos!

---

### Post by meldon12 on 2008-04-10
lastimosamente no he podido, llevo mas de un mes intentandolo sin ningun resultado, tendre que ahorrar mis respectivos 30.00 dolares para cambiar a router. Encontre un tutorial en los foros de latinol que no se si les sirva, no lo pongo porque lo pueden caalogar como spam, asi que si alguien lo necesita diganmelo por mp.

saludos

---

### Post by demogar on 2008-04-10
ya habia encontrado el tutorial que dices, el problema con el tutorial es q parece q necesitaba un archivo llamado " AmCWpanama04.tar.gz" que estaba posteado ahi, pero ya no lo esta ya...
Estoy pensando que ya la unica solucion va a ser o permanecer en window$ por mientras... y tratar de conseguir el ethernet este

---

### Post by greer on 2008-04-12
bueno yo lo hice funcionar hace ya un año o mas no recuerdo 
primero tienes que decir si es PPPoE o coneccion directa (PPPoA)

de las dos forma lo consegui.  no se necesita compilar  el kernel ni nada.

una introduccion rapida ok ? despues me dicen cada uno cual es el modem y que tipo de cuenta tienen para ayudarlos a todos ok ?

uno para el user y pass (PPPoE)

leanse esta guia si no entienden o se enredaron me avisan ok ? 

[http://www.hackpr.net/db/index.php?act=view&id=38](http://www.hackpr.net/db/index.php?act=view&id=38)

bajenla  esta en PDF

************************************************************

para coneccion directa (PPPoA)

sigan estos pasos, los mio claro! 

[http://www.ubuntu-es.org/index.php?q=node/60131&page=1](http://www.ubuntu-es.org/index.php?q=node/60131&page=1)

si se quedaron en alguna parte avisenme ok ? bueno!

---

### Post by meldon12 on 2008-04-12
el mio es PPPoA o de conexion directa, ya que no tengo que meter contrasela ni nada.

saludos

---

### Post by greer on 2008-04-12
**para coneccion directa**

sigue los pasos que salen aqui: 
[http://www.ubuntu-es.org/index.php?q=node/60131&page=1](http://www.ubuntu-es.org/index.php?q=node/60131&page=1)

claro! si ya tienes el modem detectado y andando. ese link es para configurar el interface de red para que sincronice etc...

si aun no haz instalado el modem bajate esta guia:

[http://www.hackpr.net/db/index.php?act=view&id=38](http://www.hackpr.net/db/index.php?act=view&id=38)

[COLOR="Red"]y solo llega asta el paso donde se sube la interface osea hasta[/COLOR]

**#sudo ifconfig nas0 up**

despues de ese paso lo que sigue es la configuracion de la interface ya creada (nas0) entonces ahi comiensa con el link que te di:

[http://www.ubuntu-es.org/index.php?q=node/60131&page=1](http://www.ubuntu-es.org/index.php?q=node/60131&page=1)

listo...

*******************************************************
otra cosa de la guia esa guia es para instalar el modem y despues instalr el programa : rppppoe3.8.tar.gz que es el que se usa para la coneccion PPPoE

user y pass  pero para coneccion directa no es necesario ese programa solo instalr el modem usando la guia y configurando le interface ya creada siguiendo los pasos: [http://www.ubuntu-es.org/index.php?q=node/60131&page=1](http://www.ubuntu-es.org/index.php?q=node/60131&page=1)

*******************************************************

aca les dejo los programas para los dos casos PPPoE y PPPoA
necesarios para los dos ya que en los dos caso se necesita instalar el modem

solo PPPoA no nedesita el paquete **rppppoe3.8.tar.gz**

aca les dejo el link para que bajen todos los programas necesarios todos estan en una carpeta comprimida zip:

[http://www.hackpr.net/db/index.php?act=view&id=40](http://www.hackpr.net/db/index.php?act=view&id=40)

---

### Post by greer on 2008-04-12
para PPPoE (user y pass) :S prepago

sigan todos los pasos de esa guia, paso a paso y donde se queden estancados me avisan.

***********************************************

para PPPoA (coneccion directa)

sigan los pasos de la guia paso a paso **pero** omitan el paso donde se instala el programa para poner    _pass y user_  osea el paquete ( rppppoe3.8.tar.gz )

ya que ese no es necesario.

en la guia menciona unos programas necesario para los dos casos pueden bajarlos de link que ya les di: 

[http://www.hackpr.net/db/index.php?act=view&id=40](http://www.hackpr.net/db/index.php?act=view&id=40)

**********************************************

para PPPoA una ves instalado el modem osea que se prendan las luces etc...

siguiendo la guia entonces va llegar el paso de configurar la interface, y como configurarlo entonces sigan los pasos que hice: 

[http://www.ubuntu-es.org/index.php?q=node/60131&page=1](http://www.ubuntu-es.org/index.php?q=node/60131&page=1)

---

### Post by meldon12 on 2008-04-16
muchas gracias por la guia, te informare por si tengo algun problema, aunque, tengo una pregunta, como dije, me dice que solo falta configurar la interfaz cuando intento iniciar el modem, pero yo use ese paquete que dijistes que omitiera en mi caso, puedo seguir normal o tengo que borrar lo que hice y empezar mejor??? muchas gracias por la ayuda.

saludos

medon12

---

### Post by greer on 2008-04-16
ya lo instalaste ? pues si es asi no importa... es solo un prorama. no afecta nada.

pero bueno sigue con la configuracion de la interface. si tu modem esta detectado, se prenden las luces y todo pues creo yo que esta listo solo falta sincronizarlo. sigue la guia de como hacerlo es facil, tiene pocos pasos...

[http://www.ubuntu-es.org/index.php?q=node/60131&page=1](http://www.ubuntu-es.org/index.php?q=node/60131&page=1)

solo es cuestion de asignarte un ip en este caso ponerle el ip estatico que te dio cwp ponerle el gateway, el subnet y los dns listo...


esos datos los puedes sacar de windows si lo tienes instalado donde ?

serca del reloj de windows abajo ahi un icono que tiene como unos monitores :s
tu sabes!!! bueno ahi copia esos datos y mantenlos a mano...

otra cosa ya que te allas conectado siempre que reinicies vas a tener que poner esos datos pero yo encontre una forma de que al iniciar el sistema se configure sola y la interface se configure sola.... despues hablamos eso  primero ahi que tener coneccion.

---

### Post by meldon12 on 2008-04-18
bueno greer, ya he hecho lo que pusistes en tu guia pero tengo una duda, en la parte que pones *broadcast 192.168.255.255* no estoy seguro de que debe ir hay porque pones una combinacion de numeros que no corresponde a ninguno de los datos que tienes, lo demas ya lo he hecho, ¿despues tengo que entrar en internet haber si funciona?? o tengo que poner alguna otra instruccion para que inicie el modem??

saludos

---

### Post by greer on 2008-04-18
no brother!!! eso son ips falsos osea de ejemplo, ahi tienes que poner los tuyos.

osea mira ESTE ES UN EJEMPLO CON   IP´S  FALSOS, AHI DONDE VAN ESOS ES DONDE TIENES QUE PONER LOS TUYOS:


**************************************************

Supongamos que tenemos estos datos y que queremos configurar la interfaz **nas0** :

IP privada: 192.168.0.2
Mascara de subred: 255.255.0.0
Puerta de enlace: 192.168.0.1
DNS primario: 80.58.0.33
DNS secundario: 80.58.32.97
 
La configuración desde cero de la red sería asi (recordad que hay que hacerlo como root):
 
    # ifconfig nas0 192.168.0.2 broadcast 192.168.255.255 netmask 255.255.0.0 up
    # route add default gw 192.168.0.1
    # echo "nameserver 80.58.0.33" >/etc/resolv.conf
    # echo "nameserver 80.58.32.97" >>/etc/resolv.conf 
 
Con estas 4 líneas configuramos la red, añadimos la puerta de enlace y ponemos los servidores DNS en el fichero /etc/resolv.conf. Ahora ya tenemos lista nuestra red para usar nuestro ADSL, o simplemente formar parte de la red local en la que estemos.

---

### Post by meldon12 on 2008-04-18
si lo se, se que es un ejemplo, yo puse los mios, sino que no se que es eso de BROADCAST.

saludos

EDITO:

tambn queria preguntar otra cosa ¿tengo que poner 2 servidores DNS nada mas? porque a mi me aparecen 3 cuando me fijo en ejecutar>>cmd>>ipconfig (windows)

---

### Post by greer on 2008-04-18
ok solo pon tu ip y el netmask asi:

# ifconfig nas0 192.168.0.2 netmask 255.255.0.0 up


y es necesario 2 dns como minimo pero si tu quieres poner un tercero  bienvenido sea...
los dns va el el archivo         /etc/resolv.conf  
si no lo encuentras es por que no esta, entonces ahi crealo y ponel como nombre         resolv.conf          y ponlo dentro de           /etc y darle permiso de ejecusion
y tienes que poner en ese archivo los DNS y pordelante NAMESERVER osea nameserver 80.58.32.97

entonces quedaria asi lo que pondrias en consola :

# ifconfig nas0 192.168.0.2 netmask 255.255.0.0 up
# route add default gw 192.168.0.1
# echo "nameserver 80.58.0.33" >/etc/resolv.conf
# echo "nameserver 80.58.32.97" >>/etc/resolv.conf
# echo "nameserver 80.58.32.57" >>/etc/resolv.conf

**********************************

hermano quiero acordarte que este es la configuracion final de la interface osea tienes que tener primero tu modem listo. ahora te pregunto ya lo sincronisaste ?

ya haz puesto este paso ?

[COLOR="black"]modprobe br2684[/COLOR]

[COLOR="black"]br2684ctl -c 0 -b -a 1.32[/COLOR]

estos dos pasos se tienen que hacer primero,  que la configuracion de ips etc...

---

### Post by meldon12 on 2008-04-18
ese de br268.... ya lo hice pero el modprobe no, pero mi modem prende y se queda fijo cada vez que entro en ubuntu.

saludos

PD: No puedo creerlo lo he logrado, muchas gracias por tu ayuda GREER, sin tu ayuda hubiera sido imposible, te lo agrdezco de verdad, no sabes la emocion que siento.

DESDE UBUNTU!!!!!!!!!!!!!!!!!

Saludos a todossssssss!!!!

---

### Post by greer on 2008-04-18
serio !?  bueno me alegro y que lo disfrutes xD

la comunidad esta para eso para ayudar!

otra cosa, siempre que inicie ubuntu tienes que poner en consola:

#modprobe br2684
#br2684ctl -c 0 -b -a 1.32
#ifconfig nas0 192.168.0.2 netmask 255.255.0.0 up
#route add default gw 192.168.0.1

lo que hice yo fue poner esas 4 lines en el fichero /etc/rc.local

ese fichero esta para poner cosas asi osea poner cosas que quieres que se inicien cuando inica ubuntu y asi no tienes que hacerlo a mano cada ves que inicie ubuntu con ponerlo en ese fichero se hace automatico...

entonces  pones esas cuatro lineas dende termina las letras azules.

no le pongas numeral (#) osea no comentes las cuatro lineas.y se veria asi:

# By default this script does nothing.
modprobe br2684
br2684ctl -c 0 -b -a 1.32
ifconfig nas0 192.168.0.2 netmask 255.255.0.0 up
route add default gw 192.168.0.1
exit 0

---

### Post by meldon12 on 2008-04-19
ya lo he hecho, de nuevo muchas gracias por tu ayuda, al final resulto ser muy facil XD.

PD: nunca te coenctas al msn

saludos

---

### Post by demogar on 2008-04-20
Ante todo, disculparme pero nunca me entere que estaban teniendo las conversaciones por estos lugares, hasta que el amigo meldon (Death) me contacto en msn diciendome que habia logrado hacer esto.

Bueno, yo tengo un Zyxel prestige 630 (el azulito) y las luces me permanecen totalmente encendidas cuando entro al Ubuntu, por lo que creo que el modem esta completamente instalado, pero no esta bien sincronizado con el sistema. 

El problema es que apenas entro a ubuntu y ejecuto el
sudo echo "nameserver xxx.xxx.xxx.xxx" >/etc/resolv.conf

me tira un mensaje de error la terminal diciendome:
bash: /etc/resolv.conf: Permiso denegado

Lo que no entiendo es porque sucede.

---

### Post by demogar on 2008-04-20
tuve q hacer la edicion con un sudo gedit pero las luces del modem se mantienen encendidas ambas....

---

### Post by greer on 2008-04-20
brother el fichero /etc/[COLOR="Black"]resolv.conf[/COLOR] es para poder ver las paginas web por asi decirlo osea ahi van las dns. puedes estar conectado pero sin ese fichero no podras ver las paginas web.

de nada sirve si no tienes el modem instalado y configurado ok ? sigue las guias que he dejado... lee los post anteriores.


el que las luces del modem esten encendidas no quiere decir que este instaldo.
si estan encendidas es por que el linux (kernel) lo detecta solo eso.

sigue los pasos de las guias que he dejado en los post anteriores.

pd.: son los mismos pasos para los dos casos el de coneccion PPPoE y el PPPoA
la unica diferencia es que uno necesita un programa de mas (PPPoE) que es el programa donde se pone el user y pass, pero antes de eso todo es igual en los dos casos.

---

### Post by greer on 2008-04-21
y respondiendo al tu post... ese fichero tiene que tener permiso de ejecucion y para modificarlo tienes que ser root.

entra a /etc  y buscalo si no esta es por que no se ha creado, no existe.
entonces crealo :) y ponle las 2 dns, y si tienes 3 ponsela tambien.

recuerda que se tiene que poner    nameserver xxx.xxx.xxx.xxx

solo eso y darle permiso de ejecucion. una ves creado ya no necesitas volver a crearlo ni volver a ponerle las dns ok ?
cuando lo allas hecho no necesitas volver hacerlo cada ves que inicies ubuntu :s 

pero ese fichero es solo para poder ver las paginas web, para poder visualizarlas en tu navegador, como ya dije puedes estar conectado a internet, pero sin ese fichero no vas a poder ver las paginas web :s

pero de nada sirve que tengas ese fichero con las dns si no te haz coenctado :s

instala el modem configura tus ips y me avisas despues como te fue...
como dije antes sigue las guias que he dejado en los post anteriores que estan muy claras y faciles de seguir, no ahi complicaciones.

---

### Post by meldon12 on 2008-04-21
hola greer, hoy llegue feliz a mi casa, prendi el pc e hice lo de las ips y eso (porque no me sirve lo de rc.local), bueno, la cosa es que entro al firefox y se queda un monton de tiempo cargando pero no sale nada :( reinice como tres veces y lo volvia a intentar, y seguia igual, cargando pero nada, y no se porque sera, despues intente volver a hacer lo que habia hecho antes, instalar eso de br2684 (algo asi) y ahora lo que salia cuando hacia lo de sudo ifconfig..... es que no se encuentra la interfaz nas0 y otro monton de errores y estoy muy triste, ya que me habia acostumbrado al ubuntito :(.

Ahora estoy pensando en instalar ubuntu de nuevo y comenzar de nuevo, pero mejor con la guia que dices tu que usastes, para enredarme menos, si sabes otra solcuion, me dice plss.

Saludos

meldon12

---

### Post by greer on 2008-04-21
copia aqui lo que te sale en ifconfig.
pon asi ifconfig >> Desktop/ifconfig.txt y pon aqui lo que te salga.


eso del firefox que se queda como pensando me parece  que es que algo hiciste con las dns.

trata a ver si te conectas con el messenger, si es asi y aun no puedes ver nada por firefox es porque algo hiciste con las dns.

y como dije antes una ves puesto las dns no hace falta tocar ese fichero mas!
es mas ponlas y olvida despues que existe ese fichero no lo toques, si es eso el problema claro.


lo que debes hacer siempre que inicias ubuntu es poner solo esto:

#modprobe br2684
#br2684ctl -c 0 -b -a 1.32
#ifconfig nas0 192.168.0.2 netmask 255.255.0.0 up
#route add default gw 192.168.0.1

y lo de

# echo "nameserver 80.58.0.33" >/etc/resolv.conf
# echo "nameserver 80.58.32.97" >>/etc/resolv.conf

solo se hace una ves y que quiere decir ? que creas el fichero resolv.conf
y le pones como texto nameserver 80.58.0.33

despues de ahi eso no se toca.

vuelvo y repito...

esto:

#modprobe br2684
#br2684ctl -c 0 -b -a 1.32
#ifconfig nas0 192.168.0.2 netmask 255.255.0.0 up
#route add default gw 192.168.0.1

es lo que siempre se debe pooner, en nuestro caso cuando iniciamos ubuntu ok ? solo esas 4 lineas que es la creacion de la interface.

y yo lo puse en rc.local que tiene que tener permiso de ejecucion y!!!
el dueño del fichero tiene que ser el root y tiene que ser asi:

usuario - solo lectura
grupo - solo lectrua
otros - solo lectura

---

### Post by greer on 2008-04-21
tu ip es estatica o dinamica ?

---

### Post by meldon12 on 2008-04-22
mi ip es estática.

respecto a lo de rc.local, la ves pasada lo puse pero no me sirvio, y no se como se le da permiso de ejecucion, mmm creo que si, voy a ubuntu a ver..

saludos

---

### Post by meldon12 on 2008-04-22
mi ip es estática.

respecto a lo de rc.local, la ves pasada lo puse pero no me sirvio, y no se como se le da permiso de ejecucion, mmm creo que si, voy a ubuntu a ver..

saludos

---

### Post by meldon12 on 2008-04-22
listo, muchas gracias greer, disculpa haberte dado tanta lata XD, ya lo he arreglado.

Otra vez, DESDE UBUNTU 7.10 GUTSY GIBBON xD

Saludos a todos!!

meldon12

---

### Post by eltincho1 on 2008-05-02
Holaaaa, soy re novato en esto. tengo un modem zyxel 600 prestige y no se como  instalar en mi ubuntu!!!!!. me estoy volviendo loco buscando en todos lados!!!!! porfa nesecito ayuda profecional :P

Va a ser MUUUYYY agradecida :)
hasta luego!

---

### Post by meldon12 on 2008-05-02
se ve que no has leido el post entero, porque en un mensaje greer pone un manual para poder instalarlo, y nisiquiera nos dices que es lo que has hecho, si algo te ha salido mal, para asi pioder ayudarte mejor.

saludos

---

### Post by greer on 2008-05-02
hermano leete el tema completo...

quiero agregar al tema y a la facilidad de la instalacion del modem que, en la nueva vercion 8.04 gracias a su plug and play integrado ahora... la instalacion se hace mas rapida con lo que ya no es necesario reiniciar el sistema y para mejorar el asunto necesitamos menos paquetes de los que le di a detallar en el tema.

paea ser mas exacto solo se necesita el paquete donde esta el firmware del modem (ueagle-data-1.1.tar). extraer el contenido en /lib/firmware/ueagle-atm

y por si fuera poco no ahi la necesidad de ejecutar el comando modporbe

ya que el mismo kernel lo hace, solo ahi que darle maximo unos 5 segundos para que el modem prenda y se sincronize y quede listo!

vuelvo y repito solo se necesita un solo paquete de los que sale en la guia, extraer y copiarlo el contenido en la carpeta /lib/firmware/ueagle-atm  y listo el modem esta instalado!

lo unico que haria falta seria configurar la interface el cual necesita el paquete que se menciona en la guia br2684ctl_200402261_i386.deb y seguir los pasos para la creacion de la interface...

ojo la creacion de la interface y la instalacion del modem son dos cosas apartes pero ligadas.

en realidad se estarin usando 2 paquetes de los mencionados en la guia el firmware y el de la interface el br2684ctl_200402261_
i386.deb

---

### Post by meldon12 on 2008-05-03
O_O no sabia eso, me bajo ya mismo el 8.04, ya que tuve que formatiar mi pc y se "ñexio" mi ubunto, asi que mejor me bajo el hardy heron.

gracias por el dato GREER.

saludos

meldon12

---

### Post by meldon12 on 2008-05-03
una pregunta chicos, como mi pc es de esas viejitas con 256Mb de ram, quisiera instalar el Xubuntu, pero nose si es igual a lo hora de instalar el modem, ¿los pasos son los mismos que en ubuntu? ¿los comandos tambn lo son?

saludos y gracias de antemano.

meldon12

---

### Post by eivar on 2008-05-05
Hola meldon12 en teoría los pasos deberían ser los mismo salvo por alguna herramienta gráfica que depende el entorno de Ubuntu (Gnome).

Nos cuentas como te fue con el Xubuntu.

Saludos.

---

### Post by thebestboy2671 on 2008-07-17
Hola que tal a todos, en especial a greer por la excelente guía, pero tengo un problema greer, tal y como dices:

> **greer said:**
> lo unico que haria falta seria configurar la interface el cual necesita el paquete que se menciona en la guia br2684ctl_200402261_i386.deb y seguir los pasos para la creacion de la interface...


Ya tengo mi módem sincronizado y todo lo demás, lo que me falta es configurar la interface, pero hay un problema y es que como mi portátil vino con el win vista pre-instalado, el módem que yo uso (zhone de c&w) no le funciona al vista, así que, no puedo obtener lo que son las dns, puerta de enlace, etc desde mi portátil. ¿Entonces cómo le hago para obtener esos datos? Gracias y saludos.

PD: Tengo otra pc con win xp, la cual usa actualmente el módem zhone de c&w, he intentado configurar la interface con los datos de esta pc, cambiándole solamente la ip por la de mi portátil, pero nada todavía.

---

### Post by thebestboy2671 on 2008-07-17
No lo puedo creer!, ya estoy navegando en internet con mi ubuntu gracias a gente como ustedes, lo que me faltaba era configurar mi interfaz utilizando los pasos del punto #8 de [esta página]("http://birriandoanime.blogspot.com/2008/01/slackware-c-adsl-plug-v20.html") y seleccionando la opción ipv4ll en Sistema>Administración>Red. Saludos.

---

