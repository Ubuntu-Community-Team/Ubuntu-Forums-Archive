---
title: "Problemas Phyton en Ubuntu 9.04"
date: 2009-09-04
forum: Colombia Team - Colombia
---

### Post by zaratan on 2009-09-04
Hola Comunidad de ubuntu Colombia, este es mi primer post y pues la verdad es que tengo un problema grande, recientemente se me ocurrio la maravillosa idea de instalar pykaraoke en ubuntu 9.04, siguiendo un tutorial de esos que uno encuentra en google trate de seguir los pasos y me baje el archivo de la pagina oficial y trate de compilarlo con python el setup.py para cual salia un error ya que tenia la version 2.6 y necesitaba la 2.5, luego me di cuenta que tambien la version 2.5 venia instalada, pero busque y logre poner en el eleccion la que mas quisiera por lo que elegi la 2.5 cosa que no me mejoro. Rindiendome me baje versiones estables para ubuntu de pykaraoke pero el archivo .deb, trate de instalarlo pero nada tampoco funciono, finalmente y no se porque no lo hize de primero puse en la consolo sudo apt-get install pykaraoke lo cual trato de instalar el programa con un errores pero la aplicacion funcionaba y pues de hecho funciona. 

a que voy con todo esto ...ahora no puedo instalar programas  python:(:confused: por ejemplo tratando de actualizar pidgin a la version 2.6 con soporte de audio y video me sale el siguiente error para cualquier cosa que implique utilizar python, desintalar o instalar.

```
Obj http://packages.medibuntu.org jaunty/non-free Packages                     
Obj http://co.archive.ubuntu.com jaunty/main Packages                          
Obj http://co.archive.ubuntu.com jaunty/restricted Packages                    
Obj http://co.archive.ubuntu.com jaunty/main Sources                           
Obj http://co.archive.ubuntu.com jaunty/restricted Sources                     
Obj http://co.archive.ubuntu.com jaunty/universe Packages                      
Obj http://co.archive.ubuntu.com jaunty/universe Sources                       
Obj http://co.archive.ubuntu.com jaunty/multiverse Packages                    
Obj http://ppa.launchpad.net jaunty Release                                    
Des:4 http://ppa.launchpad.net jaunty Release [74,7kB]                         
Obj http://co.archive.ubuntu.com jaunty/multiverse Sources                     
Obj http://co.archive.ubuntu.com jaunty-updates/main Packages                  
Obj http://co.archive.ubuntu.com jaunty-updates/restricted Packages            
Obj http://co.archive.ubuntu.com jaunty-updates/main Sources                   
Obj http://co.archive.ubuntu.com jaunty-updates/restricted Sources             
Obj http://co.archive.ubuntu.com jaunty-updates/universe Packages              
Obj http://co.archive.ubuntu.com jaunty-updates/universe Sources               
Obj http://co.archive.ubuntu.com jaunty-updates/multiverse Packages            
Obj http://co.archive.ubuntu.com jaunty-updates/multiverse Sources             
Des:5 http://ppa.launchpad.net jaunty/main Packages [9168B]                    
Des:6 http://ppa.launchpad.net jaunty/main Sources [2637B]                     
Obj http://ppa.launchpad.net jaunty/main Packages                              
Des:7 http://ppa.launchpad.net jaunty/main Packages [9649B]                    
Obj http://security.ubuntu.com jaunty-security Release.gpg                     
Ign http://security.ubuntu.com jaunty-security/main Translation-es
Ign http://security.ubuntu.com jaunty-security/restricted Translation-es
Ign http://security.ubuntu.com jaunty-security/universe Translation-es
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-es
Obj http://security.ubuntu.com jaunty-security Release
Obj http://security.ubuntu.com jaunty-security/main Packages
Obj http://security.ubuntu.com jaunty-security/restricted Packages
Obj http://security.ubuntu.com jaunty-security/main Sources
Obj http://security.ubuntu.com jaunty-security/restricted Sources
Obj http://security.ubuntu.com jaunty-security/universe Packages
Obj http://security.ubuntu.com jaunty-security/universe Sources
Obj http://security.ubuntu.com jaunty-security/multiverse Packages
Obj http://security.ubuntu.com jaunty-security/multiverse Sources
Descargados 171kB en 4s (40,1kB/s)
Leyendo lista de paquetes... Hecho
W: Duplicate sources.list entry http://ppa.launchpad.net jaunty/main Packages (/var/lib/apt/lists/ppa.launchpad.net_ubuntu-mozilla-daily_ppa_ubuntu_dists_jaunty_main_binary-i386_Packages)
W: Tal vez quiera ejecutar 'apt-get update' para corregir estos problemas
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Los siguientes paquetes se han retenido:
  libpurple0 pidgin pidgin-data
Se actualizarán los siguientes paquetes:
  gstreamer0.10-alsa gstreamer0.10-gnomevfs gstreamer0.10-plugins-bad
  gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps
  gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly
  gstreamer0.10-pulseaudio gstreamer0.10-tools gstreamer0.10-x
  libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libpurple-bin
  python-gst0.10 xulrunner-1.9.1 xulrunner-1.9.1-gnome-support
16 actualizados, 0 se instalarán, 0 para eliminar y 3 no actualizados.
3 no instalados del todo o eliminados.
Necesito descargar 13,7MB de archivos.
Se utilizarán 451kB de espacio de disco adicional después de esta operación.
¿Desea continuar [S/n]? s
Des:1 http://ppa.launchpad.net jaunty/main libgstreamer0.10-0 0.10.24-1~pidgin1.9.04 [769kB]
Des:2 http://ppa.launchpad.net jaunty/main libgstreamer-plugins-base0.10-0 0.10.24-1~pidgin1.9.04 [388kB]
Des:3 http://ppa.launchpad.net jaunty/main gstreamer0.10-alsa 0.10.24-1~pidgin1.9.04 [36,3kB]
Des:4 http://ppa.launchpad.net jaunty/main gstreamer0.10-gnomevfs 0.10.24-1~pidgin1.9.04 [16,1kB]
Des:5 http://ppa.launchpad.net jaunty/main gstreamer0.10-plugins-base 0.10.24-1~pidgin1.9.04 [616kB]
Des:6 http://ppa.launchpad.net jaunty/main gstreamer0.10-tools 0.10.24-1~pidgin1.9.04 [46,4kB]
Des:7 http://ppa.launchpad.net jaunty/main gstreamer0.10-plugins-base-apps 0.10.24-1~pidgin1.9.04 [51,1kB]
Des:8 http://ppa.launchpad.net jaunty/main gstreamer0.10-plugins-ugly 0.10.12-1~pidgin1.9.04 [324kB]
Des:9 http://ppa.launchpad.net jaunty/main gstreamer0.10-plugins-bad 0.10.13-1ubuntu1~pidgin1.9.04 [1185kB]
Des:10 http://ppa.launchpad.net jaunty/main gstreamer0.10-plugins-good 0.10.15-2ubuntu1~pidgin4.9.04 [1345kB]
Des:11 http://ppa.launchpad.net jaunty/main gstreamer0.10-pulseaudio 0.10.15-2ubuntu1~pidgin4.9.04 [77,8kB]
Des:12 http://ppa.launchpad.net jaunty/main gstreamer0.10-x 0.10.24-1~pidgin1.9.04 [74,0kB]
Des:13 http://ppa.launchpad.net jaunty/main libpurple-bin 1:2.6.1-1ubuntu0~pidgin1.9.04 [97,1kB]
Des:14 http://ppa.launchpad.net jaunty/main python-gst0.10 0.10.16-1~pidgin1.9.04 [461kB]
Des:15 http://ppa.launchpad.net jaunty/main xulrunner-1.9.1-gnome-support 1.9.1.4~hg20090902r26316+nobinonly-0ubuntu2~umd1~jaunty [40,2kB]
Des:16 http://ppa.launchpad.net jaunty/main xulrunner-1.9.1 1.9.1.4~hg20090902r26316+nobinonly-0ubuntu2~umd1~jaunty [8135kB]
Descargados 13,7MB en 2min 51s (79,6kB/s)                                      
(Leyendo la base de datos ...  
182967 ficheros y directorios instalados actualmente.)
Preparando para reemplazar libgstreamer0.10-0 0.10.22-1 (usando .../libgstreamer0.10-0_0.10.24-1~pidgin1.9.04_i386.deb) ...
Desempaquetando el reemplazo de libgstreamer0.10-0 ...
Preparando para reemplazar libgstreamer-plugins-base0.10-0 0.10.22-5 (usando .../libgstreamer-plugins-base0.10-0_0.10.24-1~pidgin1.9.04_i386.deb) ...
Desempaquetando el reemplazo de libgstreamer-plugins-base0.10-0 ...
Preparando para reemplazar gstreamer0.10-alsa 0.10.22-5 (usando .../gstreamer0.10-alsa_0.10.24-1~pidgin1.9.04_i386.deb) ...
Desempaquetando el reemplazo de gstreamer0.10-alsa ...
Preparando para reemplazar gstreamer0.10-gnomevfs 0.10.22-5 (usando .../gstreamer0.10-gnomevfs_0.10.24-1~pidgin1.9.04_i386.deb) ...
Desempaquetando el reemplazo de gstreamer0.10-gnomevfs ...
Preparando para reemplazar gstreamer0.10-plugins-base 0.10.22-5 (usando .../gstreamer0.10-plugins-base_0.10.24-1~pidgin1.9.04_i386.deb) ...
Desempaquetando el reemplazo de gstreamer0.10-plugins-base ...
Preparando para reemplazar gstreamer0.10-tools 0.10.22-1 (usando .../gstreamer0.10-tools_0.10.24-1~pidgin1.9.04_i386.deb) ...
Desempaquetando el reemplazo de gstreamer0.10-tools ...
Preparando para reemplazar gstreamer0.10-plugins-base-apps 0.10.22-5 (usando .../gstreamer0.10-plugins-base-apps_0.10.24-1~pidgin1.9.04_i386.deb) ...
Desempaquetando el reemplazo de gstreamer0.10-plugins-base-apps ...
Preparando para reemplazar gstreamer0.10-plugins-ugly 0.10.10.2-1build1 (usando .../gstreamer0.10-plugins-ugly_0.10.12-1~pidgin1.9.04_i386.deb) ...
Desempaquetando el reemplazo de gstreamer0.10-plugins-ugly ...
Preparando para reemplazar gstreamer0.10-plugins-bad 0.10.11-2ubuntu1 (usando .../gstreamer0.10-plugins-bad_0.10.13-1ubuntu1~pidgin1.9.04_i386.deb) ...
Desempaquetando el reemplazo de gstreamer0.10-plugins-bad ...
Preparando para reemplazar gstreamer0.10-plugins-good 0.10.14-1ubuntu0.1 (usando .../gstreamer0.10-plugins-good_0.10.15-2ubuntu1~pidgin4.9.04_i386.deb) ...
Desempaquetando el reemplazo de gstreamer0.10-plugins-good ...
Preparando para reemplazar gstreamer0.10-pulseaudio 0.10.14-1ubuntu0.1 (usando .../gstreamer0.10-pulseaudio_0.10.15-2ubuntu1~pidgin4.9.04_i386.deb) ...
Desempaquetando el reemplazo de gstreamer0.10-pulseaudio ...
Preparando para reemplazar gstreamer0.10-x 0.10.22-5 (usando .../gstreamer0.10-x_0.10.24-1~pidgin1.9.04_i386.deb) ...
Desempaquetando el reemplazo de gstreamer0.10-x ...
Preparando para reemplazar libpurple-bin 1:2.5.5-1ubuntu8.4 (usando .../libpurple-bin_1%3a2.6.1-1ubuntu0~pidgin1.9.04_all.deb) ...
Desempaquetando el reemplazo de libpurple-bin ...
Preparando para reemplazar python-gst0.10 0.10.14-1ubuntu1 (usando .../python-gst0.10_0.10.16-1~pidgin1.9.04_i386.deb) ...
dpkg: aviso - script de `pre-removal' antiguo devolvió código de error 1
dpkg - probando el script del nuevo paquete en su lugar...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2190, in <module>
    main()
  File "/usr/bin/pycentral", line 2184, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1638, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 276, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.6
dpkg: error al procesar /var/cache/apt/archives/python-gst0.10_0.10.16-1~pidgin1.9.04_i386.deb (--unpack):
 el subproceso script pre-removal nuevo devolvió el código de salida de error 1
dpkg: error al reorganizar:
 el subproceso post-installation script devolvió el código de salida de error 1
Preparando para reemplazar xulrunner-1.9.1-gnome-support 1.9.1.4~hg20090901r26311+nobinonly-0ubuntu2~umd1~jaunty (usando .../xulrunner-1.9.1-gnome-support_1.9.1.4~hg20090902r26316+nobinonly-0ubuntu2~umd1~jaunty_i386.deb) ...
Desempaquetando el reemplazo de xulrunner-1.9.1-gnome-support ...
Preparando para reemplazar xulrunner-1.9.1 1.9.1.4~hg20090901r26311+nobinonly-0ubuntu2~umd1~jaunty (usando .../xulrunner-1.9.1_1.9.1.4~hg20090902r26316+nobinonly-0ubuntu2~umd1~jaunty_i386.deb) ...
Desempaquetando el reemplazo de xulrunner-1.9.1 ...
Procesando disparadores para man-db ...
Se encontraron errores al procesar:
 /var/cache/apt/archives/python-gst0.10_0.10.16-1~pidgin1.9.04_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Estoy deseperado no soy muy nuevo en ubuntu, y no quiero llegar a instalarlo otra vez porque se que la comunidad tiene buen soporte.

---

### Post by dirakx on 2010-01-06
Saludos.

Parece ser que allí hay un error general de python, la versión que cambiaste en el archivo, no es igual a la versión por default en el sistema. Revisa bien la sintaxis del archivo que cambiaste por que es la configuración general de python.

---

### Post by dirakx on 2010-01-06
Específicamente tienes que tener bien el archivo similar a este, en ubuntu.


/usr/share/python/debian_defaults

---

