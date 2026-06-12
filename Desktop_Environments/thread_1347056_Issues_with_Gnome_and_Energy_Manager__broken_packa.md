---
title: "Issues with Gnome and Energy Manager / broken packages"
date: 2009-12-05
forum: Desktop Environments
---

### Post by Ken-san on 2009-12-05
Seems like anytime I post in these forums I have a new problem... Anyway, here goes...

Ever since a couple of days ago, I've been getting an unusual error upon booting into ubuntu, which reads something like this:

"The default configuration of the energy management system was not properly installed. Please contact your system administrator." (Which would be entirely useless, because my sysadmin is... me :P)

GNOME won't work at all, KDE (which is what I'm using for the moment) works fine. However, there seems to be a related problem.

This is the output of sudo aptitude full-upgrade (I assumed doing an upgrade would fix the issue -- and do note that it's in spanish; if there's anything that needs translating, please let me know):
```
carlos@inuki:~$ sudo aptitude full-upgrade
Leyendo lista de paquetes... Hecho        
Creando árbol de dependencias             
Leyendo la información de estado... Hecho 
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho
Se instalarán los siguiente paquetes NUEVOS:    
  linux-headers-2.6.31-16{a} linux-headers-2.6.31-16-generic{a} linux-image-2.6.31-16-generic 
Se actualizarán los siguientes paquetes:                                                      
  compiz-gnome linux-generic linux-headers-generic linux-image-generic rhythmbox              
Se configurarán los siguientes paquetes que están ahora parcialmente instalados:              
  compiz compiz-core compiz-plugins compiz-wrapper evolution-indicator google-chrome-unstable libdecoration0 libglib2.0-0 libglib2.0-data libglib2.0-dev libsmbclient libwbclient0 linux-libc-dev samba-common 
  samba-common-bin smbclient                                                                                                                                                                                   
5 paquetes actualizados, 3 nuevos instalados, 0 para eliminar y 0 sin actualizar.                                                                                                                              
Necesito descargar 39,1MB/41,2MB de archivos. Después de desempaquetar se usarán 196MB.                                                                                                                        
¿Quiere continuar? [Y/n/?] y                                                                                                                                                                                   
Escribiendo información de estado extendido... Hecho                                                                                                                                                           
Des:1 http://ve.archive.ubuntu.com karmic-updates/main linux-image-2.6.31-16-generic 2.6.31-16.52 [28,9MB]                                                                                                     
Des:2 http://ve.archive.ubuntu.com karmic-updates/main linux-generic 2.6.31.16.29 [3270B]                                                                                                                                     
Des:3 http://ve.archive.ubuntu.com karmic-updates/main linux-image-generic 2.6.31.16.29 [3282B]                                                                                                                               
Des:4 http://ve.archive.ubuntu.com karmic-updates/main linux-headers-2.6.31-16 2.6.31-16.52 [9527kB]                                                                                                                          
Des:5 http://ve.archive.ubuntu.com karmic-updates/main linux-headers-2.6.31-16-generic 2.6.31-16.52 [692kB]                                                                                                                   
Des:6 http://ve.archive.ubuntu.com karmic-updates/main linux-headers-generic 2.6.31.16.29 [3270B]                                                                                                                             
Descargados 39,1MB en 12min 16s (53,2kB/s).                                                                                                                                                                                   
(Leyendo la base de datos ...  00%                                                                                                                                                                                            
187330 ficheros y directorios instalados actualmente.)                                                                                                                                                                        
Preparando para reemplazar compiz-gnome 1:0.8.4-0ubuntu2 (usando .../compiz-gnome_1%3a0.8.4-0ubuntu2.1_amd64.deb) ...                                                                                                         
Desempaquetando el reemplazo de compiz-gnome ...                                                                                                                                                                              
dpkg: aviso: script de `post-removal' antiguo devolvió un error de salida 249                                                                                                                                                 
dpkg - probando el script del nuevo paquete en su lugar...                                                                                                                                                                    
dpkg: error al procesar /var/cache/apt/archives/compiz-gnome_1%3a0.8.4-0ubuntu2.1_amd64.deb (--unpack):                                                                                                                       
 el subproceso script post-removal nuevo devolvió el código de salida de error 249                                                                                                                                            
dpkg: error al reorganizar:                                                                                                                                                                                                   
 el subproceso script post-removal nuevo devolvió el código de salida de error 249                                                                                                                                            
Preparando para reemplazar rhythmbox 0.12.5-0ubuntu5 (usando .../rhythmbox_0.12.5-0ubuntu5.1_amd64.deb) ...                                                                                                                   
Desempaquetando el reemplazo de rhythmbox ...                                                                                                                                                                                 
dpkg: aviso: script de `post-removal' antiguo devolvió un error de salida 249                                                                                                                                                 
dpkg - probando el script del nuevo paquete en su lugar...                                                                                                                                                                    
dpkg: error al procesar /var/cache/apt/archives/rhythmbox_0.12.5-0ubuntu5.1_amd64.deb (--unpack):                                                                                                                             
 el subproceso script post-removal nuevo devolvió el código de salida de error 249                                                                                                                                            
dpkg: error al reorganizar:                                                                                                                                                                                                   
 el subproceso script post-removal nuevo devolvió el código de salida de error 249                                                                                                                                            
Seleccionando el paquete linux-image-2.6.31-16-generic previamente no seleccionado.                                                                                                                                           
Desempaquetando linux-image-2.6.31-16-generic (de .../linux-image-2.6.31-16-generic_2.6.31-16.52_amd64.deb) ...                                                                                                               
Done.                                                                                                                                                                                                                         
Preparando para reemplazar linux-generic 2.6.31.15.28 (usando .../linux-generic_2.6.31.16.29_amd64.deb) ...                                                                                                                   
Desempaquetando el reemplazo de linux-generic ...                                                                                                                                                                             
Preparando para reemplazar linux-image-generic 2.6.31.15.28 (usando .../linux-image-generic_2.6.31.16.29_amd64.deb) ...                                                                                                       
Desempaquetando el reemplazo de linux-image-generic ...                                                                                                                                                                       
Seleccionando el paquete linux-headers-2.6.31-16 previamente no seleccionado.                                                                                                                                                 
Desempaquetando linux-headers-2.6.31-16 (de .../linux-headers-2.6.31-16_2.6.31-16.52_all.deb) ...                                                                                                                             
Seleccionando el paquete linux-headers-2.6.31-16-generic previamente no seleccionado.                                                                                                                                         
Desempaquetando linux-headers-2.6.31-16-generic (de .../linux-headers-2.6.31-16-generic_2.6.31-16.52_amd64.deb) ...                                                                                                           
Preparando para reemplazar linux-headers-generic 2.6.31.15.28 (usando .../linux-headers-generic_2.6.31.16.29_amd64.deb) ...                                                                                                   
Desempaquetando el reemplazo de linux-headers-generic ...                                                                                                                                                                     
Procesando disparadores para desktop-file-utils ...                                                                                                                                                                           
Procesando disparadores para man-db ...                                                                                                                                                                                       
Procesando disparadores para menu ...                                                                                                                                                                                         
Procesando disparadores para hicolor-icon-theme ...                                                                                                                                                                           
Se encontraron errores al procesar:                                                                                                                                                                                           
 /var/cache/apt/archives/compiz-gnome_1%3a0.8.4-0ubuntu2.1_amd64.deb                                                                                                                                                          
 /var/cache/apt/archives/rhythmbox_0.12.5-0ubuntu5.1_amd64.deb                                                                                                                                                                
E: Sub-process /usr/bin/dpkg returned an error code (1)                                                                                                                                                                       
Un paquete no se pudo instalar. Intentado recuperarse:                                                                                                                                                                        
dpkg: problemas de dependencias impiden la configuración de compiz:                                                                                                                                                           
 compiz depende de compiz-gnome | compiz-kde; sin embargo:                                                                                                                                                                    
  El paquete `compiz-gnome' no está instalado.                                                                                                                                                                                
  El paquete `compiz-kde' no está instalado.                                                                                                                                                                                  
dpkg: error al procesar compiz (--configure):                                                                                                                                                                                 
 problemas de dependencias - se deja sin configurar                                                                                                                                                                           
Configurando libwbclient0 (2:3.4.0-3ubuntu5.2) ...                                                                                                                                                                            

Configurando linux-libc-dev (2.6.31-16.52) ...
Configurando libdecoration0 (1:0.8.4-0ubuntu2.1) ...

Configurando linux-headers-2.6.31-16 (2.6.31-16.52) ...
Configurando libsmbclient (2:3.4.0-3ubuntu5.2) ...     

Configurando samba-common (2:3.4.0-3ubuntu5.2) ...

Configurando linux-headers-2.6.31-16-generic (2.6.31-16.52) ...
Examining /etc/kernel/header_postinst.d.                       
run-parts: executing /etc/kernel/header_postinst.d/dkms        
 * Running DKMS auto installation service for kernel 2.6.31-16-generic                                                                                                                                                        
 *  nvidia (185.18.36)...                                                                                                                                                                                                     nvidia (185.18.36): Installing module.                                                                                                                                                                                        
..........                                                                                                                                                                                                                    
......                                                                                                                                                                                                                        
                                                                                                                                                                                                                       [ OK ] 
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common                                                                                                                                                              

Configurando smbclient (2:3.4.0-3ubuntu5.2) ...
Configurando linux-image-2.6.31-16-generic (2.6.31-16.52) ...
Running depmod.                                              
update-initramfs: Generating /boot/initrd.img-2.6.31-16-generic
Running postinst hook script /usr/sbin/update-grub.            
Generating grub.cfg ...                                        
Found linux image: /boot/vmlinuz-2.6.31-16-generic             
Found initrd image: /boot/initrd.img-2.6.31-16-generic         
Found linux image: /boot/vmlinuz-2.6.31-15-generic             
Found initrd image: /boot/initrd.img-2.6.31-15-generic         
Found linux image: /boot/vmlinuz-2.6.31-14-generic             
Found initrd image: /boot/initrd.img-2.6.31-14-generic         
Found memtest86+ image: /boot/memtest86+.bin                   
Found Windows 7 (loader) on /dev/sda1                          
done                                                           
Examining /etc/kernel/postinst.d.                              
run-parts: executing /etc/kernel/postinst.d/dkms               
 * Running DKMS auto installation service for kernel 2.6.31-16-generic                                                                                                                                                        
 *  nvidia (185.18.36)...                                                                                                                                                                                                     nvidia (185.18.36): Already installed on this kernel.                                                                                                                                                                         
                                                                                                                                                                                                                       [ OK ] 
run-parts: executing /etc/kernel/postinst.d/nvidia-common                                                                                                                                                                     

Configurando samba-common-bin (2:3.4.0-3ubuntu5.2) ...
update-alternatives: usar /usr/bin/nmblookup.samba3 para proporcionar /usr/bin/nmblookup (nmblookup) en modo automático
update-alternatives: usar /usr/bin/net.samba3 para proporcionar /usr/bin/net (net) en modo automático                  
update-alternatives: usar /usr/bin/testparm.samba3 para proporcionar /usr/bin/testparm (testparm) en modo automático   

Configurando linux-headers-generic (2.6.31.16.29) ...
Configurando compiz-wrapper (1:0.8.4-0ubuntu2.1) ... 
Configurando libglib2.0-0 (2.22.3-0ubuntu1) ...      

Configurando libglib2.0-data (2.22.3-0ubuntu1) ...
Configurando compiz-core (1:0.8.4-0ubuntu2.1) ... 
Configurando linux-image-generic (2.6.31.16.29) ...
Configurando linux-generic (2.6.31.16.29) ...      
Configurando google-chrome-unstable (4.0.249.22-r33427) ...

Configurando evolution-indicator (0.2.4-0ubuntu3.1) ...
dpkg: error al procesar evolution-indicator (--configure):
 el subproceso script post-installation instalado devolvió el código de salida de error 249
Configurando libglib2.0-dev (2.22.3-0ubuntu1) ...                                          
Configurando compiz-plugins (1:0.8.4-0ubuntu2.1) ...                                       
Procesando disparadores para libc-bin ...                                                  
ldconfig deferred processing now taking place                                              
Procesando disparadores para menu ...                                                      
Se encontraron errores al procesar:                                                        
 compiz                                                                                    
 evolution-indicator                                                                       
Leyendo lista de paquetes... Hecho                                                         
Creando árbol de dependencias                                                              
Leyendo la información de estado... Hecho                                                  
Leyendo la información de estado extendido                                                 
Inicializando el estado de los paquetes... Hecho                                           
Escribiendo información de estado extendido... Hecho                                       

Estado actual: 2 actualizados [-3].
```
apt-get install -f does nothing. Trying to remove the broken package via apt-get, aptitude, or dpkg fails to work. It seems the two broken packages are compiz and compiz-gnome.
Any ideas on how to fix this, please?

---

### Post by daggaz on 2010-02-23
Hola
¿Qué hay de este problema? ¿lo pudiste resolver?
Yo llevo dos días y nada... Además no hay suficiente información en internet, solo un poco y está en inglés...
Estoy a punto de solucionar estilo Güindous, es decir, formatear...

---

