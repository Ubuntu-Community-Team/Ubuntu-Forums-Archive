---
title: "Dame tu opinion: Mejor forma de instalar Ubuntu y Güindous."
date: 2009-12-27
forum: Comunidad
---

### Post by daggaz on 2009-12-27
Hola.
Bueno, luego de hacer un verdadero caos con mi disco duro y de actualizarme a Karmic con muchos problemas graves entre los que destacan el no reconocimiento de periféricos y demás hardware decidí volver a instalar todo como los dioses mandan.
Aquí va más o menos como quiero tener mi disco duro; Quiero tener: 
 
[LIST=1]
[*]Ubuntu (9.10 no creo que si lo instalo bien me de tantos problemas)
[*]Güindos (No sé que versión, creo que XP me acomoda más)
[*]Una partición grande para mis archivos.
[/LIST]
 Y eso sería todo básicamente. Actualmente solo tengo Ubuntu y un fantasma de Güinodus Vista que no se va.
La cosa es que no sé más o menos cuanto espacio debo dar a las particiones de los sistemas operativos y no sé como hacer para que Ubuntu tenga la carpeta «home» en una partición diferente. En cuanto a la cantidad de programas a instalar, pues en Güindos serían básicamente ProTools, Flash, TS A-MIDI, After Effects, Premier y me supongo que algún programa o códec para poder manejar la partición ext4 de mis documentos, que espero exista...
En Ubuntu: Cinelerra, LMMS, Kdenlive, Audacity, KToon, Arduor... Y las «default» (Amarok, VLC, K3b, Compiz y Emerald, Google Earth, Gimp, Inkscape... Además de las que incluye el S.O.); no sé calcular el peso de los programas, pero uso aplicaciones multimedia (audio,video y gráficos), todas juntas, ¿unos 20Gb en Güin y 2Gb en Ubuntu? (amo la ligereza del Soft Libre).
La otra cosa es la Swap, que me han dicho que es mejor ponerla hasta el final del disco, pero no lo sé... ¿Cómo hago eso?
 Mi PC:
HD: 300Gb.
Ram: 3Gb
CPU: Intel Core2 Duo a 2.000(x2) [supongo que a 64 bits]
Es una HP Compaq6910p (Tuve que instalar controlador privativo Broadcom, y creo que la tarjeta gráfica da algunos problemas con Linux y eso de que sea a 64, según creo, también puede ser un poco fastidioso sobre todo con los paquetes .deb ya que aún no soy bueno compilando).
 En resumen, mis dudas son las siguientes:
 
[LIST]
[*]¿Qué instalo primero Güindos o Ubuntu?
[*]¿Si he tenido problemas con Ubuntu Karmic actualizado de Jaunty me recomiendan instalarlo o quedarme con Jaunty?
[*]¿Ubuntu a 64 bits? (¿tengo otra opción?)
[*]¿En qué orden debo hacer las particiones (Güin, Ubuntu, «Home» y Swap)?
[*]¿Cuanto espacio debo dar más o menos a cada S.O. a los documentos y a la Swap?
[*]Ext3 o Ext4
[*]¿Cómo le digo a Ubuntu que haga la carpeta «home» en una partición diferente?
[*]¿Existe alguna cosa para que Güidos lea Ext4 o Ext3?
[*]¿Algún otro consejo?
[/LIST]
 Pues eso sería todo, espero me puedan dar al menos una opinión o consejo de los muchos que pido.
 Muchas gracias.

---

### Post by z37a on 2009-12-27
Todo depende tambien de la persona que lo vaya a usar, lo que si te recomiendo es que particiones con el live de Ubuntu primero, luego instales Windows y por ultimo Ubuntu, por que asi, por que podes poner al principio del disco una particion primaria de 128MB para el /boot, luego particionas una primaria NTFS y por ultimo las particiones que quieras. Ahora en las particiones Linux te reocmiendo que uses ext4 en caso de que sea 9.10.

El por que el /boot adelante con tan poco espacio, bueno es algo que tengo de costumbre hacer pero tiene tambien una logica el seprarlo, si la persona que la usa decide borrar la particion de Linux, si no borra esa de 128MB puede seguir ingresando a Windows, eso pro una parte(aunque no se si se puede con GRUB2 esto) y por otra, es por que esta estandarizado que debe haber una partici0on al principio del disco para tal fin, pero esto viene de maquinas viejas!!!!

---

### Post by pol666 on 2009-12-27
Yo lo que hago primero en las PCs es, backup de lo que es muy importante porque nunca se sabe, luego  meto el live cd de ubuntu (si, por más que vaya a instalar otra distro, el particionador Gparted que viene es lo más) y de ahí particiono, redimensiono, etc. 

Lo que recomiendo es, 1 raiz "/" de 7gb, una partición grande cómo /home  para poner todos los archivos, lo que desee de Windows, y a algunos les he recomendado poner otra partición ntfs, otros, cómo yo, tenemos otra partición de 7gb para instalar más distribuciones :)

Existen programas que leen ext3 en windows, ext4 hasta donde sabía no, pero igual yo ni los necesito, paso los archivos que necesito antes de reiniciar. 

Reinicio con el CD de Windows e instalo en la partición que tengo pensada, luego instalo la distribución en cuestión. 


¿Qué instalo primero Güindos o Ubuntu?
Windows, porque sino "rompe" el grub.
¿Si he tenido problemas con Ubuntu Karmic actualizado de Jaunty me recomiendan instalarlo o quedarme con Jaunty?
No, te recomiendo intentar al máximo solucionar los problemas, así aprendes
¿Ubuntu a 64 bits? (¿tengo otra opción?)
Con 3gb de RAM no vale tanto la pena, cómo quieras a esta altura no hay mucha diferencia. 
¿En qué orden debo hacer las particiones (Güin, Ubuntu, «Home» y Swap)?
Para hacer particiones no tengo un orden, podes armarlas todas juntas y luego el particionador hace los cambios solo..
¿Cuanto espacio debo dar más o menos a cada S.O. a los documentos y a la Swap?
Windows depende de que versión sea y para que lo uses, para linux unos 7gb para la raíz y lo que quieras/tengas para /home
Ext3 o Ext4?
Ext4, olvidate de ext3 ahora. 
¿Cómo le digo a Ubuntu que haga la carpeta «home» en una partición diferente?
En la instalación, seleccionas la particion y designas cómo punto de montaje /home
¿Existe alguna cosa para que Güidos lea Ext4 o Ext3?
Ext3 si, ext4 hasta donde sabía no... pero si uno es precavido y maneja bien los archivos no hace falta esas cosas :P
¿Algún otro consejo?
No te preocupes si rompes algo que todo se arregla, ^^

---

### Post by guillermon on 2010-01-02
Hola, muy completo tanto el plateo como las respuestas... Me animo a dar un solo aporte,a partir de haber instalado varias veces y en distintas pcs, y por recientemente haber tenido problemas con el tamaño asignado a Win$. Qué me pasó? En mi pc solamente le asigné 10 gigas a un xp que no uso nunca, pero cuando necesité usar el adobe premiere (pues con las aplicaciones libres lamentablemente me fue muy mal... digo esto con mucho dolor, en serio) para editar un video, me quedé sin espacio y no pude hacer leer los discos con ext4! Le pedí una super pc de un amigo, al cual le había instalado lo mismo pero asignándole 45 gigas al disco, pero el vista que todo lo destroza no tardó en  dejarme sin espacio y traerme problemas.
   He leido que vas a usar  programas pesados en Win$. Piensa bien en esto. Considera esa idea de crear un disco en ntfs extra a tu home, que tendrá la ventaja de ser leido desde ambos sistemas, y tendrás espacio si necesitas hacer algún trabajo pesado. Tienes 300 gigas, eso corre a tu favor...
   Espero que no te pase lo me pasó. Suerte!
Guillermo

---

### Post by clasificado on 2010-01-05
> 
[LIST]
[*]¿En qué orden debo hacer las particiones (Güin, Ubuntu, «Home» y Swap)?
[*]Ext3 o Ext4
[*]¿Existe alguna cosa para que Güidos lea Ext4 o Ext3?
[*]¿Algún otro consejo?
[/LIST]


Tengo pocas cosas que acotar a lo que ya se ha dicho, por lo que me remito solo a estos puntos que quoteo.

1) **Sobre el orden de las particiones**, depende enteramente de las capacidades de tu equipo y de la clase de uso que se le quiera dar. (más que dicho) *pero esto determina seriamente la velocidad del sistema operativo*

un disco rígido común siempre aprovecha el 100% de la velocidad en la primera partición (ponele, 60mb/seg en mi notebook), cae a 45mb/seg en la mitad del disco, y se precipita a 30mb/seg al final.

Por lo que el orden de las particiones determina la velociad de acceso a los archivos de sistema para el sistema operativo en cuestión

- Yo tengo así: Ubuntu/Home/Ventanas/Swap. Eso es porque tengo 2gb de memoria y casi nunca me salto a la swap.
- Si fuera un equipo de poca memoria, recomendaría el swap primero.
- Si se usara mas Ventanas que ubuntu, pondria Ventanas primero

2) **Ext3 o Ext4**: Ext4 se dice mas rápido (lo fué en mi caso), pero no se puede acceder desde Ventanas (AFAIK). Ext3, si.

Entonces, si entendemos que las particiones son Ubuntu/Home/Ventanas/Swap, el Ubuntu lo ponemos en Ext4 para velocidad y el Home lo ponemos en Ext3 para compatibilidad con Ventanas.

El acceso desde Ventanas al home ext3 se hace con el [http://www.ext2fsd.com/](http://www.ext2fsd.com/), que hace poco agregó el soporte para ext3 con inodes de 256, así que no hace falta hablar de eso.

No se puede acceder al Ubuntu (Ext4) desde Ventanas (de nuevo, AFAIK). En mi caso no me hace falta, ya que mis docs están en el Home que es ext3 y sí lo puedo acceder desde Ventanas

3) **¿Algún otro consejo?**
Yo, particularmente, agregué UNA PARTICION MAS, la de boot.

por lo que quedaría boot|ubuntu|home|ventanas|swap

Es porque uso más de una instalación de linux, y la verdad es que me copa bastante darle al apt-get y al yum y al emerge y las distribuciones se me desestabilizan como si fuera un Ventanas :P y hay que reinstalar medio seguido. Pero no siempre termino las instalaciones, y muchas veces las particiones desaparecen (porque no instalo) y no me gusta perder acceso a mi computadora porque me aburro de una distribución/os

Así que el boot va aparte (un grub2 comunacho) y de ahi a donde se quiera

*cuando se superan las cuatro particiones hay un detalle técnico*, el de las particiones extendidas y lógicas.

Para cerrar la cosa, yo lo tengo así: boot|[ubuntu|home|gentoo|suse]|ventanas|swap, siendo ubuntu|home|gentoo|suse lógicas, y siendo [] la extendida.

boot,home:ext3
ubuntu,gentoo,suse:ext4
ventans:ntfs
swap:swap

Es increible como proliferan las particiones :P por suerte existe gparted

clasificado

---

### Post by daggaz on 2010-01-06
Muchas gracias a todos por sus aportaciones, sus consejos me fueron muy útiles; espero que a muchas más personas les sean útiles también. Ahora mi Ubuntu Karmic corre sin ningún problema y mejor incluso que como lo hacía mi Jaunty.
También debo mencionar que no pasé por alto los consejos y recomendaciones que me encontré en [*Ubuntu Life*]("http://ubuntulife.wordpress.com/2009/11/06/cosas-a-hacer-despues-de-instalar-ubuntu-9-10-kamic-koala/"), para hacer inmediatamente después de instalar Ubuntu.

---

### Post by clasificado on 2010-01-19
Agrego un detalle con el [ext2fsd]("http://www.ext2fsd.com/"): El [instalador común 0.48 que se puede descargar del sitio oficial]("http://sourceforge.net/projects/ext2fsd/files/Ext2fsd/0.48/Ext2Fsd-0.48.exe/download") **nunca me anduvo de una**. Implica saber manejar una ventana CMD desde Ventanas.

**¿Recién instalado qué hace?** Nada de lo que le pido. 

Desde Explorer me exije formatear el disco (DECILE QUE NO!!!), desde un CMD me dice que "el formato de archivos no es compatible" o algo así.

**¿Porqué?** No se, porque nunca le encontré logs a la cosa.

**¿Que alternativas tengo?** Descargarse la OTRA versión, también disponible en el sitio oficial: **[el paquete ZIP 0.48 que no es el código fuente]("http://sourceforge.net/projects/ext2fsd/files/Ext2fsd/0.48/Ext2Fsd-0.48.zip/download")**

El rol del paquete es el mismo: instalar el bicho y sus bichitos en un Ventanas. 

Pero la interfaz de instalación es diferente, un SETUP.BAT que está tirado en ~/Setup/Setup.bat

El setup.bat sin parámetros nos da un help bien consiso
```

Help on ext2fsd setup utility:
setup 2k:             install ext2fsd to windows 2000 x86
setup xp  [signed]:   install [signed] ext2fsd to windows xp/vista x86
setup w64 [signed]:   install [signed] ext2fsd to windows xp/vista x64

```

La opción que hizo la mitad del milagro fue **setup.bat xp signed**

Inmediatamente después se abrió una ventana de búsqueda de archivo pidiendome el ext2fsd.sys, la segunda mitad del milagro.

Yo lo encontré en ~/Setup/wxp/ext2fsd.signed.sys, aunque no está solo, tiene otros archivos alrededor. Los borré, el que no dice signed y su pdb y le cambié el nombre al archivo para asegurarme de cual está eligiendo.

**Voilà! funcionando**. Ejecutando a mano el ~/Setup/Ext2Mgr.exe se pudo montar discos ext3 y toda la pelota.

En mi caso, lo desinstalé con otro bat del mismo paquete "Uninstall.bat" sin parámetros

Después volví a instalar el ejecutable Ext2Fsd-0.48.exe y en las opciones de instalación **le dije "Read Only" ya que no me interesa obtener más. Nunca probé la escritura de uno de estos drivers para XP en un ext3 con inodes de 256.** Sí los he probado mucho mucho en inodes de 128, pero hace mucho. supongo que sera mas estable todavía, cosas del paso del tiempo

Con esto, quedó instaladito, run on boot y funcionando signed (porque el driver signed quedó en el caché de Sys propio del sistema ya no usa el que viene en el instalador)

Al final habré reiniciado seis veces el sistema :P

clasificado

---

### Post by guillermon on 2010-01-20
> **clasificado said:**
>  Nunca probé la escritura de uno de estos drivers para XP en un ext3 con inodes de 256.[/B] Sí los he probado mucho mucho en inodes de 128, pero hace mucho. supongo que sera mas estable todavía, cosas del paso del tiempo 
Hola, yo además de consultarle a "clasificado" abrí un post sobre este tema, pues no podía montar. Como no obtenía ayuda, me puse a leer más (no es que no lo había hecho; pues ahí decía que si andaba, y a mi no... entonces profundicé). Clasificado tenía razón, y en el post de aquí arriba lo explaya más. En mi caso, luego de pasar algunas horas leyendo, cuando fui a aplicar la teoría: chan! funcionaba... Juro haber reiniciado y tocado opciones. Luego lo he instalado en otra pc y corre perfecto, con solo instalar el archivo .exe.
   **Lo que aporto es que lo he probado como escritura, inclusive copiando un archivo de 8 gigas (un avi), y anduvo de pelos (con 256 inodes)**
   Estoy un poco triste y avergonzado por toda la vuelta. Lo dije y le vuelvo a agradecer a clasificado. Saludos

Guillermo

---

