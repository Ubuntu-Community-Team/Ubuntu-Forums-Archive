---
title: "Kompozer 0.8+Pack Lenguaje en Castellano .deb"
date: 2009-07-04
forum: Comunidad
---

### Post by juancarlospaco on 2009-07-04
**[CENTER][SIZE="5"][COLOR="Sienna"]Kompozer 0.8+Pack Lenguaje en Castellano .deb[/COLOR][/SIZE][/CENTER]**


[CENTER]
[LIST]
[*]**[SIZE="4"][COLOR="DarkOrange"]En los Repos esta la Version anterior 0.7 ![/COLOR][/SIZE]**
[/LIST]

[IMG]http://kompozer.sourceforge.net/screenshots/kpz-scr-01.png[/IMG][/CENTER]

[LIST]
[*]**Kompozer 0.8a4 + Todos los Language Packs para la misma version.**
[/LIST]

Danish, German, English, Spanish, French, Italian, Dutch, Russian, Chinese.

[SIZE="1"][I]usr/share/Kompozer/kpz-langpack-enUS.xpi
usr/share/Kompozer/kpz-langpack-it.xpi
usr/share/Kompozer/kpz-langpack-esES.xpi
usr/share/Kompozer/kpz-langpack-de.xpi
usr/share/Kompozer/kpz-langpack-da.xpi
usr/share/Kompozer/kpz-langpack-nl.xpi
usr/share/Kompozer/kpz-langpack-fr.xpi
usr/share/Kompozer/kpz-langpack-ru.xpi
usr/share/Kompozer/kpz-langpack-zhCN.xpi[/I][/SIZE]

Descargados desde la web de Kompozer HOY.
Deberia funcionar en** Ubuntu Hardy 8.04, Intrepid 8.10, Jaunty 9.04.**

Maneja las dependencias por metapaquetes de *buntu,
probablemente no funcione en Debian o versiones no derivadas de Ubuntu.

Se lo quise mandar al autor pero me rebota el mail, 
si alguien sabe como mandarselo por mail por favor hagalo.

[CENTER][[IMG]http://kompozer.sourceforge.net/images/kompozer_128x128.png[/IMG]]("http://tecnicoslinux.com.ar/livecd/Kompozer_0.8a4_i386.deb")[/CENTER]




:p

---

### Post by guillermolisi on 2009-07-04
> Maneja las dependencias por metapaquetes de *buntu,
probablemente no funcione en Debian o versiones no derivadas de Ubuntu.Como para poner las cosas en el orden natural que poseen, deberia leerse:

"Maneja las dependencias por metapaquetes de *buntu,
probablemente no funcione en Ubuntu o versiones no derivadas de Debian."

Lo cual suena raro, cierto ?

Podrias aclarar esta aparente limitacion asi evitamos que alguien se entusiasme instalandolo y termine llenando el disco del server del foro con pedidos de ayuda ? ;)

Muy buena noticia !! Lo habia dejado de usar porque la version de los repos esta atestada de bugs, casi inoperante para produccion.

Gracias por el aviso :o

---

### Post by juancarlospaco on 2009-07-04
Que depende del meta-packete " **ubuntu-standard** ",
que no esta en Debian, que si esta en otros sabores de Ubuntu,
que esta en todas las instalaciones de Ubuntu excepto en las JeOS y Minimal,
inclusive en la Server, Kubuntu y Xubuntu tambien esta,
que es un paquete base para asegurarme que tenga lo minimo pa que ande.
*Que e un coso que hace que tengas todos los cosos basicos en tu sistema.*

El idioma no te lo pone solo, por que muchos dicen que lo mejor es usarlo en Ingles,
asi que luego de instalarlo con el nuevo Kompozer abran el archivo:

/usr/share/Kompozer/kpz-langpack-esES.xpi

:)

---

### Post by sergiom99 on 2009-07-04
yo creia que Kompozer estaba abandonado y bien muerto.

---

### Post by guillermolisi on 2009-07-04
> Que e un coso que hace que tengas todos los cosos basicos en tu sistemaMe encanto explicado asi ! :D

---

### Post by sergiom99 on 2009-07-12
lo estoy probando.
Gracias Juan Carlos!

Sabes si hay algun ppa hecho para agregar como repo? Porque ahora al bajar actualizaciones me pide "actualizarlo" al 0.7.10 !

---

### Post by juancarlospaco on 2009-07-12
**Synaptic--->Buscar Kompozer--->Barra de Menus--->Paquete--->Bloquear Version**
*No hay .deb, por eso hice ese, en Karmic Final ya va estar, pero hasta entonces...*

:)

---

### Post by sergiom99 on 2009-07-12
Uso Kubuntu JJ. Ni en Adept ni el otro Kpackage... aparece la opcion para bloquear versiones.
Pero lo reemplace con 
```
 sudo aptitude hold kompozer  
```
y me sigue apareciendo el aviso de actualizar a la version anterior.

---

### Post by juancarlospaco on 2009-07-12
Si, los reemplazos de Synaptics de KDE no estan tan buenos :(
*no deberia...*

---

### Post by sergiom99 on 2009-07-13
Ahora si:

```

sudo su
echo kompozer hold | dpkg --set-selections
sudo sudo aptitude update && sudo aptitude upgrade
```

[https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

---

