---
title: "Linux !!! me salvo windows!!!!"
date: 2008-05-29
forum: Comunidad
---

### Post by rxx266 on 2008-05-29
Me agarre un virus *****, una variante de bagle, me contagie por emule, automaticamente luego de la infeccion deja inoperante todas las protecciones instaladas,no permite que se ejecuten ni tampoco volver a instalarlas:

KPF sunbelt (firewall)
Nod32 antivirus
Spybot
Avg antispyware
Combofix
SDFIX
Spysweeper

Todas estas aplicaciones quedaron disfuncional,segui con un programa que se llama hidden finder examina procesos ocultos  barbaro lo veia,entonces pense:... jajaaj te cagué .... cuando le di kill, ¿saben lo que paso? el mismo virus me cerro la aplicacion,lo volvi abrir , error... me tire por los scanner online,tampoco no los detectaba,process explorer ni por las tapas lo veía.
El sistema de recuperacion no la podia usar, porque estaba infectada con copias en la carpeta system restore file,no me quedaba otra, que usar combo fix y sdfix pero estas aplicaciones solo funcionan, en Modo Seguro, cuando apreto f8 elijo modo seguro,saben que pasó charan charan pantalla azul STOP 0x00000b7, ******* virus!!!!, y como ultimo paso dije: Dios mio que hago ahora, segui con la consola reparacion y no sirvio, solo ejecuta comandos,y no puede usar programas, asi que chau sdfix y combofix (esta aplicaciones buscan virus desconiciods rootkitss etc).Entonces me prepare un cafecito me relaje y dije: ...y si uso linux para desinfectar windows... inicie linux (ubuntu), me baje F-prot, lo instale, y tiré en la shell la siguiente linea de comando:

sudo fpscan -b --exclude=/media/SISTEMA/Documents* /media/SISTEMA

antes puse fpscan /? y de ahi vi todas las funciones de scaneo, las voy a explicar:

-b significa, que sacanee en el sector de booteo, tambien use la opcion excludes porque sabia que ahi estan los keygen,seriales mas que seguro me lo ivan a detectar como virus, y son solo falsos positivos por eso la exclui pero sabia que en los demas directorio sobre todo C:\windows ahi esta el mayor caldo de virus
Era hermoso lo bien que hacia el trabajo ese antivirus, habia carpetas, y archivos totalmente ocultos y este antivirus fue capaz de detectarla y eliminarlas.
Termino el proceso elimino todo, y arranque windows y fue magia limpito y totalmente funcional, lo unico que tube que hacer es reinstalar el driver de la placa de red.

PD:Que me deja esta experiencia, es que jamas desde windows iva a poder recuperar el sistema,ninguna de las aplicaciones mencionadas, ni metodos sirvieron, y desde linux me tomo solo 15 minutos resolverlo, con 1 sola aplicacion.Suerte espero que les haya sido util mi post.

---

### Post by madelaki on 2008-05-29
Que se le dice al hermano mayor, ventanitas? Que se dice?
Yo que vos lo dejaba ahi tirado :)

---

### Post by valucha on 2008-05-29
[COLOR="DarkOrchid"]"... entonces ahora me decidí a usar este robusto sistema operativo, libre de virus, de keygens y cosas irrecuperables"..

Ehh ah!.. hu, no dijiste eso :(..

;)[/COLOR]

---

### Post by jpmorelli on 2008-05-29
El hombre es el único animal que tropieza dos veces con la misma piedra...
Para que seguir con Windows si de un momento a otro te deja a pata por cualquier vulnerabilidad que ande dando vueltas.
Usá el linux !!!...y no me digas que te ponés a bajar con emule, bajá con Amule :) :lolflag:

---

### Post by rober-mpp on 2008-05-29
Me alegro que Ubuntu te haya ayudado a resolver mas problemas. Lamentablemente te vas a seguir cruzando con muchos mas de ellos, sobre todo si usas w1n2. Opciones de software libre sobran, asi como mencionaron el amule, hay para cuanto programa propietario conozcas. Espero que este thread contagie a mucha mas gente a usar Ubuntu o cualquier otro GNU/Linux. 

Y si, era de esperar, como el papa no va a ayudar al hijo... :P

---

### Post by faktorqm on 2008-05-29
Yo te diria, que utilices mejor los recursos de tu pc, y no los gastes en antivirus, anti-spyware, protecciones para windows, etc. 
Te cuento algo gracioso, como mis clientes tienen windows, aparte del linux tengo un xp con drivers y office, no tiene NADA mas, para probar algunos programas o hacer los tp's con los nabos de la facultad que todavia estan con windous. Entre pito y flauta actualice al kernel blabla y el otro dia, voy a arrancar el windous para ver una cosa, y ¡no podia arrancarlo! y me empece a reir solo, por que no era que tiraba error, volvia al grub siempre como si hubiera reiniciado la pc, volvia el contador, volvia todo. ¡¡Era una señal celestial!! o algo asi. no debia arrancar eso...

Asi que nada, fui al menu.lst y como perfectamente habia dicho HEI KU, se puso una configuracion de cero y me liquidó mi ordenado menu.lst. (debí haberte hecho caso hei...) asi ke todo mal. 

Amule anda perfectamente, tiene sus bugcitos, pero va josha. Salu2!

---

### Post by Hei Ku on 2008-05-29
> **faktorqm said:**
> 
Asi que nada, fui al menu.lst y como perfectamente habia dicho HEI KU, se puso una configuracion de cero y me liquidó mi ordenado menu.lst. (debí haberte hecho caso hei...) asi ke todo mal. 

Me parece que me debes una estrellita.... :lolflag:

---

