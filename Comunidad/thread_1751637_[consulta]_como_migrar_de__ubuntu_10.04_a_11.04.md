---
title: "[consulta] como migrar de  ubuntu 10.04 a 11.04"
date: 2011-05-06
forum: Comunidad
---

### Post by eberfalu on 2011-05-06
hola soy meio nueo en esto, y queria saber si alguno me puede decir si es q se puede cargar ubunut 11.04 sin perder las cosas y paquetes instalados en mi ubuntu 10.04, de ser asi como se hace, y si no se puede con cual me aconsejan quedar....
desde ya muchas gracias.

---

### Post by joseluis on 2011-05-07
si..se puede y mucha gente lo hizo y fue bien.Cuando pones para instalar el cd de instalacion te pone una imagen que te dice qué tenes instalado (win, ubuntu 10.04, etc) y te pide que optes por una. haciend click sobre la correspondiente, te instale sobre la 10.04 manteniendo configuraciones.
[http://sliceoflinux.com/2011/04/29/actualizar-a-ubuntu-11-04-paso-a-paso/](http://sliceoflinux.com/2011/04/29/actualizar-a-ubuntu-11-04-paso-a-paso/)

Lo que me gustaría si alguien puede responder si esto vale también para pasar de 10.04 de 32 a 11.04 de 64 bit. Si todo va bien en ese caso.

---

### Post by gmunioz on 2011-05-07
1- No es aconsejable, hacerlo de 10.04 a 11.04, teóricamente habría que pasar primero por la 10.10. Sin embargo lo he realizado algunas veces (prefiero instalaciones limpias en general) mediante el alternate-cd, es necesario desactivar todos los repositorios desde synaptic, recargar para que solo queden marcados en él, los paquetes instalados y luego introducir el alternate-cd, este inmediatamente solicitará permisos para actualizar el sistema.

2- No se puede de 32 a 64 o viceversa, se pueden cambiar los motores de un fiat 600 y de un fiat 1100 por otros similares más modernos o menos destruidos, pero nunca poner el del 600 en el 1100 o el del 1100 en el 600.

---

### Post by joseluis on 2011-05-07
gmunioz, pero lo sugiere el mismo menú de instalación, en una de sus opciones está claro. De hecho casi lo hago pero preferi hacer como decis una instalacion limpia hace un par de dias. Pero que el menú de Ubuntu lo dice, eso no lo dudo. Y si lo dice es porque seguramente está pensado para hacerlo.

---

### Post by eberfalu on 2011-05-08
gente MUCHISIMAS GRACIAS, sinceramente no habia probado, de hecho aun no baje el cd...pero de ser de esta manera es muy probable que me actualize. ahora solo quiero preguntar, que es mas convniente que me quede con el 10.04 o emire al 11.04???? y porq me decian q es mejor hacer una instalacion limpia???? corro algun riezgo? porq de ultima si tengo mala suerte los datos estan en otra particio.

---

### Post by cespinal on 2011-05-08
Siempre aconsejan instalaciones limpias para cubrirse un poco las espaldas. Ademas... siempre hay un riesgo de que la compu se te quede sin conexion o se apague durante la actualizacion..con resultados desastrosos.. 

el 11.04 vino con algunos bugs asquerosos apenas salio pero ya los han ido resolviendo. Si tu version te funciona perfectamente, yo esperaria tal vez un mes mas a que vengan mas actualizaciones y luego pruebas. 

11.04 en lo personal me ha gustado mucho y siento que es la manera como ubuntu deberia diferenciarse de los demas... yo te aconsejaria que lo preuebes a ver que tal...

---

### Post by joseluis on 2011-05-08
yo tuve que actualizar (desde  instlacion limpia) en mi notebook, que tenia 10.04 a 11.04 solo porque había un problema en  drivers de video, algo que muchos habian reportado para la Lenovo. Si no fuera por eso no lo hubiera cambiado. 
En cuando a mi pc de escritorio, en este momento voy a migrar a 11.04 desde 10.04 porque se me j***ó algo de fstab y no se que cosas, asi que prefiero limpiar todo. Como tengo la home en otra particion no creo que pierda nada. Igual tengo copia.

Bueno..suerte...

---

### Post by EnriqueK on 2011-05-08
Para migrar en forma limpia y segura a cualquier versión ya sea de 32 o 64 bits, sería la siguiente:
1.- En tu acatual instalacuón ejecuta el siguiente comando
dpkg --get-selections | grep -v deinstall > paq.txt
Se va a crear el archivo paq.txt en tu carpeta de usuario que contiene la lista de todos los paquetes instalados en tu actual sistema,  se trata de un listado sin especificar la cersión de los paquetes, por lo tanto sirve para usarla en la instalación en otro totalmente difetesnte, por ejenplo yo instalé Debian 32 bits basado    en una lista de Ubuntu 64 bits   ,
2.- Haz una instalación de la nueva versión , habilita todos los repositorios equivalentes para la nueva versi´on , entras a Synaptic -->Archivo --> Leer seleccuines, doble click sobre el archivo paq.txt  generado en la instalación anterior , seguidamente selecciona Filtros --->rotos , a la derecha te aparecerán todos los paquetes con problemas, los seleccionas a todos y los eliminas , --->Aplicar, acepta todo lo que te pida y a esperaaaaaar , cuando termine vas a tener una instalación limpia con todos los paquetes que correspondan a la nueva versión.

---

### Post by biale on 2011-05-08
Personalmente yo no recomiendo tocar una instalacion que esta funcionando bien sin antes hacer un buen backup de todo, incluyendo las areas de sistema. Mi idea siempre es hacer una instalacion limpia en algun pequeño lugar apartado del disco y probar con tranquilidad todo lo que valga la pena.

Mi segunda regla es esperar un par meses. Observo que ese es mas o menos el tiempo que tardan en estabilizar bien cada release, y si se trata de una version LTS a veces hastan tardan mas (?).

Encuentro a la idea de Enriquek ideal para trabajar dentro de una misma version, por ejemplo para pasar en forma facil de 32 bits a 64 bits y viceversa. Pero cuando se cambia de version tambien hay gente que no la recomienda. Puede suceder que un paquete haya cambiado de nombre, y en ese caso no instala nada. Tambien cambian los paquetes recomendados, etc.

En fin, son solo ideas mias y no la verdad absoluta, las experiencias son variadas.

---

### Post by joseluis on 2011-05-08
Estoy de acuerdo. Y de hecho yo migré hoy con una instlación limpia de 10.04 a 11.04. Pero tuve que hacerlo porque en mi caso tenía algunos lios que me daba la impresión que no valía la pena arreglarlos. 
Siempre prefiero una LTS a las normales, pero no siempre se puede hacer lo que uno prefiere.
Por otra parte, contrariamente a lo que me suponía o imaginaba, me gusta mucho 11.04, con o sin Unity, es muy bueno. No tengo problemas hasta ahora, obvio que hace cuatro horas nada más que lo estoy usando. 
Ademàs, sabemos que es provisorio de alguna manera.

---

### Post by eberfalu on 2011-05-08
gente siempre dije que en los usuarios de ubuntu son excelentes personas y ayudan mucho mas que todo a los novatos como yo.
Les cuento q acabo de migrar a la 10.10 pero NO HICE INSTALACION limpia solo actualize, en lo personal hago eso porq me cueta arrancar de cero, por ejemplo hacer andar las radios on-line de arg, poder instalar el paquete necesaro para hacer andar el amarok y ciertas cosas q me cuestan aun pero me voy a quedar en la 10.10 y en un mes o dos voy a hacer una instalacion limpia de la 11.04 aunq me cueste...
Desde ya muchas gracias...

---

### Post by joseluis on 2011-05-09
felicitaciones!!!!

---

