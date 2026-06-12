---
title: "bar title very big!"
date: 2007-11-10
forum: Desktop Environments
---

### Post by Dani87cadiz on 2007-11-10
ello everybody!

I just installed in my pc Ubuntu 7.10 and I have a problem since the start for the first time the title bar of the window is enormous and therefore slows the pc something besides be something ... Uncomfortable.

Not as remove even Preferences --> appearance change the size and font of the title but nothing once reboot the pc and came to be natural size but when cerre session and reintroduced it to be returned to start putting enormous, and nor rebooting or anything.

Does anyone know how to fix this?

PD: part on the home screen Session sources to put the user and pass out too huge or see what is written

Thanks in advance!

---

### Post by erginemr on 2007-11-10
> **Dani87cadiz said:**
> ello everybody!

I just installed in my pc Ubuntu 7.10 and I have a problem since the start for the first time the title bar of the window is enormous and therefore slows the pc something besides be something ... Uncomfortable.

Not as remove even Preferences --> appearance change the size and font of the title but nothing once reboot the pc and came to be natural size but when cerre session and reintroduced it to be returned to start putting enormous, and nor rebooting or anything.

Does anyone know how to fix this?

PD: part on the home screen Session sources to put the user and pass out too huge or see what is written

Thanks in advance!

Hi there. Welcome to the Ubuntu world. I hope you will like it as much as we did.

Could you please take a screenshot of one of your windows and post it here? You can do this by first pressing Alt+PrintScreen while one of your problematic windows is active, saving your picture on the desktop, then going into advanced in the post-writing screen and attaching the file using the attachment icon.

Also, part of your nick name (Cadiz) and the word "cerre" suggests that you are from Spain. If you do not feel comfortable in English, you may post your question in Spanish. I will do my best to help you with my little Spanish, and I saw other posts in Spanish in the Ubuntu forum, so there will hopefully be other people to try and help you.

Take Care.

---

### Post by Dani87cadiz on 2007-11-10
[IMG]http://img45.imageshack.us/img45/1304/pantallazoze9.jpg[/IMG]


Thank!!!

---

### Post by erginemr on 2007-11-10
¡Hola! Gracias por la pantalla.

Cuando cambio el tamaño de la fuente para la barra del título,
recibo el mismo resultado que el suyo. Tiene que reducir el
tamaño de la fuente según lo indicado en los cuadros unidos.

No he entendido su mensaje inicial bien, pero creo que usted hizo ya eso, 
pero sus cambios fueron perdidos después de un reboot. ¿Es
este correcto?

---

### Post by Dani87cadiz on 2007-11-10
Hola, que alegria que hables mi idioma, pues si exactamente eso me ocurre, aunque lo arregle, vuelve a pasar lo mismo si cierro sesion y vuelvo a iniciarla

---

### Post by erginemr on 2007-11-10
> **Dani87cadiz said:**
> Hola, que alegria que hables mi idioma, pues si exactamente eso me ocurre, aunque lo arregle, vuelve a pasar lo mismo si cierro sesion y vuelvo a iniciarla

Puede ajustar el mismo ajuste también en gconf-redactor. 
Utilice Alt-F2, escriba gconf-redactor. 
Debajo del llave "/apps/metacity/general/titlebar_font", 
cambie el tamaño de fuente a 10 o a 12. Logout y login. 
¿Diferencia?

---

### Post by erginemr on 2007-11-10
Además, compruebe por favor que usted tenga los correctos permisos de escritura en su directorio casero (de casa), especialmente en el directorio del ".gconf". 
Publique el comando: "ls -la ~" 
en une consola (terminal) y copie el resultado aquí por favor.

---

### Post by Dani87cadiz on 2007-11-10
bien hice lo que me dijo y al ejecutar el comando gconf-redactor me dice que no encuentra el archivo.

Por otra parte hice lo que me pidio de ejecutar el comando ls -la ~ y aparece lo siguiente:
total 1248
drwxr-xr-x 31 dani dani   4096 2007-11-11 02:05 .
drwxr-xr-x  3 root root   4096 2007-11-09 22:02 ..
-rw-------  1 dani dani    132 2007-11-10 21:08 .bash_history
-rw-r--r--  1 dani dani    220 2007-11-09 22:02 .bash_logout
-rw-r--r--  1 dani dani   2298 2007-11-09 22:02 .bashrc
drwxr-xr-x  3 dani dani   4096 2007-11-09 21:07 .cache
-rw-r--r--  1 dani dani 122404 2007-11-09 23:17 Clipboard.jpg
drwxr-xr-x  5 dani dani   4096 2007-11-09 21:34 .config
-rw-------  1 dani dani     28 2007-11-11 02:05 .dmrc
drwxr-xr-x  2 dani dani   4096 2007-11-09 21:07 Documentos
drwxr-xr-x  2 dani dani   4096 2007-11-10 21:15 Escritorio
-rw-------  1 dani dani     16 2007-11-09 21:07 .esd_auth
drwxr-xr-x  7 dani dani   4096 2007-11-10 21:16 .evolution
lrwxrwxrwx  1 dani dani     26 2007-11-09 22:02 Examples -> /usr/share/example-content
drwxr-xr-x  2 dani dani   4096 2007-11-09 23:47 .fontconfig
drwx------  4 dani dani   4096 2007-11-11 02:05 .gconf
drwx------  2 dani dani   4096 2007-11-11 02:09 .gconfd
drwxr-xr-x 22 dani dani   4096 2007-11-09 23:51 .gimp-2.4
-rw-r-----  1 dani dani      0 2007-11-10 19:33 .gksu.lock
drwxr-xr-x  3 dani dani   4096 2007-11-09 21:07 .gnome
drwx------ 11 dani dani   4096 2007-11-10 21:16 .gnome2
drwx------  2 dani dani   4096 2007-11-09 21:07 .gnome2_private
drwxr-xr-x  2 dani dani   4096 2007-11-09 21:07 .gstreamer-0.10
-rw-r--r--  1 dani dani    116 2007-11-11 02:05 .gtk-bookmarks
-rw-r--r--  1 dani dani     86 2007-11-09 21:07 .gtkrc-1.2-gnome2
-rw-------  1 dani dani    169 2007-11-11 02:05 .ICEauthority
drwxr-xr-x  2 dani dani   4096 2007-11-09 21:09 .icons
drwxr-xr-x  2 dani dani   4096 2007-11-09 21:07 Imágenes
drwxr-xr-x  3 dani dani   4096 2007-11-09 21:07 .local
drwx------  3 dani dani   4096 2007-11-09 22:16 .macromedia
drwx------  3 dani dani   4096 2007-11-09 21:08 .mozilla
drwxr-xr-x  2 dani dani   4096 2007-11-09 21:07 Música
drwxr-xr-x  3 dani dani   4096 2007-11-10 21:16 .nautilus
-rw-r--r--  1 dani dani 352256 2007-11-10 19:37 nautilus-debug-log.txt
-rw-r--r--  1 dani dani 602242 2007-11-09 21:54 Pantallazo.png
drwxr-xr-x  2 dani dani   4096 2007-11-09 21:07 Plantillas
-rw-r--r--  1 dani dani    566 2007-11-09 22:02 .profile
drwxr-xr-x  2 dani dani   4096 2007-11-09 21:07 Público
drwx------  5 dani dani   4096 2007-11-10 00:28 .purple
-rw-r--r--  1 dani dani   7068 2007-11-10 21:16 .recently-used.xbel
-rw-r--r--  1 dani dani      0 2007-11-09 21:10 .sudo_as_admin_successful
drwxr-xr-x  2 dani dani   4096 2007-11-09 21:09 .themes
drwx------  3 dani dani   4096 2007-11-09 21:09 .thumbnails
drwx------  2 dani dani   4096 2007-11-09 23:59 .Trash
drwxr-xr-x  2 dani dani   4096 2007-11-09 22:00 .update-manager-core
drwx------  2 dani dani   4096 2007-11-10 00:28 .update-notifier
drwxr-xr-x  2 dani dani   4096 2007-11-09 21:07 Videos
-rw-------  1 dani dani    178 2007-11-11 02:05 .Xauthority
-rw-r--r--  1 dani dani   4972 2007-11-11 02:05 .xsession-errors

---

### Post by erginemr on 2007-11-11
Lo siento, debe estar "gconf-editor". :)

---

### Post by Dani87cadiz on 2007-11-11
pero usted dijo gconf-editor o gconf-redactor?

---

### Post by Linicks on 2007-11-11
> **Dani87cadiz said:**
> [IMG]http://img45.imageshack.us/img45/1304/pantallazoze9.jpg[/IMG]


Thank!!!

LOL.  First time I laughed out loud in these forums... great image!

Nick

---

### Post by forrid on 2007-11-11
thankx

---

### Post by Dani87cadiz on 2007-11-11
> **erginemr said:**
> Puede ajustar el mismo ajuste también en gconf-redactor. 
Utilice Alt-F2, escriba gconf-redactor. 
Debajo del llave "/apps/metacity/general/titlebar_font", 
cambie el tamaño de fuente a 10 o a 12. Logout y login. 
¿Diferencia?

Tuve que colocar la fuente en tamaño 1 para que la barra fuese normal, inicie sesion y aparecio normal :)

Pero el problema es que tengo Compiz fusion y ahora las ventanas me van muy lentas al maximizarla o moverlas, antes del problema (cuando llege a solucionarlo temporalmente) iba perfectamente

---

### Post by erginemr on 2007-11-11
¡Muy bien! ¿Pero qué sucede cuando usted ajustó el tamaño de fuente a
10 pixeles en gconf-editor como he descrito antes?

---

### Post by erginemr on 2007-11-11
For the other Ubuntu users, our friend has a problem with the title bars font size in Ubuntu.

He says when he selects a reasonable font size (say 10 px) from the Appearance applet, his windows are back to normal, but as soon as he stops and restarts the session, the font size has been reset by itseltf and the huge title bar on the windows returns.

I have advised him to use "gconf-editor" as an alternative to set the font size under the key:
/apps/metacity/general/titlebar_font
and asked him to check his home folder (esp. the hidden directory .gconf, which, as far as I know, holds these settings) for the permissions. It appears that permissions have been correctly said.

Then, he said he has temporarily resolved the problem by setting the font size to 1 pixels (but this might be a typo, where he actually might have wanted to say 10 px.), he can now login and logout, with the settings kept between sessions.

But he now ran into another issue: With Compiz Fusion enabled, the windows started to move and resize very slowly. He says the window effects were fast enough before the change.

Any ideas from other Ubuntu users?

---

### Post by Dani87cadiz on 2007-11-12
por si sirve de algo, mi pc es una laptop Intel Core2 Duo a 1.66 y 1gb de Ram con una grafica integrada de Intel 945GM a 128

---

### Post by erginemr on 2007-11-12
> **Dani87cadiz said:**
> por si sirve de algo, mi pc es una laptop Intel Core2 Duo a 1.66 y 1gb de Ram con una grafica integrada de Intel 945GM a 128

¡Muy bien! ¿Pero qué sucede cuando usted ajustó el tamaño de fuente a
10 pixeles en gconf-editor como he descrito antes? Es su problema solucionado?

---

### Post by Dani87cadiz on 2007-11-12
hice lo que usted me indico, y las barras se volvieron normales y bien, incluso reiniciando la sesion continuaba todo bien sin embargo las ventanas van muy lentas y en la pantalla de login de usuario sigue la fuente muy grande.

---

### Post by erginemr on 2007-11-13
Querido amigo,

Lo siento, pero, lamentablemente, he llegado al final de mis recursos (conocimientos). Después de este punto, todo lo que puedo hacer es adivinar (trial-and-error).

Puesto que nadie más tiene alguna idea, puedo sugerirle de hacer uno del siguiente:

1) Hay un archivo (xorg.conf) que conserve los valores de la configuración de su monitor, tarjeta gráfica (NVIDIA, ATI, etc.) y el escritorio en general. Está situado bajo el directorio "/etc/X11". Hay también un comando que lo configura de nuevo automáticamente.

1.a. Usted puede primero copiar la configuración original con:
sudo cp /etc/X11/xorg.conf  /etc/X11/xorg.bak
(Siempre copie los archivos originales antes de hacer cualquier cosa crítica.)

1.b. Entonces configure de nuevo su escritorio con:
sudo dpkg-reconfigure  -phigh  xserver-xorg

1.c. Reinicie (reboot) su ordenador para ver si todo está de vuelta a normal. Si no, usted puede restaurar la configuración original con:
sudo cp /etc/X11/xorg.bak  /etc/X11/xorg.conf

2) Si Step-1 arriba no funciona, hay un paquete adicional para Compiz-Fusion, "compizconfig-settings-manager" para una configuración detallada. Usted puede instalarlo con:
sudo aptitude install compizconfig-settings-manager

Pero primero, usted tiene que activar los otros repositorios por el menú de "synaptic". (Véase las capturas de pantalla adjuntas.)

Después de la instalación de este paquete, haz clic-derecho en la pantalla y seleccione "Change the Background" (o con el menú "System -> Preferences -> Appearance"), en una de las opciones que dice "Visual Effects", verá la Compiz - Fusion ajustes avanzados (un botón). Juega con los ajustes un poco, y ver si hay alguna mejora de velocidad en el movimiento de las ventanas.
Si no, puede desinstalar la misma, si lo desea, con:
sudo apt-get remove compizconfig-settings-manager

3) Si ni uno ni otro de los pasos antedichos trabajan, puede pensar en comenzar de nuevo y en la reinstalación de Ubuntu (Gutsy Gibbon).

4) Si lo desea, puede publicar el contenido de el archivo xorg.conf con:
cat /etc/X11/xorg.conf > output.txt  (En esta parte se lista los contenidos del archivo xorg.conf y la coloca en un nuevo archivo de texto en su directorio de casa [/home/su_nombre])

gedit output.txt   (En esta parte se abre el archivo de texto creado justo con Gnome Editor.)

y finalmente copie el resultado aquí.

Usted debe también darnos información sobre la marca y el tipo de su tarjeta gráfica (como NVIDIA GeForce FX 5500, etc)

¡Buena suerte!, espero que usted encuentre la solución.

---

### Post by erginemr on 2007-11-15
¿Cualquier progreso?

---

