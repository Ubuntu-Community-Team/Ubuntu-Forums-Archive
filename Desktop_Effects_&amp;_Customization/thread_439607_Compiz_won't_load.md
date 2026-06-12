---
title: "Compiz won't load"
date: 2007-05-10
forum: Desktop Effects &amp; Customization
---

### Post by loopeando on 2007-05-10
For an unknow reason Compiz won't start.

I've not changed anything and yesterday it worked perfectly.

When I try to start Compiz from the console I get this:

```
loop@loop-laptop:~$ compiz
/usr/bin/compiz.real: Unknown option '--no-fbo'
/usr/bin/compiz.real: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
/usr/bin/compiz.real: No manageable screens found on display :0.0
Advertencia del gestor de ventanas: «» encontrado en la base de datos de configuración no es un valor válido para la combinación de teclas «toggle_shaded»
Advertencia del gestor de ventanas: La ventana 0 en la pantalla «:0.0» ya tiene un gestor de ventanas, intente usar la opción «--replace» para reemplazar el gestor de ventanas activo.

```

How can i fix this?

Thx in advance!

---

### Post by RAOF on 2007-05-11
Just running "compiz" should never have worked, you'd want at least "compiz --replace", and probably "compiz --replace gconf".

It looks like you're using a non-Ubuntu version of Compiz, though (since the Ubuntu version understands the --no-fbo switch)

---

