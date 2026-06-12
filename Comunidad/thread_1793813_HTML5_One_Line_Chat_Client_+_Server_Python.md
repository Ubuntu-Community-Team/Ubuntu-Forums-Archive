---
title: "HTML5 One Line Chat Client + Server Python"
date: 2011-06-30
forum: Comunidad
---

### Post by juancarlospaco on 2011-06-30
**[SIZE="4"]HTML5 One Line Chat + Server Python[/SIZE]**

Bueno lo comparto por si alguien le sirve el aporte, el paquete consiste de:

[LIST]
[*]1 Cliente de Chat HTML5 de 1 Linea.
[*]1 Cliente de Chat HTML5 Completo, con deteccion de Conectividad, Eco Local, AntiSpamm en HTML5, Limita Chats a mas de 4 caracteres y menos de 140.
[*]1 Chat Server puro Python, de linea de comando, independiente.
[*]1 Web Server para Chat, de linea de comando, independiente., basado en Bottle.
[/LIST]

Todo Libre, todo en Castellano, todo independiente y minimalista, 
**si podes agregar 1 Linea a tu Blog o IntraNet ya podes tener Chat.**

La idea es mas o menos asi:

[LIST=1]
[*]El Web Server para Chat inicia el servicio de Chat Server, 
[*]el Web Server sirve la pagina client.html desde donde chatear,
[*]el client.html se conecta al Chat Server donde todos chatean.
[/LIST]

El Web Server es solo para Servir la pagina, si abris el client.html solo ya anda,
si tiene conectividad con el servidor de chat obvio, sino indicara DESCONECTADO.

No es obligatorio usar mi Web Server, ni siquiera es necesario un Web Server.
Podes Guardar, o enviar por mail el client.html y andara al hacerle Doble Click.
Client.html No tiene Autenticacion, ni password, ni nada, no pesa nada.

Las features de Client.html son:

[LIST]
[*]Deteccion de Conectividad con el Servidor de Chat.
[*]Eco Local
[*]Anti-Spamm 
[*]Solo permite mensajes de entre 4 y 140 caracteres para Anti-Flood
[*]Se puede usar solito, y se puede meter adentro de un <iframe> </iframe>
[/LIST]

Las features de onelineclient.html son:

[LIST]
[*]Minimalista, Detecta conectividad por un PopUp.
[*]Solo envia mensajes Pre-Definidos ( **I Like Ubuntu! **en este caso)
[/LIST]

Lo bueno del Chat Server es que tiene un Debug en la Bash que es amigable
 y ayuda a entender bastante como funciona todo, incluido las conexiones:

Uso del Software y Debug que produce [SIZE="1"](aprox)[/SIZE]:
```

juan@natty:~/chat-html5$ **python webchatserver.py**

Bottle server starting up (using WSGIRefServer())...
Listening on http://127.0.0.1:8000/
Use Ctrl-C to quit.

 No PYTHON-PSYCO avaliable... 
 Starting Python HTML5 Chat Server on 
 linux2 with 2.7.1+ (r271:86832, Apr 11 2011, 18:05:24) 
 [GCC 4.5.2]
 Using Local Port TCP/9999
localhost - - [30/Jun/2011 02:01:28] "GET / HTTP/1.1" 200 
 Connected from ('127.0.0.1', 59066), Hello!
 TCP 3-Way HandShake on Port 9999 in progress...
 Waiting Data from ('127.0.0.1', 59066)...
 OK!
 Incoming Chats from ('127.0.0.1', 59067) said "hola"
 Waiting Data from ('127.0.0.1', 59067)...
 OK!
 No Data
 Client Disconnected:('127.0.0.1', 59066), Bye.
^C 
Shutting down...
juan@natty:~/chat-html5$

```

**[SIZE="3"]Uso:[/SIZE]**

Como se ve aca arriba, se descomprime, se ejecuta en la misma carpeta desde la Terminal:
```
**python webchatserver.py**
```
Abris el navegador web y ingresas a: **[http://127.0.0.1:8000/](http://127.0.0.1:8000/)**

**Chatea!** *[SIZE="1"](podes abrir otra pestaña igual y chatear con vos mismo, bien ForEverAlone jiji)[/SIZE]*

**[SIZE="3"]Browsers:[/SIZE]**

Funciona con Chromium, y navegadores basados en WebKit[SIZE="1"] (KdeHTML)[/SIZE], tambien en Opera,
no esta funcionando al momento de redactar esto en Firefox, por que el motor no lo soporta,
no tengo ni idea si funciona en algun IE, no tengo Windows, y tampoco me quita el sueño...

Gracias a Eduardo Zúñiga por la REGEX y a la Docu de Google.
*[SIZE="1"]Parte de Programacion: HTML5+CSS3+Python+Bottle.[/SIZE]*

**[SIZE="3"]Screenshots:[/SIZE]**
[*Incrustado en una Web usando un iFrame*]("http://file.status.net/i/identica/juancarlospaco-20110627T214149-a4llvjr.jpeg")

---

### Post by juancarlospaco on 2011-06-30
Aca meto el archivito por que arriba no me dejo; cualquier consulta pregunten...

Como **user**: **Local** en Puerto **8000**; como **root**: **WorldWide** en Puerto **80**
El Client.html y el onelineclient.html necesita apuntar a IP o URL del Chat Server, 
para saber donde hay que editarlo, hacer en la Terminal:
```
cat client.html | grep localhost
```

---

### Post by guillermolisi on 2011-06-30
Muy bueno Juanca !

Gracias por compartirlo y por el aporte !

---

### Post by mama21mama on 2011-06-30
si funca.  lo que no se por que dice...

```
No PYTHON-PSYCO avaliable
```

---

### Post by juancarlospaco on 2011-06-30
> **mama21mama said:**
> no se por que dice...

```
No PYTHON-PSYCO avaliable
```

[sudo apt-get install python-psyco]("apt:python-psyco") 
Completamente Opcional, Anda un poquitito mas rapido con eso (no perceptible a simple vista).

Cuenten si lo usan para algo, si andubo, y si les gusto!  :D

---

### Post by mama21mama on 2011-07-01
Si me gusto... lo probé.

---

### Post by juancarlospaco on 2011-07-03
Algun dia lo tenia que hacer, espero seguir la costumbre:

[http://bazaar.launchpad.net/~juancarlospaco/+junk/webapps/files/head:/chat-html5/](http://bazaar.launchpad.net/~juancarlospaco/+junk/webapps/files/head:/chat-html5/)

Tambien hay un sitio entero Python+Bottle ahi, un brainlesstorm,
OpenID middleware login, Session, GAE, Wiki, Disqus, Chat, HTMLtoPDF, PyWAPI, etc

---

### Post by RubenOrtiz on 2012-06-22
Hola

Me puede ayudar a saber de esto: 


 Starting Python HTML5 Chat Server on
 linux2 with 2.7.2+ (default, Oct  4 2011, 20:03:08)
[GCC 4.6.1]
 Using Local Port TCP/8002

 TCP 3-Way HandShake on Port 8002 in progress...
Exception in thread Thread-2:
Traceback (most recent call last):
  File "/usr/lib/python2.7/threading.py", line 552, in __bootstrap_inner
    self.run()
  File "/usr/lib/python2.7/threading.py", line 505, in run
    self.__target(*self.__args, **self.__kwargs)
  File "/var/www/chat-html5/server/chatserver.py", line 51, in handle
    s.send(create_handshake_resp(data))
  File "/var/www/chat-html5/server/chatserver.py", line 39, in create_handshake_resp
    spaces1 = key1.count(" ")
UnboundLocalError: local variable 'key1' referenced before assignment

gracias

---

