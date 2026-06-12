---
title: "no puedo entrar a hotmail.com y al messeneger (amsn)"
date: 2009-02-22
forum: Colombia Team - Colombia
---

### Post by rechazado on 2009-02-22
wenas

tengo un problema que desde hace dias no e podido solucionar:(


tengo la vercion de ubuntu 8.10 y desde hace dias

intento ingresar a la pagina  [www.hotmail.com](www.hotmail.com)  y lo que pasa es que se queda cargando y nunca carga la pagina 

en resumen no me deja entrar

y bueno yo para ingresar al messenger utilizo el amsn  y tambien cuando ingresar se blokea el amsn:(  

y al principo pense que era problema del amsn haci que me puse a buscar en el tio google y pues hize algunas cosas para mejorar el amsn pero seguia el mismo problema

asi que instale desde synaptic el emesene que es mas liviano

y cuando uba a iniciar seccion, veo que me seguia el problema tamben se blokeaba, asi que por lo que veo el problema es entrar a hotmail.com:(

en resumen el problema es que no puedo entrar a hotmail.com desde ubuntu

alguien sabe como lo puedo solucionar poruqe ya no se como lo puedo hacer


se lo agradesco de antemano

saludos a todos

---

### Post by Rohen on 2009-02-22
Si puedes navegar la Web sin probs entonces no es Ubuntu que causa el prob.  Intenta:

1. Entrar a MSN desde otro comp.
2. Entrar a alguna otra cuenta de correo como GMAIL.
3. Borrar los cookies, cache, sesiones activas, historial, de Firefox e intenta de nuevo (CTRL+ALT+DEL)
4. Intenta usar Pidgin

---

### Post by rechazado on 2009-02-22
> **Rohen said:**
> Si puedes navegar la Web sin probs entonces no es Ubuntu que causa el prob.  Intenta:

1. Entrar a MSN desde otro comp.
2. Entrar a alguna otra cuenta de correo como GMAIL.
3. Borrar los cookies, cache, sesiones activas, historial, de Firefox e intenta de nuevo (CTRL+ALT+DEL)
4. Intenta usar Pidgin


a si es puedo navegar tranquilamente a cualquier pagina menos a la de hot mail

a gmail me deja entrar, a yahoo, tambien,:(

creo que es un problema de ubuntu porque tambien intente con otro navegador y no me abre hotmail.com

y para conectarme y chatear con mis contactose intentado con amsn y emesene y ninguno de los dos me deja conectarme:( se bloquean


creo que a nadie le a pasado este problem

gracias men

---

### Post by Rohen on 2009-02-24
Hmm no se viejomen usas Router? Como te conectas al Internet?

---

### Post by rechazado on 2009-02-24
yo me conecto a traves de un modem

 no tengo INTERNET  inhalambrico :mad:


alguien me avia dicho que prodria ser problema de router y que lo reseteara.

pero yo no tengo de eso 


saludos

---

### Post by Rohen on 2009-02-24
Podrias reinicializar la configuración de la RED:

```
sudo apt-get remove-purge network-manager net-tools
```

Reinicia el PC, ahora reinstala la RED con:

```
sudo apt-get install network-manager net-tools
```

---

