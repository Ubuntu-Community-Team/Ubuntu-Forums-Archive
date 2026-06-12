---
title: "No me aparece el menú de SALIR + Password de Root"
date: 2010-03-17
forum: Centroamerica Team
---

### Post by sol03 on 2010-03-17
Hola,

Es la primera vez que installo Ubuntu en cualquiera de sus versiones y  soy un usuario principiante. Yo trabajo en la oficina con otra  distribución (como usuario final) y decidí instalar Linux en casa para  conocer mejor el entorno. En el Menú de Inicio en Sistema no me aparece  el Menú de Salir, ni botones u opciones para apagar, cerrar sesión,  reiniciar, etc. ¿cómo puedo llevar a cabo estas tareas que no sea con  los botones de apagado o comandos de cónsola?.

Adicionalmente me gustaría saber el password por defecto de root cuando  se instala desde el CD porque aunque tengo un usuario administrativo no  es el root.

Perdonen mi ignorancia pero es mi primera vez.

Gracias de antemano por la ayuda,

SA
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=8984284") 		 		  	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] 			[]("http://ubuntuforums.org/editpost.php?do=editpost&p=8984284")[IMG]http://twitter.com/favicon.ico[/IMG][IMG]http://www.google.com/favicon.ico[/IMG][IMG]http://static.smarterfox.com/media/wiki-favicon-sharpened.png[/IMG][IMG]http://static.smarterfox.com/media/popup_bubble/oneriot-favicon.ico[/IMG]

---

### Post by riomacho on 2010-03-19
Hola, en Ubuntu no se usa el root, excepto en casos muy especificos.  Es una question de seguridad. Pero se usa mucho el "sudo" en terminal. Para alterar preferencias u instalar paquetes (programas).  El password para sudo es el mismo del usuario.  Si el sistema solo tiene un usuario, estaria en la lista de "sudoers" y se puede usar sin problema.  Si crea nuevas usuarios tiene que darles permiso via esta lista para usar el sudo.  

Adjunté un screenshot de mi panel, allí es donde debe incontrar la forma de salir.  En mi caso es un boton que sale en la esquina derechas superior y ala par es el nombre de usuario.  Se ve diferente dependiendo la tema que tiene instalado.  Si lo encuentra, entonces haciendo un clic con el mouse boton de la izquierda aparece las opciones de suspender, apagar o logout del sistema. 

Si no lo encuentras, hay varias formas de apagar, dependiendo de las preferencias.  
-  cntrl + alt + del.  
- Presionando el boton del PC.  
- en un terminal :   sudo halt 

Si no esta en el panel, entonces se puede agregar.  Haga un clic derecho con el ratón y seleccione "agrege a panel" Alli puede escoger un boton para apagar, o un boton para salir o cambiar de usuario.

---

### Post by riomacho on 2010-03-19
Agregando -  en el dialogo de agregar a panel, hay uno que dice "applet de indicador de session"  Esto es el original que le permite salir, cambiar de usuario, apagar, etc.

---

