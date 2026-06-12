---
title: "No aparece La Barra de Menú ni la Barra superior"
date: 2015-04-06
forum: Colombia Team - Colombia
---

### Post by David_Granada on 2015-04-06
Buenos Tardes. 

Tengo la actualización de Ubuntu 14.04, y soy nuevo en el sistema operativo. Ayer traté de instalar Skype y no lo logré, y esta mañana, cuando prendí el pc no aparecía ni la barra de Menú, ni la barra superior donde aparece la hora y la energía restante del pc. Estuve mirando en foros y parece que problema es recurrente, y que se debe a que el Unity del Compiz no está habilitado. Para esto sugieren meterme Equipo/usr/share y buscar el Gesto de Configuración CompizConfig. Sin embargo, cuando trato de ejecutarlo me aparece "se ha producido un error al lanzar la aplicación". Más específicamente traté de hacer lo que se hace en este video. [https://www.youtube.com/watch?v=BatbcU7T8wg](https://www.youtube.com/watch?v=BatbcU7T8wg)

También sugieren ejecutar Ctrl+Alt+F1 y ejecutar los comandos que acá se muestran después de logearse: [http://www.ubuntu-es.org/node/184268#.VSL4O_mG-Sp](http://www.ubuntu-es.org/node/184268#.VSL4O_mG-Sp). Sin embargo, me aparece siempre "Login incorrect", y no me deja hacer nada. Me gustaría saber si alguno de ustedes tiene alguna solución para que me vuelvan a aparecer las barras, o en su defecto, resetearlo a los valores iniciales, antes de instalar los programas.

Muchísimas Gracias

---

### Post by NestorAcevedo on 2015-04-08
lo que yo haría es tener un live cd o live usb de ubuntu, arrancar desde el. luego navegar en el disco, deben haber alrededor de 3 discos montados uno de ellos debe pertenecer a /home que es donde esta todo lo del usuario (Documentos, Imagenes, etc) y mostrar los archivos ocultos. allí se deberá ver una carpeta llamada .compiz, yo la renombraría, y por descartar también lo haría con la carpeta .config

lo que yo creo es más problemas en la instalación, incluyendo el uso del driver genérico de video. ahora, si se presiona la tecla Meta (tecla windows) y el launcher no aparece ya reinstalar el compiz en instalarle el gestor de configuración compizcofig si no se tiene instalado.

el login incorrect es por error en la contraseña del usuario no por más.

---

### Post by micemo on 2015-05-26
Me ocurre exactamente lo mismo, con la terminal no me reconoce usuario y contraseña (que pongo bien) y yendo a compizconfig no me deja abrirlo. Conseguiste arreglarlo????

---

