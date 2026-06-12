---
title: "Analisis Open Suse + KDE 4.2"
date: 2009-01-31
forum: Comunidad
---

### Post by pol666 on 2009-01-31
Si, lo se lo se, es ubuntu forum, pero tal vez halla alguien que le interese leer mi articulo, Tambien hablo de KDE4.2.
		
		
		

		
[CENTER]**Introducción.**



*Este análisis juzgara los productos Open SUSE 11.1 Live CD y KDE4 el escritorio que posee, Inicialmente KDE 4.1.3 y mas tarde una actualización al nuevo KDE 4.2.0*



*Se partirá desde el booteo del CD, y finalizara cuando el sistema este configurado, optimizado y actualizado con el nombrado escritorio.  (Los puntos se tomaran de forma separada dependiendo si forma parte del equipo de desarolladores de KDE o de SUSE)*




*El sistema se instalara en un Intel Pentium D 3.00Ghz con 1gb de ram a 766mhz, La placa de vídeo es Nvidia Gforce 7300 LE a 512mb, y posee una Sound Blaster Audigy. Fue instalado en una partición Ext3 de 5.00gb sin montado de particiones especiales.*

[i]
 
[img]http://multanilinuxmall.net/images/744px-OpenSUSE_Logo.svg.png[/img]
[/i] 

 [/CENTER]

 **Previa al análisis**
 

 Cuando booteamos el CD nos encontramos con un grub y la opción de bootear el live de Open SUSE, en aproximadamente 1 o  2 minutos el escritorio de KDE esta listo, con una pantalla de introducción, Desde el live CD se puede comprobar que el sonido y la red funciona, La pantalla se ve bien pero sin acelaracion gráfica
 

 Comenzamos la instalación desde el asistente, vemos un nuevo asistente renovado muy completo y automizado, pero para usuarios novatos podría ser confuso, inclusive me costo encontrar la opción para encontrar las opciones de montaje y particionado que ya las había predefinido, eligiendo instalarse en el 2do disco rígido. (por que?). Edito las opciones a mi gusto, y continuo con la instalación, el tiempo de instalación fue breve aproximadamente 15 minutos, Se reinicia la computadora y automáticamente carga SUSE, no el grub, se ejecuta un checkeo de discos muy largo que duro un buen tiempo hasta que finaliza con un error, Debido a que persistio, Intente volver a ubuntu para quitar la comprobacion de discos automatica, estaba vez si cargo el grub pero arrojaba Error 15 al querer entrar en ubuntu, repare el Grub con Super Grub Disk, y modifique el fstab desde  ubuntu, luego, el sistema inicio a la perfeccion.
 
 Nota: Un novato no sabría hacer eso sin recurrir a un foro o a otro tipo de soporte luego, el problema si bien tiene solución significo una perdida de tiempo.
   

 Cuando iniciamos el sistema por primera vez, nos encontramos con el gestor Yast que hace un análisis de hardware, tarda aproximadamente 5 minutos y luego podemos logearnos.
 

 Carga el escritorio de KDE 4.1 bastante modificado en comparación de otras distribuciones, como Kubuntu o Fedora. Como detalle, hay aplicaciones varias en QT3 como el instalador, inclusive el mismo YaST!! también las aplicaciones en GTK como Firefox u Open OpenOffice se representan como QT3 debido al gtk-qt3-engine, aunque ya existe gtk-qt4-engine! Para poder integrarse en KDE4.  No representa un problema en sí, solamente un detalle que no permite lograr una integración de escritorio completa. 

 **Aceleración Gráfica.**
 

Los usuarios de placas nvidia, sabrán que es necesario drivers privativos para poseer aceleración 3D y poder gozar de efectos de kwin o compiz y acceder a resoluciones extras, como la que uso yo.
 

 Busco en YaST pero no encuentro ningún gestor de controladores restringidos como hay en Ubuntu, así que busco en google y en el primer resultado encuentro una posible solución, un instalador que se abre con el gestor de paquetes de YaST, por lo que se ve, el tiempo de instalación de un paquete es mayor al de un .deb. Luego me entere que no es un paquete como un deb sino un script para Yast, que no contiene software alguno, sino solamente las instrucciones para instalar dicho software (agregar repositorios, descargar, solucionar dependencias, instalar).
 
 Nota: De todos modos, todas las instalaciones de .rpms demoraron mucho mas que un paquete .deb en ubuntu o Debian.
 
 

 Los driver figuraban como instalados, y los efectos activados, pero así y todo no parecía funcionar glx, en mi ignorancia, trate de modificar el xorg.conf, pero al ver que todo fue para peor lo restaure,  
 el secreto se encuentra aparentemente en SaX2 la herramienta de configuración de pantalla, cambie mi configuración a 24 bit, y seleccione nuevamente ese checkbox para efectos de escritorio.
 Volví a reiniciar el entorno gráfico, y active Kwin, esta vez funciona.
 
 Nota: kdesu pide contraseña siempre para cada proceso administrativo, Aun cuando esta marcada la casilla de recordar contraseña. Supongo que tiene un tiempo de vencimiento muy corto, en kubuntu esto no sucede, suele ser una molestia para cuando uno usa Yast a cada rato 
 

 **Sonido**
 

 No estoy muy seguro como es la configuración de audio acá, si bien la placa es reconocida me intriga saber si reconoce el sistema de parlantes 5.1
 
 Abro el Kmix, y regulo el mezclador, pero seguía sin sonido surround, Siendo KDE no me imagine que tuviera Pulse Audio como trae ubuntu, pero me equivoque! Si lo tenia, y pude configurar los parlantes editando el archivo /etc/pulse/daemon.conf. Excelente trabajo de Novell, el incluir este mezclador de sonido en KDE. 

 Nota: me doy cuenta que es muy difícil trabajar en modo root con SUSE, no pude lanzar kwrite ni Dolphin en modo de super usuario, así que lo edite mediante Vim. No se si forma parte de una herramienta de seguridad o es un bug, pero me resulto muy engorroso.
 
Luego de instalar los codecs privativos, amarok 1 reproduce los mp3 a la perfeccion, con el deseado sonido 5.1 

 **Programas Adicionales**
 


 Luego de tener red, gxl, y sonido funcionando como debe y antes de actualizar a kde4.2, se instalaran algunos programas extra, como emesene,  wine, vlc, java para usar en Firefox y  ejecutar el  Jdownloader, flash 10, y no más software ya que el sistema tiene una buena cantidad de programas.
 
[list][*]Flash: Se instalo aparentemente con el paquete de codecs, tiene sonido y funciona bien en Firefox, en Konqueror no responde
[/list][list][*]Java: Lo instalamos mediante YaST2:  3 paquetes, la maquina sun-java, la compatibilidad con alsa, y el plugin para navegador. Java funciona en Firefox 3 y el Jdownloader se ejecuta sin problemas.
[/list][list][*]emesene: En repositorios se encuentra la versión 1.01, si bien esta des-actualizado, el programa funciona al 100%
[/list][list][*]Wine: Instalo correctamente pero no fue probado con ningún programa aun.
[/list][list][*]Vlc: Instalo de manera correcta, reproduce un .avi sin problemas.
[/list]

 

 

 **Instalación de KDE4.2**
 

 Voy a actualizar mediante Yast, agregando el siguiente repositorio.

 
 *[http://download.opensuse.org/reposit...openSUSE_11.1/](http://download.opensuse.org/repositories/KDE:/KDE4:/Factory:/Desktop/openSUSE_11.1/)*
 

  Hacemos una actualización, seleccionando (si lo deseamos) únicamente el escritorio de KDE. En ese momento me dio muchos problemas con dependencias que tenia que solucionar manualmente, luego de tanto insistir, hice una actualización particular, solo de kde4-base y luego solucione las dependencias, ahí pudo instalar.
  
  Una vez que reiniciamos nos encontramos con el flamante escritorio, ya con algunos cambios en plasma, un tema oxygen renovado,  y un menu mas integrado, Comienzo la personalización agregando un panel vertical ancho a la derecha de la pantalla, en forma de barra de widgets, luego lo configuro para que se oculte automáticamente y le agrego una cantidad de plasmoids, muchos nuevos  y otros renovados como las Sticky notes, mas tarde hablaremos de los plasmoids mas de cerca.
  

  El bug de la bandeja del sistema se soluciono, el de plasma y open OpenOffice, y también despareció el Plasma Crash que sucedía al reiniciar el entorno gráfico Por ahora no nos encontramos con bugs, ni errores fatales.
  Kwin no muestra mejoras a simple vista pero notamos en el kcontrol que tenemos nuevos plugins como el cubo de escritorio, el cilindro y también la esfera!, nuevos switchers de ventanas, Flip3D estilo Vista, y Cover Flow a lo OsX. De todos modos no presenta muchas opciones de configuración, no se puede usar combinaciones de mouse y teclado para hacer atajos de efectos como si se puede en compiz, y tampoco tenemos acceso a todas las configuraciones, un detalle curioso, el cubo se gira para la derecha con el cursor izquierdo, y para la izquierda con el derecho.
  
  No veo la posibilidad de usar Skydomes, pero por otro lado tenemos la ventaja de poder usar slideshows de wallpapers que cambian con el tiempo y Wallpapers animados, vemos una buena herramienta carente en otros escritorios como Gnome. Lamentablemente es opacado por la deficiencia que representa KWIN contra Compiz Fusion.
  

  Me olvidaba que los bordes de ventanas de Kwin no están a la altura de configuración de emerald. Y en caso de querer usar este, debemos usar Compiz, que sinceramente no vale la pena usar en KDE.
    
  
  Luego de mover accesos directos,  plasmoids, cambiar temas y colores, obtenemos un escritorio configurado, funcional y útil Podemos decir que esta a la altura de windows vista o OsX pero menos pulido.  
 Para finalizar, remplazamos el menu kick off por lancelot.
  
  

 ** Plasmoids**
  
[list][*] El menu lancelot es muy configurable, nos permite cambiar numerosas opciones y modificar el icono fácilmente
[/list][list][*] Sticky Notes: En esta versión se puede cambiar de color, de fuente, y de otras opciones de escritura para texto.
[/list][list][*] Estación meteorológica LCD: Se ve un poco feo visualmente, pero es efectivo, reconoció mi ubicación (buenos aires) sin problemas, y me mostró datos extra

[/list][list][*] Bandeja de notificación (systray): Se ve mejor que en 4.1 pero sigue teniendo pequeños bugs no agradables.
[/list][list][*] Vista de Carpeta (folder view): La novedad de este plasmoid es que se puede usar de escritorio completo, esto significa que pasa a gestionar los iconos y da como resultado un escritorio real de la carpeta Desktop, al estilo KDE3, o Gnome.
[/list][list][*] Barra de Tareas: No agrega muchas funciones nuevas, simplemente tenemos la opción de agrupar ventanas, o hacer la barra de doble entrada. Todavía no hay opción de dock, como el panel de xfce, e17, o a mayores rasgos, Windows 7.
[/list][list][*] Reloj Analógico: Al igual que el resto de la serie de KDE4, no se puede cambiar su aspecto independientemente del tema plasma. Lo que hace que no combine en el escritorio.
[/list][list][*] Bball: Si bien fue agregada, nunca respondio, no parece funcionar.
[/list][list][*] Monitor de Sistema: brinda un monitor de sistema completo, pero poco configurable, no brinda mucha información acerca del uso de memoria ram.

[/list][list][*] Contenedor de Extencion interna: No parece funcionar, o no comprendo su uso.
[/list][list][*] Vida: No parece funcionar, o no comprendo su uso.
[/list][list][*] Navegador Web Sencillo: Es útil, buena extencion de konqueror, me gusto.
[/list]
  Hay ciertos plasmoids que ya se probaron y funcionan correctamente, otros no significaron relevancia, por eso se hizo incapie en los plasmoids nuevos en 4.2.
  
 **Síntesis**

  

  Dando por finalizado este análisis, puedo juzgar nuevamente a open SUSE, luego de haber probado hace un año la version 10.3 la cual me había atraído por su excelente artwork y fue la única distribución en la que Kde3 me atrajo tanto. A pesar de ello, Yast me pareció demasiado lento (mucho mas que ahora, y eso es bastante). No había reconocido mi antigua placa de red, el asistente  de adsl no funcionaba y no había tenido éxito en la instalación de los driver nvidia.  
  

    En esta instalación esos errores habían desaparecido y se habían sumado otros, No me parece un sistema lento en absoluto, si me parece y acierto en que sus herramientas de configuración son lentas y pesadas, confirmo ya con otras experiencias que el sistema de paquetes Rpm, es mas lento que los .Deb.
  


  El trabajo en KDE que hizo el equipo de SUSE en 11.1 es menor que en 10.3 cuando usaba aun KDE3, no vemos muchas modificaciones, aunque si es una de las pocas distribuciones que se fija en el detalle de cambiar el icono del menu en kde (junto con mandriva), he probado Fedora, Kubuntu y Debian y todas dejan la tediosa “K”
  

  De todos modos esto no quita que el artwork de SUSE sea fabuloso, desde que ingresamos el live CD, todos los detalles gráficos están bien cuidados, todos!, el grub, el boot, el kde y el splash, todos están bien logrados y combinan armoniosamente con los verdes del escritorio.
  

  Vuelvo a re-formular mis criticas acerca de las aplicaciones QT3 presentes, pueden ser remplazadas, harían un buen trabajo si se portan a QT4.
  

  Por dentro lo note un sistema de poco acceso, muchas trabas para abrir los archivos en modo root, se nota a simple vista que se prefiere el uso de GUI'S y no ediciones de archivos, o comandos de consola. Pero hay que aceptar que ciertas veces son necesarios.
  
Gracias a eso, el sistema no esta pensado para desarrolladores ni expertos, faltan herramientas de compilación, o editores de texto avanzados, como por ejemplo Kate. Todas las herramientas de YaST parecen fáciles de funcionar, lo que lo convierte en un sistema amigable, lastima que errores serios como el sucedido con mi grub o con el gxl, opaquen esta facilidad de uso.
  

  El sistema se mantuvo estable siempre, pero con algunas caídas del entorno gráfico, y mas luego de actualizar a Kde4.2 que cuando se agregaban plasmoids, muchas veces este se solía trabar, y trababa el escritorio. En este momento si abrimos el monitor del sistema vemos que el proceso que mas consume es plasma (57mb), luego el Writer de Open OpenOffice, (54mb) Amarok (40mb), Lancelot!! (25mb), Krunner (24mb) Konqueror (23mb) curioso, por que que konqueror no esta abierto; kwin (23mb), Firefox (21mb) que poco!, dolphin (20mb) y python usado por el emesene (28mb) hay que aclarar que hay 5 conversaciones abiertas y 2 cuentas on-line.  


  Con el resto de las aplicaciones, Top nos dice que estamos consumiendo prácticamente la totalidad de la memoria ram, con solo 29mb libres, y mas de 980mb usados! Esto es muchísimo pero el sistema permanece estable y rápido de todos modos.
  Si cerramos todos los programas con excepción de Konsole, la memoria se libera a 300 mb libres, con prácticamente toda la swap libre. Siendo Plasma nuevamente el proceso mas pesado.
  
 **Puntaje Open SUSE:**
 
[list][*] Interfaz gráfica, artwork y personalización: 9. Si bien me gusta mucho, creo que podian sacar mas provecho a KDE4.

[/list][list][*] Estabilidad, Velocidad y Rendimiento: 8. Con el software por defectos, sin contar la actualización de kde o el software de 3eros, el sistema se mantuvo estable, sin caídas, o trabas. Si bien se llego a consumir casi la totalidad de la memoria ram, lo que no es bueno, la velocidad siguió siendo la misma. Por otra parte el sistema de configuración e instalación de paquetes es lento, y no me convence del todo.
[/list][list][*] Aplicaciones y software contenido: Me sorprendió que los repositorios estuvieran casi a la altura de Ubuntu o Debian, el único programa que no encontré fue fusion-icon, me hubiera venido bastante bien. El software por defectos es muy bueno, no se quedaron con las aplicaciones “only kde” como en kubuntu, sino que incluye Firefox y Open OpenOffice 2 programas de alta calidad. También los programas de KDE están recortados o modificados, incluye Kaffeine, K3b y Amarok en qt3, ademas de que la mayoría de programa de configuración del sistema esta en qt3. Por eso, la nota es 7 simplemente, podian mejorarlo.
[/list][list][*] Facilidad de uso y configuración;: Como ya dije, Yast representa una buena herramienta para de configuración, aunque hay cosas mal ubicadas y poco intuitivas, como el instalador, el gestor de actualizaciones o la configuración de pantalla. El sistema en sí es fácil, en algunas cosas mas fácil que ubuntu y por supuesto con mas GUI's que este. Cabe destacar que me sentí perdido en ciertas ocasiones y busque ayuda en la web para sentirme tranquilo. Por eso..7
[/list][list][*] Errores, Bugs, problemas: Los problemas que tuve no tuvieron explicación alguna, o sea no hay una explicación coherente para decirme por que el grub no tomaba la instalación de ubuntu, pero si la de Windows. Tampoco hay una explicación coherente para saber por que si se marcaba que se estaban usando los efectos, estos no aparecían, hasta que en determinada sesión si funcionaron.
[/list][list][*] Tampoco hay una explicación a los errores de dependencias al querer actualizar. Aunque tal vez estos representaron problemas propios de mi hardware, lo ocurrido con el grub fue grave, un usuario novato, hubiera entrado en pánico y posiblemente reinstalado, por eso: 5
[/list][list][*] Soporte y reconocimiento de hardware, El sistema reconoció mi hardware desde el inicio con el live CD, tuve sonido, Internet, y vídeo siempre, hay que aclarar que los controladores nvidia no están incluidos por un factor de legalidad, es aceptable dentro del software libre. Al contrario que ubuntu no me incito a buscar controladores restringidos, no se me notifico ni se me advirtió en ningún momento. Es un poco difícil que existe una opción como Mandriva One pero para Open SUSE, aunque no estaria nada mal. Por otra parte también me reconoció la impresora Lexmark X1100 (aunque solo funciona el scanner, igual que en ubuntu), el Monitor Samsum SyncMaster y mi reproductor de mp3. La nota es  7. Creo que era posible una herramienta de advertencia para los driver privativos.

[/list][list][*] Mejora frente a versiones anteriores, y otras distribuciones : Hasta hoy probé muchas distribuciones de linux, pero a fondo solo K/Ubuntu, Debian, Mandriva y Open SUSE Afirmo siempre que la mas profesional y efectiva es Debian, que conserve hasta el día que instale Open SUSE, Mandriva 2008 me dejo un sabor amargo con KDE3, pero con Gnome, logre un sistema totalmente diferente a lo que conocía, me gusto hasta que llego el momento de cambiar; mi paso por Kubuntu fue para asimilar a la fuerza el escritorio de kde, si bien kde3 no lo pude digerir, ahí fue cuando comen se a hacerme usuario de kde4, pero considere que kubuntu estaba por debajo de ubuntu, los desarolladores y diseñadores no intervenían en KDE, se centraban en su trabajo con Gnome, no me agrado eso y es la causa por la que decidí probar Open SUSE nuevamente. Open SUSE 10.3 no me dio oportunidad de juzgarla, y si lo hubiera hecho, habría sido un resultado muy bajo ya que no me andaba prácticamente nada, y obviamente si no hubiera hecho una evolución, hoy no estaria escribiendo este resumen. Claramente se nota que hubo un avance. Sigo manteniendo mi opinión acerca de las distribuciones, Ubuntu (con Gnome) sigue siendo la distribución mas equilibrada y sencilla que probé, me permite instalar y configurar en no menos de 1hs y es muy útil para usuarios nuevos. Por ahora SUSE me agrado mucho mas que Mandriva 2008, y estéticamente mas que todas. Por eso SUSE se gana el premio de **La distribución mas linda por default. **Por eso y por otras cosas mas .. un 8!
[/list]
  
[list][*] Comunidad, y Soporte en Internet: No estoy seguro si deba considerar esto como parte de la calificación, pero es una verdad que el publico forma parte del sistema operativo, No encontré muchos tutoriales ni ayuda en español, eso es muy importante para los usuarios novatos. No voy a puntuar esto, simplemente merecía nombrarlo.
[/list]


  [size=4]_**[size=5]Nota Final:  8 [/size].**_ [/size][i]

**El sistema presento problemas  de causa desconocida desde el inicio, aunque fueron solucionables. Una vez configurado, responde con velocidad y estabilidad, contiene una cantidad formidable de software útil, es intuitivo, atractivo y fácil de usar para el usuario promedio de linux.**[/i]  

  

 **Al equipo de KDE**
 

  Todas mis felicitaciones para los programadores de este escritorio, convirtieron a un usuario que detestaba con toda su alma KDE3, a alguien que defiende el nuevo KDE4. Me alegro también de la evolución de 4.0 a 4.2, aceptando que la primer versión era totalmente inusable, hoy en día es un escritorio completo, sin contar detalles. No quiere decir que este libre de bugs o errores algunos, los tiene, lo veo y me doy cuenta que los tiene, en menor cantidad claro. Hace casi un año, cuando probé 4.0 un usuario me dijo que cuando salga  4.2 seria el momento de mirar hacia atrás y comprarlo con KDE3.5, me doy cuenta que faltan cosas, faltan mas herramientas de configuración, lo bueno de kde era que podías configurar hasta el ultimo pixel de la pantalla. A simple vista y por decir algo me doy cuenta que todavía no se pueden poner diferentes wallpapers en las áreas de trabajo, o la Mac Menú bar que tenia KDE3. Son detalles si, pero también se nota. Me gustaría que los desarolladores de KDE miren hacia atrás, enfoncadose en lo olvidado que dejaron en kde3.5, Para agregarlo a 4.3 que veremos a mitad de este año.
  

[list][*] Mejora Artistica: Plasma me sigue fascinando y tengo mucho interés en que se desarollen aplicaciones exclusivas, como por ejemplo los bordes de ventana, Algo así como el Aero Glass de Vista. Me encantaría que se integre en otras aplicaciones como konqueror, dolphin o amarok. La estética oxygen sufrió algunos cambios leves que la hacen mas atractiva, aunque creo yo que tendrían que dar mas usos de las transparencias.Los temas son un poco reducidos, unos cuantos temas feos, Cleanlooks, y Oxygen, Seria muy bueno que integren QtCurve y Bespin, son temas de gran configuración, serian muy útiles. Los bordes de ventana siguen siendo muy simples y de poca configuración, si bien Dekorator fue portado para Qt4, es necesaria una herramienta mas efectiva. Los plasmoids también me sorprendieron, la integración panel/escritorio es muy buena. Nota: 7, no se notaron grandes cambios en la versión, podía mejorar.
[/list]
  
[list][*] Bugs, Problemas, Errores: Se avanzo mucho en cuanto a materia de bugs, sigue habiendo Plasma Crash, aunque de resultados menos catastróficos, la configuración de escritorio suele trabarse, y es necesario reiniciar plasma. Punto en contra, aunque las mejoras valen un 8.
[/list][list][*] Evolución frente a 4.1: No se si es “La respuesta” como dice el equipo de KDE, como dije antes, es necesario que miren hacia atrás para retomar acciones olvidadas, Una de las quejas mas grandes fue  la ineficacia de los paneles, puedo decir que a la fecha, los paneles son completamente configurables, pero si recordamos el viejo Kicker de KDE3 y lo comparamos con el actual panel.. esto es obsoleto. Me molesta mucho que plasma gestione todo de manera completa, creo que que es necesario hacer temas independientes para cada aplicación y que se puedan combinar estos temas, logrando una buena diversidad en el escritorio.
[/list][list][*] Otra gran queja es que el escritorio, no es un escritorio. Hasta 4.1 era una verdad a medias, pero en 4.2 se puede cambiar de manera muy fácil gracias al Folder View.  Como había dicho antes Kwin tuvo cambios, pero no los suficientes. La mejora que más me gusto fue que ahora ARK es un archivador decente y se puede hacer uso del click derecho con decencia. Pero como considero que todavía queda mucho por hacer para 4.3, la nota es un 7
[/list][list][*] Aplicaciones: La frutilla del postre es Amarok 2, es simplemente excelente, y lo convierte en el mejor reproductor de audio que probé hasta el momento. Por otro lado hay aplicaciones como kaffeine o k3b que no se portaron y son muy necesarias. Dragon Player no representa un reproductor bueno, y opto por VLC. Kwin es otro de los programas que me desilusiono, tenia grandes expectativas para esta versión, Lo mejor hubiera sido que hagan una modifcacion del compiz, lo adapten y lo optimicen para KDE, no creo que empezar de nuevo halla resultado una ventaja visible. Kopete no veo que este a la altura de pidgin y suele ser incomodo para el que esta acostumbrado a un mensajero mas simple. No tuve la oportunidad de probar krita o koffice, no se si es justo aplicar una nota por algo que no probé, así que por lo visto, negro sobre blanco, un 6.

[/list]
  

  **[size=5]Nota Final KDE   7[/size]**

 *** Kde4.2 es fantástico, pero existen cosas obvias, muy obvias que necesitaron ser tomadas en cuenta antes, Me imagino que los programadores se concentraron en liberarlo de la mayoría de los bugs y solucionar las quejas de los usuarios y que piensan perfeccionar el escritorio para 4.3, Sin duda, no habría nada para mejorar si no es eso lo que tienen en plan. Entonces saco como conclucion que para la próxima versión portaran todos los programas que hoy reclamo, y se centraran en los detalles olvidados. Espero que así sea.***
 


[CENTER][b]Screenshots (click para agrandar)
[/b]


[[img]http://i41.tinypic.com/290q04j_th.jpg[/img]](http://i41.tinypic.com/290q04j.jpg)


[[img]http://i42.tinypic.com/14vsoed_th.jpg[/img]](http://i42.tinypic.com/14vsoed.jpg)


[[img]http://i42.tinypic.com/5ttlvs_th.jpg[/img]](http://i42.tinypic.com/5ttlvs.jpg)


[[img]http://i40.tinypic.com/wclmkm_th.jpg[/img]](http://i40.tinypic.com/wclmkm.jpg) [/CENTER]
  


  

  

 [b] Comentario para Concluir
[/b]
  

  Con el fin de querer hacer algo serio, el análisis llevo mucho tiempo de trabajo, algunos dolores de cabeza, y cansancio en los ojos.  

  Por ahora me quedaré con Open SUSE, me quedaron algunas cosas por hacer como editar fstab o mover los documentos de mi familia. Mi único deseo es que si leyeron el articulo, me hagan saber que les  pareció en todo sentido, Si tenes un blog y te gustaría publicarlo, no hay ningún problema, mientras cites la autoria.; es mas seria un gran elogio que alguien publique mi articulo, mi blog esta prácticamente abandonado y no tengo interés en publicarlo ahí.
  Por mi parte, usare el resto del día para descansar de todo que tenga que ver con una pantalla
  

 **Saludos, Pol.  Pablo Perez**
[b]pol.metalrock@gmail.com

[/b]

---

### Post by guisheca on 2009-02-02
Me encantó el análisis pol666 lo voy a publicar en mi blog. Te comento que hasta ahora en donde mejor vi aplicado el escritorio kde4 es en mandriva 2009, todos los problemas que te comentaba por mp el otro día no existen allí. Está muy bien integrado aunque no muy actualizado.
Saludos.

---

### Post by pol666 on 2009-02-02
Estoy esperando a la salida de Mandriva 2009.1 en Abril para probarlo

---

