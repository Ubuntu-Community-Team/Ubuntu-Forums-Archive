---
title: "Ubuntu Server problema con firefox"
date: 2023-02-20
forum: Centroamerica Team
---

### Post by valgrif on 2023-02-20
Buenas, tengo una maquina virtual (creda con UTM) de ubuntu server 22.04.1 arm64, trabajo desde un MacBook pro m1.
Instalo el entorno gráfico y aparentemente todo funciona correctamente salvo el Firefox, el cual cuando trato de abrir no me muestra la ventana y se queda atrapado en bucle.
He probado a desintalarlo y reinstalarlo, actualizarlo, he probado a crear otra maquina virtual y el problema persiste. EL cual, ni siquiera entiendo porque me ocurre, pues como digo las otras aplicaciones funcionan correctamente
Si alguien puede ayudarme se lo agradezco

Saludos

---

### Post by lacrosby on 2023-02-21
Hola,


¿Qué versión de Firefox estás intentando usar? ¿Has intentado actualizar el paquete? tipo


sudo apt update && sudo apt full-upgrade


¿Qué sucede si carga Firefox desde la terminal? Que error da?

Perdón por los errores de traducción, usé el traductor de Google

---

### Post by valgrif on 2023-02-21
Si cargo desde terminal me aparece este error:

[COLOR=#232629][FONT=-apple-system]Gtk-Message: 15:43:41.763: Not loading module "atk-bridge": The functionality is provided by GTK natively. Please try to not load it. [GFX-]: glxtest: VA-API test failed: failed to initialise VAAPI connection. 
ATENNTION: default value of option mesa_glthread overrriden by enviroment[/FONT][/COLOR][COLOR=#232629][FONT=-apple-system] [/FONT][/COLOR]

---

### Post by lacrosby on 2023-02-21
¿Se carga cuando ejecuta este comando desde la consola?

[COLOR=#000000][FONT=monospace]firefox -safe-mode[/FONT][/COLOR]

---

### Post by valgrif on 2023-02-22
No, cunado ejecuto "firefox -safe-mode" aparece el mismo error :(

---

