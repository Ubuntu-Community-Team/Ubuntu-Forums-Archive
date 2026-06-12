---
title: "Problem removing package bnetd"
date: 2009-02-05
forum: General Help
---

### Post by HoLiC on 2009-02-05
Hi all,

 I'm newbie in ubuntu world, and i have a little problem removing a package.

I have a Amd 64 processor, i have installed kubuntu intrepid ibex (in spanish), and this is the package info:

> ~$ aptitude -V show bnetd
Paquete: bnetd                        
Estado: configurado parcialmente      
Instalado automáticamente: no         
Versión: 0.4.25-8                     
Prioridad: opcional                   
Sección: universe/net                 
Desarrollador: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Tamaño sin comprimir: 1196k                                         
Depende de: libc6 (>= 2.4)                                          
Sugiere: fortune                                                    
Proporcionado por: pvpgn                                            
Descripción: Gaming server that emulates Battle.net(R)

And the error is:
> ~$ sudo apt-get remove bnetd
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo la información de estado... Hecho
Los siguientes paquetes se ELIMINARÁN:
  bnetd
0 actualizados, 0 se instalarán, 1 para eliminar y 0 no actualizados.
1 no instalados del todo o eliminados.
Se liberarán 1196kB después de desempaquetar.
¿Desea continuar [S/n]?
dpkg: error al procesar bnetd (--remove):
 El paquete está en un estado muy malo e inconsistente - debe reinstalarlo
 antes de intentar desinstalarlo.
Se encontraron errores al procesar:
 bnetd
E: Sub-process /usr/bin/dpkg returned an error code (1)

I was looking in google trying this:
[list]
[*]sudo apt-get -f install
> Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo la información de estado... Hecho
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
1 no instalados del todo o eliminados.
Necesito descargar 405kB de archivos.
Se utilizarán 0B de espacio de disco adicional después de desempaquetar.
Des:1 [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) intrepid/universe bnetd 0.4.25-8 [405kB]
Descargados 405kB en 0s (458kB/s)
Seleccionando el paquete bnetd previamente no seleccionado.
(Leyendo la base de datos ...
158404 ficheros y directorios instalados actualmente.)
Preparando para reemplazar bnetd 0.4.25-8 (usando .../bnetd_0.4.25-8_amd64.deb) ...
Stopping Battle.net(R) gaming server: invoke-rc.d: initscript bnetd, action "stop" failed.
dpkg: aviso - script de `pre-removal' antiguo devolvió código de error 1
dpkg - probando el script del nuevo paquete en su lugar...
Stopping Battle.net(R) gaming server: invoke-rc.d: initscript bnetd, action "stop" failed.
dpkg: error al procesar /var/cache/apt/archives/bnetd_0.4.25-8_amd64.deb (--unpack):
 el subproceso script pre-removal nuevo devolvió el código de salida de error 1
chown: no se puede acceder a «/var/run/bnetd»: No existe el fichero ó directorio
dpkg: error al reorganizar:
 el subproceso post-installation script devolvió el código de salida de error 1
Se encontraron errores al procesar:
 /var/cache/apt/archives/bnetd_0.4.25-8_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

[*]sudo dpkg --configure -a
> dpkg: error al procesar bnetd (--configure):
 El paquete está en un estado grave de inconsistencia - debe reinstalarlo
 antes de intentar su configuración.
Se encontraron errores al procesar:
 bnetd
[/list]

I'm still getting the same error
and i dont know how to fix this, i was looking for bugs too ([https://bugs.launchpad.net/ubuntu/+source/bnetd/+bug/323314](https://bugs.launchpad.net/ubuntu/+source/bnetd/+bug/323314)) but i don't know how this working.

If anybody have any ideas, plz i will be appreciate

PD: sorry if i translate something wrong, my first lenguage is spanish.

---

### Post by jwillson on 2011-10-12
Hi HoLiC,

Check out this bug report:

[https://bugs.launchpad.net/ubuntu/+s...td/+bug/846560](https://bugs.launchpad.net/ubuntu/+s...td/+bug/846560)

Here's what ACTUALLY WORKED for me:
Note: XXX should be replaced with the actual PID number that you get.

sudo /etc/init.d/bnetd stop
ps -e -o pid -o args | grep bnetd
XXX bnetd
sudo kill -9 XXX
rm /etc/init.d/bnetd
sudo apt-get remove bnetd

Notice the "rm /etc/init.bnetd". That's necessary to be able to actually remove it. I hope this helps!

---

