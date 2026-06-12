---
title: "Windows software y Ubuntu"
date: 2007-12-04
forum: Ecuador Team
---

### Post by compuniversal on 2007-12-04
Hola, el problema que tengo es el siguiente. Bueno varios problemas pero creo que se pueden arreglar.
Dentro de mi trabajo todas las maquina trabajan con Windows pero uno como revelde le instale Ubuntu 7.1  la mia. El problema que tengo es que tenemos dos sitemas diseniados exclusivamente para lo que se hace en la compania donde trabajo, entonces me dije bueno instalo Ubuntu y luego instalo VirtualBox y los hago correr alli los programas. Ahora la cosa es que ya instale VirtualBox pero cuando estoy dentro de el no puedo ver las demas computadoras que estan dentro del network. Con Ubuntu si puedo ver todas las maquinas pero no puedo entrar a los folder compratidos y todo lo demas. La cosa es que necesito instalar tambien una impresora que esta dentro del network, osea instalar una impresora compartida por otra maquina. Asi mismo dentro de VirtualBox poder ingresar a las otras maquinas del Network Local.

Gracias por su ayuda de antemano :)

Ubuntu Rock's:guitar:

---

### Post by hubuntu on 2007-12-06
ya probaste wine para correr las aplicaciones?

[http://www.winehq.org/](http://www.winehq.org/)

R

---

### Post by compuniversal on 2007-12-07
Buenos ya solucione lo del problema del systema con Wine ahora la cosa es que como tenemos una data base en una computadora que hace de server en nuestra oficina, este programa se conecta a la data base a travez de una map network, bueno asi lo realizaba en win.

El nuevo problema que tengo ahora es que tengo el server y 4 maquinas mas con win y la mia con ubuntu 7.1, pero desde las maquinas con win si puedo ver los folders compartidos de mi maquina de Ubuntu pero viceversa no, osea desde ubuntu a windows no puedo ver los folders compartidos. Gracias a este [manual de Samba]("http://www.guia-ubuntu.org/index.php?title=Samba") puse ver los folders compartidos de mi maquina de Ubuntu.

Pero el grande problema es poder ver de mi maquina de Ubuntu a las de Wndows que si tienen folders compartidos, si tienen full access, estan todas dentro de una misma area local y tienen ip consecuticas 192.168.0.......... Todas conectadas a travez de un Switch D-link.

Espero alguien me ayude :popcorn:

---

### Post by hubuntu on 2007-12-14
Lo que tienes  que hacer es adherirte al mismo workgroup de las otras máquinas y con eso puedes ya ver las carpetas compartidas. Prueba red (Network) bajo nautilus y ve si puedes ver a otras máquinas aparte del servidor.

Puedes también colocar a esas máquinas como "servidores". Para eso necesitas poner la IP y el nombre de usuario de acceso, pero esto debería ser innecesario si están en el mismo grupo de trabajo. Usa CIFS: [http://linux-cifs.samba.org/](http://linux-cifs.samba.org/) para automontar las carpetas compartidas como locales :) - este tutorial está tb bueno(inglés): [http://www.debian-administration.org/articles/165](http://www.debian-administration.org/articles/165)

Es el servidor de terminal, de dominio o simplemente de archivos e impresoras?

Si es de terminal usas Linux terminal Server para conectarte. Si es de dominio usas windows-auth. El acceso a archivos e impresoras ya está según tengo entendido.

---

