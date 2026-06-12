---
title: "I can't edit menus"
date: 2009-06-17
forum: General Help
---

### Post by hadouken on 2009-06-17
Hi, I was trying to edit menus but after removing a program, everything under programs menu dissapeared and now I can't edit menus. Please help!

---

### Post by VMC on 2009-06-17
> **hadouken said:**
> Hi, I was trying to edit menus but after removing a program, everything under programs menu dissapeared and now I can't edit menus. Please help!

Not quite sure what you mean "everything under programs". Try right-click under Applications. Then Edit menus.

---

### Post by hadouken on 2009-06-17
I mean, alacarte doesn't seem to work and the Applications menu doesn't show anything.

---

### Post by jenkinbr on 2009-06-17
Do you know what application you removed?

---

### Post by hadouken on 2009-06-17
I think it was only a graphical adventure game.

---

### Post by jenkinbr on 2009-06-17
Could you try someting quick?

Press alt+f2
enter 'gnome-terminal'

enter the command 'update-menus'

see if that helps

---

### Post by hadouken on 2009-06-17
It says file doesn't exist.

---

### Post by jenkinbr on 2009-06-17
There's our problem

in the same terminal window, run

```
sudo apt-get install menu
```

---

### Post by hadouken on 2009-06-17
sorry, it would be more like "command not accepted" I'm using ubuntu in spanish from spain if that helps.

---

### Post by hadouken on 2009-06-17
> **jenkinbr said:**
> There's our problem

in the same terminal window, run

```
sudo apt-get install menu
```

Nope, it doesn't work.

---

### Post by jenkinbr on 2009-06-17
> **hadouken said:**
> Nope, it doesn't work.
What was the output?

---

### Post by hadouken on 2009-06-17
[I]Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Se instalarán los siguientes paquetes NUEVOS:
  menu
0 actualizados, 1 se instalarán, 0 para eliminar y 5 no actualizados.
Necesito descargar 438kB de archivos.
Se utilizarán 1987kB de espacio de disco adicional después de esta operación.
Des:1 [http://sv.archive.ubuntu.com](http://sv.archive.ubuntu.com) jaunty/universe menu 2.1.41ubuntu1 [438kB]
Descargados 438kB en 12s (35,8kB/s)                                            
Seleccionando el paquete menu previamente no seleccionado.
(Leyendo la base de datos ...  
146613 ficheros y directorios instalados actualmente.)
Desempaquetando menu (de .../menu_2.1.41ubuntu1_i386.deb) ...
Procesando disparadores para man-db ...
Procesando disparadores para doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Configurando menu (2.1.41ubuntu1) ...[/I]

The command worked, but it didn't fix my problem.

---

### Post by jenkinbr on 2009-06-17
> **hadouken said:**
> [I]Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Se instalarán los siguientes paquetes NUEVOS:
  menu
0 actualizados, 1 se instalarán, 0 para eliminar y 5 no actualizados.
Necesito descargar 438kB de archivos.
Se utilizarán 1987kB de espacio de disco adicional después de esta operación.
Des:1 [http://sv.archive.ubuntu.com](http://sv.archive.ubuntu.com) jaunty/universe menu 2.1.41ubuntu1 [438kB]
Descargados 438kB en 12s (35,8kB/s)                                            
Seleccionando el paquete menu previamente no seleccionado.
(Leyendo la base de datos ...  
146613 ficheros y directorios instalados actualmente.)
Desempaquetando menu (de .../menu_2.1.41ubuntu1_i386.deb) ...
Procesando disparadores para man-db ...
Procesando disparadores para doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Configurando menu (2.1.41ubuntu1) ...[/I]

The command worked, but it didn't fix my problem.
Try

```
sudo apt-get install gnome-menus
```

---

### Post by hadouken on 2009-06-17
It says something like: gnome it's already in it's most current version

---

### Post by jenkinbr on 2009-06-17
Did you run 'sudo apt-get install gnome menus' or 'sudo apt-get install gnome-menus'

They are two different commands.

If 'gnome-menus' says it's at it's most recent version, then try 'sudo apt-get install --reinstall gnome-menus'

---

### Post by hadouken on 2009-06-17
I tried `sudo apt-get install gnome-menus`, and 'sudo apt-get install --reinstall gnome-menus' dosn't fix it either.

---

### Post by rcayea on 2009-06-17
If you deleted from your menu then look in home folder -> .config/menus/applications.menu (.config is a hidden folder, when in home folder go Ctrl+h if not visible

You should see an entry like this (i added the red
Code:

</Menu>
	<Menu>
		<Name>wine-wine</Name>
		[COLOR="Red"]<Deleted/>[/COLOR]
	</Menu>
</Menu>

Remove what's in red, and save


Does this help?

---

### Post by jenkinbr on 2009-06-17
That's odd - wait!

I forgot to tell you to run 'update-menus' again after we installed menu.  Try that.

---

### Post by hadouken on 2009-06-17
> **rcayea said:**
> If you deleted from your menu then look in home folder -> .config/menus/applications.menu (.config is a hidden folder, when in home folder go Ctrl+h if not visible

You should see an entry like this (i added the red
Code:

</Menu>
    <Menu>
        <Name>wine-wine</Name>
        [COLOR=Red]<Deleted/>[/COLOR]
    </Menu>
</Menu>

Remove what's in red, and save


Does this help?

I don't see something like that,

and 'update-menus' doesn't fix it.

---

### Post by hadouken on 2009-06-17
Hey, I found in another forum the solution, open the terminal and use:
"rm -f ~/.config/menus/applications.menu"
Problem solved! Thanks guys!

---

### Post by jenkinbr on 2009-06-17
Glad you solved it.

Thanks for posting the fix for the benefit of others with the same problem.

---

