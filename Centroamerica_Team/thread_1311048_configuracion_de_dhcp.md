---
title: "configuracion de dhcp"
date: 2009-11-02
forum: Centroamerica Team
---

### Post by yariel on 2009-11-02
si buenas tardes a todos 

si estoy configurando un servidor dhcp en linux para que reparta direccion ip  ya hice todo le procedimiento pero no reparte direccion ip mi pregunta es si la tarjeta de red que esta integrada al board no tiene esa opcion de repartir direccion ip o tendria que comprar una TARJETA EN EPSECIAL O SI ME PUEDEN DECIR LOS PASOS PARA configurar la direccion ip 

tengo un motherboar  1366  modelo dx58S0  INTEL


le agradeceria su respuesta seria de mucha ayuda. ya que soy nuevo en esto de linux y estos dias monte un servidor web con linux y le agredezco mucho a los que me ayudaron en este trabajo

---

### Post by Nugar on 2009-11-02
Hola Yariel,

Yo no soy experto en estos temas, pero me gustaria saber un poco mas.

Por ejemplo, estas configurando un servidor web, correcto?

Ese servidor quieres que "reparta" direcciones IP? No entiendo qué quieres hacer.

En realidad, tu debes tener por ejemplo un router o switch que es el encargado de repatir los IP y el directorio adquiere una mediante dhcp.

Ahora, puede ser que quiereas hacer alguna otra cosa, como configurar un NAT, por ejemplo. Para eso necesitas que la maquina que hace de server tenga dos tarjetas o conexiones de red.

Cuentanos mas de lo que quieres hacer especificamente a ver si alguien aqui logra orientarte...

Saludos,

---

### Post by adrianlancer on 2009-11-02
bueno nugar si puedes configurar gnu/linux a trabajar como router y firewall a la vez tambien como control parental. pero es un pokito complicado por lo que he leido y si nesecitas 2 tarjetas de red (si no me equivoco) pero si estas trabajando con cwp entonces el router que ellos proveen ya se encaga de repartir ip's privados cuentanos un pokito mas de repente alguien se le prende el foco ;)

---

### Post by Nugar on 2009-11-02
Hola Adrian,

Bueno, en realidad es Yariel quien quiere hacer eso ;)

Yo recuerdo que una vez monte un mini servidor linux. Usaba una distribución linux que no recuerdo como se llamaba. Creo que era Mandrake Firewall o algo asi.

Se usaban dos tarjetas de red, una por la cual entraba la señal de Internet y otra que iba a la red. Recuerdo que hacia de NAT, servidor dhcp y tenia la opcion de ser servidor web y de pop3. Pero esa distribucion duro poco siendo gratuita. Luego habia que pagar por ella y costaba mas de US$1,000!!!

Ahora lo que hago es que tengo un Linksys WRT54G, le flashie dd-wrt, que es otra distribucion linux especial para routers/switchs y listo :)

Pero es importante saber entonces que es exactamente lo que yariel desea hacer para ver como podemos ayudarle.

Si lo que quiere es que el servidor haga de NAt ademas de ser servidor web y de correos, habria que buscar a ver que distribucion le sirve. De pronto Ubuntu server...

---

### Post by yariel on 2009-11-03
buenas tardes si lo que pasa es que tengo un  modem de cwp
tengo un router linkys pero  las computadoras se estan consumiendo todo el ancho de banda. lo que queria hacer. es que escuche en un foro que tu puedes montar un servidor  dhcp y y a la vez bajarle como un NAT para dividr el ancho de banda ok ya una tarjeta de red esta configurada para conectarse a int ernet pero no logro que reparta dhcp hacias las computadoras

---

### Post by Nugar on 2009-11-03
Cual router Linksys tienes? Dependiendo de eso, puedes hacer algo mejor: flashearlo con dd-wrt y especificar cuanto ancho de banda le toca a cada equipo.

---

### Post by z-itou16 on 2009-11-06
Buenas yariel,

Ya tienes el daemon DHCP iniciado?

---

