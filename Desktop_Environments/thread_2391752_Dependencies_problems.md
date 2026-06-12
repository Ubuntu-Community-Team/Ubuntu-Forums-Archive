---
title: "Dependencies problems"
date: 2018-05-12
forum: Desktop Environments
---

### Post by josefranw on 2018-05-12
After updating Xubuntu to the newest version via console, there appeared the following errors with dependencies:


 keyboard-configuration
 xserver-xorg-core
 xserver-xorg-video-radeon
 xserver-xorg
 xserver-xorg-video-amdgpu
 xserver-xorg-input-wacom
 console-setup-linux
 xorg
 xserver-xorg-video-ati
 console-setup
 xserver-xorg-video-intel
 xubuntu-desktop
 xserver-xorg-input-libinput
 xserver-xorg-video-all
 kbd
 xubuntu-core
 ubuntu-minimal
 xserver-xorg-input-all

The system seems to work fine, up to now, but why does that message appear after any update now and to fix it?

---

### Post by PaulW2U on 2018-05-13
> **josefranw said:**
> The system seems to work fine, up to now, but why does that message appear after any update now and to fix it?
All you have given us is a list of packages that are referred to in the error message. But what was the error message? It would also be good to know which version of Xubuntu you are using.

In a terminal, please run ```
sudo apt-get update
``` and post the output wrapped in [NOPARSE][CODE][/NOPARSE] tags. How you fix the problem will depend on the error message.

---

### Post by josefranw on 2018-05-19
Thank you for the answer...
Here it is:

```
josefranw@josefranw-3000-N200:~$ sudo apt update[sudo] contraseña para josefranw: 
Obj:1 http://apt.insynchq.com/ubuntu bionic InRelease                          
Obj:2 http://ve.archive.ubuntu.com/ubuntu bionic InRelease                     
Obj:3 http://archive.canonical.com/ubuntu bionic InRelease                     
Obj:4 http://ve.archive.ubuntu.com/ubuntu bionic-updates InRelease             
Obj:5 http://archive.canonical.com bionic InRelease                            
Des:6 http://security.ubuntu.com/ubuntu bionic-security InRelease [83,2 kB]    
Obj:7 http://ve.archive.ubuntu.com/ubuntu bionic-backports InRelease           
Des:8 http://security.ubuntu.com/ubuntu bionic-security/main i386 DEP-11 Metadata [204 B]
Ign:9 https://mega.nz/linux/MEGAsync/xUbuntu_17.04 ./ InRelease                
Des:10 http://security.ubuntu.com/ubuntu bionic-security/universe i386 DEP-11 Metadata [2.456 B]
Des:11 https://mega.nz/linux/MEGAsync/xUbuntu_17.04 ./ Release [988 B]         
Descargados 86,9 kB en 22s (3.863 B/s)                                         
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Todos los paquetes están actualizados.
josefranw@josefranw-3000-N200:~$ sudo apt upgrade
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Calculando la actualización... Hecho
Los paquetes indicados a continuación se instalaron de forma automática y ya no son necesarios.
  libcapi20-3 libodbc1 libosmesa6 ocl-icd-libopencl1
Utilice «sudo apt autoremove» para eliminarlos.
0 actualizados, 0 nuevos se instalarán, 0 para eliminar y 0 no actualizados.
18 no instalados del todo o eliminados.
Se utilizarán 0 B de espacio de disco adicional después de esta operación.
¿Desea continuar? [S/n] s
Configurando keyboard-configuration (1.178ubuntu2) ...
/var/lib/dpkg/info/keyboard-configuration.config: 11: /etc/default/keyboard: Syntax error: Unterminated quoted string
dpkg: error al procesar el paquete keyboard-configuration (--configure):
 instalado keyboard-configuration paquete post-installation guión el subproceso devolvió un error con estado de salida 2
dpkg: problemas de dependencias impiden la configuración de xserver-xorg-core:
 xserver-xorg-core depende de keyboard-configuration; sin embargo:
 El paquete `keyboard-configuration' no está configurado todavía.


dpkg: error al procesar el paquete xserver-xorg-core (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de xserver-xorg-video-radeon:
 xserver-xorg-video-radeon depende de xorg-video-abi-23; sin embargo:
  El paquete `xorg-video-abi-23' no está instalado.
  El paquete `xserver-xorg-core' que provee `xorg-video-abi-23' aún no está configurado.
 xserver-xorg-video-radeon depende de xserver-xorg-core (>= 2:1.18.99.901); sin embargo:
 El paquete `xserver-xorg-core' no está configurado todavía.


dpkg: error al procesar el paquete xserver-xorg-video-radeon (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuNo se escribió un informe «apport» porque el mensaje de error indica que es un mensaje de error asociado a un fallo previo.
             No se escribió un informe «apport» porque el mensaje de error indica que es un mensaje de error asociado a un fallo previo.
                                                        No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
                                                                 No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
                                                                          No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
   No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
            No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
                     No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
                              No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
                                       No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
                                                No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
                                                         ración de xserver-xorg:
 xserver-xorg depende de xserver-xorg-core (>= 2:1.17.2-2); sin embargo:
 El paquete `xserver-xorg-core' no está configurado todavía.


dpkg: error al procesar el paquete xserver-xorg (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de xserver-xorg-video-amdgpu:
 xserver-xorg-video-amdgpu depende de xorg-video-abi-23; sin embargo:
  El paquete `xorg-video-abi-23' no está instalado.
  El paquete `xserver-xorg-core' que provee `xorg-video-abi-23' aún no está configurado.
 xserver-xorg-video-amdgpu depende de xserver-xorg-core (>= 2:1.18.99.901); sin embargo:
 El paquete `xserver-xorg-core' no está configurado todavía.


dpkg: error al procesar el paquete xserver-xorg-video-amdgpu (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de xserver-xorg-input-wacom:
 xserver-xorg-input-wacom depNo se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
                                      No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
                                               No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
                                                        No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
                                                                 No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
                                                                          No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
   ende de xorg-input-abi-24; sin embargo:
  El paquete `xorg-input-abi-24' no está instalado.
  El paquete `xserver-xorg-core' que provee `xorg-input-abi-24' aún no está configurado.
 xserver-xorg-input-wacom depende de xserver-xorg-core (>= 2:1.18.99.901); sin embargo:
 El paquete `xserver-xorg-core' no está configurado todavía.


dpkg: error al procesar el paquete xserver-xorg-input-wacom (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de console-setup-linux:
 console-setup-linux depende de keyboard-configuration (= 1.178ubuntu2); sin embargo:
 El paquete `keyboard-configuration' no está configurado todavía.


dpkg: error al procesar el paquete console-setup-linux (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de xorg:
 xorg depende de xserver-xorg (>= 1:7.7+19ubuntu7); sin embargo:
 El paquete `xserver-xorg' no está configurado todavía.


dpkg: error al procesar el paquete xorg (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de xserver-xorg-video-ati:
 xserver-xorg-video-ati depende de xorg-video-abi-23; sin embargo:
  El paquete `xorg-video-abi-23' no está instalado.
  El paquete `xserver-xorg-core' que provee `xorg-video-abi-23' aún no está configurado.
 xserver-xorg-video-ati depende de xserver-xorg-core (>= 2:1.18.99.901); sin embargo:
 El paquete `xserver-xorg-core' no está configurado todavía.
 xserver-xorg-video-ati depende de xserver-xorg-video-radeon; sin embargo:
 El paquete `xserver-xorg-video-radeon' no está configurado todavía.


dpkg: error al procesar el paquete xserver-xorg-video-ati (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de console-setup:
 console-setup depende de console-setup-linux | console-setup-freebsd | hurd; sin embargo:
 El paquete `console-setup-linux' no está configurado todavía.
  El paquete `console-setup-freebsd' no está instalado.
  El paquete `hurd' no está instalado.
 console-setup depende de keyboard-configuration (= 1.178ubuntu2); sin embargo:
 El paquete `keyboard-configuration' no está configurado todavía.


dpkg: error al procesar el paquete console-setup (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de xserver-xorg-video-intel:
 xserver-xorg-video-intel depende de xorg-video-abi-23; sin embargo:
  El paquete `xorg-video-abi-23' no está instalado.
  El paquete `xserver-xorg-core' que provee `xorg-video-abi-23' aún no está configurado.
 xserver-xorg-video-intel depende de xserver-xorg-core (>= 2:1.18.99.901); sin embargo:
 El paquete `xserver-xorg-core' no está configurado todavía.


dpkg: error al procesar el paquete xserver-xorg-video-intel (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de xubuntu-desktop:
 xubuntu-desktop depende de xorg; sin embargo:
 El paquete `xorg' no está configurado todavía.


dpkg: error al procesar el paquete xubuntu-desktop (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de xserver-xorg-input-libinput:
 xserver-xorg-input-libinput depende de xorg-input-abi-24; sin embargo:
  El paquete `xorg-input-abi-24' no está instalado.
  El paquete `xserver-xorg-core' que provee `xorg-input-abi-24' aún no está configurado.
 xserver-xorg-input-libinput depende de xserver-xorg-core (>= 2:1.18.99.901); sin embargo:
 El paquete `xserver-xorg-core' no está configurado todavía.


dpkg: error al procesar el paquete xserver-xorg-input-libinput (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de xserver-xorg-video-all:
 xserver-xorg-video-all depende de xserver-xorg-video-amdgpu; sin embargo:
 El paquete `xserver-xorg-video-amdgpu' no está configurado todavía.
 xserver-xorg-video-all depende de xserver-xorg-video-ati; sin embargo:
 El paquete `xserver-xorg-video-ati' no está configurado todavía.


dpkg: error al procesar el paquete xserver-xorg-video-all (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de kbd:
 kbd depende de console-setup | console-setup-mini; sin embargo:
 El paquete `console-setup' no está configurado todavía.
  El paquete `console-setup-mini' no está instalado.


dpkg: error al procesar el paquete kbd (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de xubuntu-core:
 xubuntu-core depende de xorg; sin embargo:
 El paquete `xorg' no está configurado todavía.


dpkg: error al procesar el paquete xubuntu-core (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de ubuntu-minimal:
 ubuntu-minimal depende de console-setup; sin embargo:
 El paquete `console-setup' no está configurado todavía.
 ubuntu-minimal depende de kbd; sin embargo:
 El paquete `kbd' no está configurado todavía.


dpkg: error al procesar el paquete ubuntu-minimal (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de xserver-xorg-input-all:
 xserver-xorg-input-all depende de xserver-xorg-input-libinput; sin embargo:
 El paquete `xserver-xorg-input-libinput' no está configurado todavía.


dpkg: error al procesar el paquete xserver-xorg-input-all (--configure):
 problemas de dependencias - se deja sin configurar
Se encontraron errores al procesar:
 keyboard-configuration
 xserver-xorg-core
 xserver-xorg-video-radeon
 xserver-xorg
 xserver-xorg-video-amdgpu
 xserver-xorg-input-wacom
 console-setup-linux
 xorg
 xserver-xorg-video-ati
 console-setup
 xserver-xorg-video-intel
 xubuntu-desktop
 xserver-xorg-input-libinput
 xserver-xorg-video-all
 kbd
 xubuntu-core
 ubuntu-minimal
 xserver-xorg-input-all
E: Sub-process /usr/bin/dpkg returned an error code (1)
josefranw@josefranw-3000-N200:~$
```

---

### Post by cruzer001 on 2018-05-20
Try this

```
sudo apt clean
sudo mv /var/lib/apt/lists /var/lib/apt/lists.old && sudo mkdir /var/lib/apt/lists
sudo apt update
```
No change?  Please post output of:
```
cat /etc/apt/sources.list && ls /etc/apt/sources.list.d/*.list
```

---

### Post by josefranw on 2018-05-31
```
josefranw@josefranw-3000-N200:~$ cat /etc/apt/sources.list && ls /etc/apt/sources.list.d/*.list# deb cdrom:[Xubuntu 17.10 _Artful Aardvark_ - Release i386 (20180105)]/ artful main multiverse restricted universe


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ve.archive.ubuntu.com/ubuntu/ bionic main restricted
# deb-src http://ve.archive.ubuntu.com/ubuntu/ artful main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://ve.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
# deb-src http://ve.archive.ubuntu.com/ubuntu/ artful-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ve.archive.ubuntu.com/ubuntu/ bionic universe
# deb-src http://ve.archive.ubuntu.com/ubuntu/ artful universe
deb http://ve.archive.ubuntu.com/ubuntu/ bionic-updates universe
# deb-src http://ve.archive.ubuntu.com/ubuntu/ artful-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ve.archive.ubuntu.com/ubuntu/ bionic multiverse
# deb-src http://ve.archive.ubuntu.com/ubuntu/ artful multiverse
deb http://ve.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
# deb-src http://ve.archive.ubuntu.com/ubuntu/ artful-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ve.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
# deb-src http://ve.archive.ubuntu.com/ubuntu/ artful-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu bionic partner
# deb-src http://archive.canonical.com/ubuntu artful partner


deb http://security.ubuntu.com/ubuntu bionic-security main restricted
# deb-src http://security.ubuntu.com/ubuntu artful-security main restricted
deb http://security.ubuntu.com/ubuntu bionic-security universe
# deb-src http://security.ubuntu.com/ubuntu artful-security universe
deb http://security.ubuntu.com/ubuntu bionic-security multiverse
deb http://archive.canonical.com/ bionic partner
# deb-src http://archive.canonical.com/ artful partner
# deb-src http://archive.canonical.com/ artful partner
# deb-src http://archive.canonical.com/ artful partner
# deb-src http://archive.canonical.com/ artful partner
# deb-src http://archive.canonical.com/ artful partner
# deb-src http://archive.canonical.com/ artful partner
# deb-src http://security.ubuntu.com/ubuntu artful-security multiverse
# deb http://archive.canonical.com/ precise partner
# deb-src http://archive.canonical.com/ precise partner
# deb-src http://archive.canonical.com/ artful partner
/etc/apt/sources.list.d/insync.list  /etc/apt/sources.list.d/megasync.list
josefranw@josefranw-3000-N200:~$ 



```

---

### Post by josefranw on 2018-06-04
Hello, excuse me. Can anyone help me figure this out? It continues to appear:

```
sudo apt update[sudo] contraseña para josefranw: 
Obj:1 http://archive.canonical.com/ubuntu bionic InRelease                     
Des:2 http://security.ubuntu.com/ubuntu bionic-security InRelease [83,2 kB]    
Obj:3 http://ve.archive.ubuntu.com/ubuntu bionic InRelease                     
Obj:4 http://apt.insynchq.com/ubuntu bionic InRelease                          
Des:5 http://ve.archive.ubuntu.com/ubuntu bionic-updates InRelease [83,2 kB]   
Obj:6 http://archive.canonical.com bionic InRelease                            
Des:7 http://ve.archive.ubuntu.com/ubuntu bionic-backports InRelease [74,6 kB] 
Des:8 http://ve.archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages [103 kB]
Des:9 http://security.ubuntu.com/ubuntu bionic-security/main i386 Packages [64,2 kB]
Ign:10 https://mega.nz/linux/MEGAsync/xUbuntu_17.04 ./ InRelease               
Des:11 http://ve.archive.ubuntu.com/ubuntu bionic-updates/main Translation-en [43,9 kB]
Des:12 http://security.ubuntu.com/ubuntu bionic-security/main Translation-en [27,1 kB]
Des:13 http://security.ubuntu.com/ubuntu bionic-security/main i386 DEP-11 Metadata [204 B]
Des:14 http://security.ubuntu.com/ubuntu bionic-security/universe i386 Packages [19,9 kB]
Des:15 http://security.ubuntu.com/ubuntu bionic-security/universe Translation-en [10,2 kB]
Des:16 http://security.ubuntu.com/ubuntu bionic-security/universe i386 DEP-11 Metadata [2.456 B]
Des:17 http://ve.archive.ubuntu.com/ubuntu bionic-updates/main i386 DEP-11 Metadata [70,6 kB]
Des:18 http://ve.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 48x48 Icons [15,8 kB]
Des:19 http://ve.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 64x64 Icons [28,2 kB]
Des:20 http://ve.archive.ubuntu.com/ubuntu bionic-updates/universe i386 Packages [68,3 kB]
Des:21 http://ve.archive.ubuntu.com/ubuntu bionic-updates/universe Translation-en [30,6 kB]
Des:22 http://ve.archive.ubuntu.com/ubuntu bionic-updates/universe i386 DEP-11 Metadata [117 kB]
Des:23 http://ve.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 48x48 Icons [118 kB]
Des:24 http://ve.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 64x64 Icons [190 kB]
Des:25 http://ve.archive.ubuntu.com/ubuntu bionic-backports/universe i386 DEP-11 Metadata [5.100 B]
Des:26 https://mega.nz/linux/MEGAsync/xUbuntu_17.04 ./ Release [961 B]         
Descargados 1.156 kB en 23s (50,9 kB/s)                                        
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Se pueden actualizar 14 paquetes. Ejecute «apt list --upgradable» para verlos.
josefranw@josefranw-3000-N200:~$ sudo apt upgrade
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Calculando la actualización... Hecho
El paquete indicado a continuación se instaló de forma automática y ya no es necesario.
  thermald
Utilice «sudo apt autoremove» para eliminarlo.
Se actualizarán los siguientes paquetes:
  liblouis-data liblouis14 libncurses5 libncursesw5 libpulse-mainloop-glib0
  libpulse0 libpulsedsp libtinfo5 ncurses-base ncurses-bin pulseaudio
  pulseaudio-module-bluetooth pulseaudio-utils snapd
14 actualizados, 0 nuevos se instalarán, 0 para eliminar y 0 no actualizados.
18 no instalados del todo o eliminados.
Se necesita descargar 12,2 MB de archivos.
Se utilizarán 10,2 kB de espacio de disco adicional después de esta operación.
¿Desea continuar? [S/n] s
Des:1 http://ve.archive.ubuntu.com/ubuntu bionic-updates/main i386 ncurses-bin i386 6.1-1ubuntu1.18.04 [165 kB]
Des:2 http://ve.archive.ubuntu.com/ubuntu bionic-updates/main i386 ncurses-base all 6.1-1ubuntu1.18.04 [17,8 kB]
Des:3 http://ve.archive.ubuntu.com/ubuntu bionic-updates/main i386 libncurses5 i386 6.1-1ubuntu1.18.04 [101 kB]
Des:4 http://ve.archive.ubuntu.com/ubuntu bionic-updates/main i386 libtinfo5 i386 6.1-1ubuntu1.18.04 [80,4 kB]
Des:5 http://ve.archive.ubuntu.com/ubuntu bionic-updates/main i386 libncursesw5 i386 6.1-1ubuntu1.18.04 [128 kB]
Des:6 http://ve.archive.ubuntu.com/ubuntu bionic-updates/main i386 liblouis-data all 3.5.0-1ubuntu0.1 [1.258 kB]
Des:7 http://ve.archive.ubuntu.com/ubuntu bionic-updates/main i386 liblouis14 i386 3.5.0-1ubuntu0.1 [71,5 kB]
Des:8 http://ve.archive.ubuntu.com/ubuntu bionic-updates/main i386 libpulsedsp i386 1:11.1-1ubuntu7.1 [33,4 kB]
Des:9 http://ve.archive.ubuntu.com/ubuntu bionic-updates/main i386 pulseaudio-utils i386 1:11.1-1ubuntu7.1 [63,8 kB]
Des:10 http://ve.archive.ubuntu.com/ubuntu bionic-updates/main i386 pulseaudio-module-bluetooth i386 1:11.1-1ubuntu7.1 [69,8 kB]
Des:11 http://ve.archive.ubuntu.com/ubuntu bionic-updates/main i386 pulseaudio i386 1:11.1-1ubuntu7.1 [782 kB]
Des:12 http://ve.archive.ubuntu.com/ubuntu bionic-updates/main i386 libpulse-mainloop-glib0 i386 1:11.1-1ubuntu7.1 [22,5 kB]
Des:13 http://ve.archive.ubuntu.com/ubuntu bionic-updates/main i386 libpulse0 i386 1:11.1-1ubuntu7.1 [270 kB]
Des:14 http://ve.archive.ubuntu.com/ubuntu bionic-updates/main i386 snapd i386 2.32.9+18.04 [9.178 kB]
Descargados 12,2 MB en 5min 32s (36,9 kB/s)                                    
(Leyendo la base de datos ... 201365 ficheros o directorios instalados actualmente.)
Preparando para desempaquetar .../ncurses-bin_6.1-1ubuntu1.18.04_i386.deb ...
Desempaquetando ncurses-bin (6.1-1ubuntu1.18.04) sobre (6.1-1ubuntu1) ...
Configurando ncurses-bin (6.1-1ubuntu1.18.04) ...
(Leyendo la base de datos ... 201365 ficheros o directorios instalados actualmente.)
Preparando para desempaquetar .../ncurses-base_6.1-1ubuntu1.18.04_all.deb ...
Desempaquetando ncurses-base (6.1-1ubuntu1.18.04) sobre (6.1-1ubuntu1) ...
Configurando ncurses-base (6.1-1ubuntu1.18.04) ...
(Leyendo la base de datos ... 201367 ficheros o directorios instalados actualmente.)
Preparando para desempaquetar .../libncurses5_6.1-1ubuntu1.18.04_i386.deb ...
Desempaquetando libncurses5:i386 (6.1-1ubuntu1.18.04) sobre (6.1-1ubuntu1) ...
Preparando para desempaquetar .../libtinfo5_6.1-1ubuntu1.18.04_i386.deb ...
Desempaquetando libtinfo5:i386 (6.1-1ubuntu1.18.04) sobre (6.1-1ubuntu1) ...
Configurando libtinfo5:i386 (6.1-1ubuntu1.18.04) ...
(Leyendo la base de datos ... 201367 ficheros o directorios instalados actualmente.)
Preparando para desempaquetar .../libncursesw5_6.1-1ubuntu1.18.04_i386.deb ...
Desempaquetando libncursesw5:i386 (6.1-1ubuntu1.18.04) sobre (6.1-1ubuntu1) ...
Configurando libncursesw5:i386 (6.1-1ubuntu1.18.04) ...
(Leyendo la base de datos ... 201367 ficheros o directorios instalados actualmente.)
Preparando para desempaquetar .../0-liblouis-data_3.5.0-1ubuntu0.1_all.deb ...
Desempaquetando liblouis-data (3.5.0-1ubuntu0.1) sobre (3.5.0-1) ...
Preparando para desempaquetar .../1-liblouis14_3.5.0-1ubuntu0.1_i386.deb ...
Desempaquetando liblouis14:i386 (3.5.0-1ubuntu0.1) sobre (3.5.0-1) ...
Preparando para desempaquetar .../2-libpulsedsp_1%3a11.1-1ubuntu7.1_i386.deb ...
Desempaquetando libpulsedsp:i386 (1:11.1-1ubuntu7.1) sobre (1:11.1-1ubuntu7) ...
Preparando para desempaquetar .../3-pulseaudio-utils_1%3a11.1-1ubuntu7.1_i386.deb ...
Desempaquetando pulseaudio-utils (1:11.1-1ubuntu7.1) sobre (1:11.1-1ubuntu7) ...
Preparando para desempaquetar .../4-pulseaudio-module-bluetooth_1%3a11.1-1ubuntu7.1_i386.deb ...
Desempaquetando pulseaudio-module-bluetooth (1:11.1-1ubuntu7.1) sobre (1:11.1-1ubuntu7) ...
Preparando para desempaquetar .../5-pulseaudio_1%3a11.1-1ubuntu7.1_i386.deb ...
Desempaquetando pulseaudio (1:11.1-1ubuntu7.1) sobre (1:11.1-1ubuntu7) ...
Preparando para desempaquetar .../6-libpulse-mainloop-glib0_1%3a11.1-1ubuntu7.1_i386.deb ...
Desempaquetando libpulse-mainloop-glib0:i386 (1:11.1-1ubuntu7.1) sobre (1:11.1-1ubuntu7) ...
Preparando para desempaquetar .../7-libpulse0_1%3a11.1-1ubuntu7.1_i386.deb ...
Desempaquetando libpulse0:i386 (1:11.1-1ubuntu7.1) sobre (1:11.1-1ubuntu7) ...
Preparando para desempaquetar .../8-snapd_2.32.9+18.04_i386.deb ...
Desempaquetando snapd (2.32.9+18.04) sobre (2.32.8+18.04) ...
Configurando libncurses5:i386 (6.1-1ubuntu1.18.04) ...
Configurando keyboard-configuration (1.178ubuntu2) ...
/var/lib/dpkg/info/keyboard-configuration.config: 11: /etc/default/keyboard: Syntax error: Unterminated quoted string
dpkg: error al procesar el paquete keyboard-configuration (--configure):
 instalado keyboard-configuration paquete post-installation guión el subproceso devolvió un error con estado de salida 2
dpkg: problemas de dependencias impiden la configuración de xserver-xorg-core:
 xserver-xorg-core depende de keyboard-configuration; sin embargo:
 El paquete `keyboard-configuration' no está configurado todavía.


dpkg: error al procesar el paquete xserver-xorg-core (--configure):
 problemas de dependencias - se deja sin configurar
Configurando libpulse0:i386 (1:11.1-1ubuntu7.1) ...
No se escribió un informe «apport» porque el mensaje de error indica que es un mensaje de error asociado a un fallo previo.
                                           dpkg: problemas de dependencias impiden la configuración de xserver-xorg-video-radeon:
 xserver-xorg-video-radeon depende de xorg-video-abi-23; sin embargo:
  El paquete `xorg-video-abi-23' no está instalado.
  El paquete `xserver-xorg-core' que provee `xorg-video-abi-23' aún no está configurado.
 xserver-xorg-video-radeon depende de xserver-xorg-core (>= 2:1.18.99.901); sin embargo:
 El paquete `xserver-xorg-core' no está configurado todavía.


dpkg: error al procesar el paquete xserver-xorg-video-radeon (--configure):
 problemas de dependencias - se deja sin configurar
No se escribió un informe «apport» porque el mensaje de error indica que es un mensaje de error asociado a un fallo previo.
                                           Configurando liblouis-data (3.5.0-1ubuntu0.1) ...
dpkg: problemas de dependencias impiden la configuración de xserver-xorg:
 xserver-xorg depende de xserver-xorg-core (>= 2:1.17.2-2); sin embargo:
 El paquete `xserver-xorg-core' no está configurado todavía.


dpkg: error al procesar el paquete xserver-xorg (--configure):
 problemas de dependencias - se deja sin configurar
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
         Configurando snapd (2.32.9+18.04) ...
snapd.snap-repair.service is a disabled or a static unit, not starting it.
Procesando disparadores para libc-bin (2.27-3ubuntu1) ...
dpkg: problemas de dependencias impiden la configuración de xserver-xorg-video-amdgpu:
 xserver-xorg-video-amdgpu depende de xorg-video-abi-23; sin embargo:
  El paquete `xorg-video-abi-23' no está instalado.
  El paquete `xserver-xorg-core' que provee `xorg-video-abi-23' aún no está configurado.
 xserver-xorg-video-amdgpu depende de xserver-xorg-core (>= 2:1.18.99.901); sin embargo:
 El paquete `xserver-xorg-core' no está configurado todavía.


dpkg: error al procesar el paquete xserver-xorg-video-amdgpu (--configure):
 problemas de dependencias - se deja sin configurar
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
         Configurando liblouis14:i386 (3.5.0-1ubuntu0.1) ...
Procesando disparadores para man-db (2.8.3-2) ...
Procesando disparadores para dbus (1.12.2-1ubuntu1) ...
dpkg: problemas de dependencias impiden la configuración de xserver-xorg-input-wacom:
 xserver-xorg-input-wacom depende de xorg-input-abi-24; sin embargo:
  El paquete `xorg-input-abi-24' no está instalado.
  El paquete `xserver-xorg-core' que provee `xorg-input-abi-24' aún no está configurado.
 xserver-xorg-input-wacom depende de xserver-xorg-core (>= 2:1.18.99.901); sin embargo:
 El paquete `xserver-xorg-core' no está configurado todavía.


dpkg: error al procesar el paquete xserver-xorg-input-wacom (--configure):
 problemas de dependencias - se deja sin configurar
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
         dpkg: problemas de dependencias impiden la configuración de console-setup-linux:
 console-setup-linux depende de keyboard-configuration (= 1.178ubuntu2); sin embargo:
 El paquete `keyboard-configuration' no está configurado todavía.


dpkg: error al procesar el paquete console-setup-linux (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de xorg:
 xorg depende de xserver-xorg (>= 1:7.7+19ubuntu7); sin embargo:
 El paquete `xserver-xorg' no está configurado todavía.


dpkg: error al procesar el paquete xorg (--configure):
 problemas de dependencias - se deja sin configurar
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
         No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
                  dpkg: problemas de dependencias impiden la configuración de xserver-xorg-video-ati:
 xserver-xorg-video-ati depende de xorg-video-abi-23; sin embargo:
  El paquete `xorg-video-abi-23' no está instalado.
  El paquete `xserver-xorg-core' que provee `xorg-video-abi-23' aún no está configurado.
 xserver-xorg-video-ati depende de xserver-xorg-core (>= 2:1.18.99.901); sin embargo:
 El paquete `xserver-xorg-core' no está configurado todavía.
 xserver-xorg-video-ati depende de xserver-xorg-video-radeon; sin embargo:
 El paquete `xserver-xorg-video-radeon' no está configurado todavía.


dpkg: error al procesar el paquete xserver-xorg-video-ati (--configure):
 problemas de dependencias - se deja sin configurar
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
         dpkg: problemas de dependencias impiden la configuración de console-setup:
 console-setup depende de console-setup-linux | console-setup-freebsd | hurd; sin embargo:
 El paquete `console-setup-linux' no está configurado todavía.
  El paquete `console-setup-freebsd' no está instalado.
  El paquete `hurd' no está instalado.
 console-setup depende de keyboard-configuration (= 1.178ubuntu2); sin embargo:
 El paquete `keyboard-configuration' no está configurado todavía.


dpkg: error al procesar el paquete console-setup (--configure):
 problemas de dependencias - se deja sin configurar
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
         dpkg: problemas de dependencias impiden la configuración de xserver-xorg-video-intel:
 xserver-xorg-video-intel depende de xorg-video-abi-23; sin embargo:
  El paquete `xorg-video-abi-23' no está instalado.
  El paquete `xserver-xorg-core' que provee `xorg-video-abi-23' aún no está configurado.
 xserver-xorg-video-intel depende de xserver-xorg-core (>= 2:1.18.99.901); sin embargo:
 El paquete `xserver-xorg-core' no está configurado todavía.


dpkg: error al procesar el paquete xserver-xorg-video-intel (--configure):
 problemas de dependencias - se deja sin configurar
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
         dpkg: problemas de dependencias impiden la configuración de xubuntu-desktop:
 xubuntu-desktop depende de xorg; sin embargo:
 El paquete `xorg' no está configurado todavía.


dpkg: error al procesar el paquete xubuntu-desktop (--configure):
 problemas de dependencias - se deja sin configurar
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
         Configurando libpulse-mainloop-glib0:i386 (1:11.1-1ubuntu7.1) ...
Configurando libpulsedsp:i386 (1:11.1-1ubuntu7.1) ...
Configurando pulseaudio-utils (1:11.1-1ubuntu7.1) ...
dpkg: problemas de dependencias impiden la configuración de xserver-xorg-input-libinput:
 xserver-xorg-input-libinput depende de xorg-input-abi-24; sin embargo:
  El paquete `xorg-input-abi-24' no está instalado.
  El paquete `xserver-xorg-core' que provee `xorg-input-abi-24' aún no está configurado.
 xserver-xorg-input-libinput depende de xserver-xorg-core (>= 2:1.18.99.901); sin embargo:
 El paquete `xserver-xorg-core' no está configurado todavía.


dpkg: error al procesar el paquete xserver-xorg-input-libinput (--configure):
 problemas de dependencias - se deja sin configurar
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
         No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
                  dpkg: problemas de dependencias impiden la configuración de xserver-xorg-video-all:
 xserver-xorg-video-all depende de xserver-xorg-video-amdgpu; sin embargo:
 El paquete `xserver-xorg-video-amdgpu' no está configurado todavía.
 xserver-xorg-video-all depende de xserver-xorg-video-ati; sin embargo:
 El paquete `xserver-xorg-video-ati' no está configurado todavía.


dpkg: error al procesar el paquete xserver-xorg-video-all (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de kbd:
 kbd depende de console-setup | console-setup-mini; sin embargo:
 El paquete `console-setup' no está configurado todavía.
  El paquete `console-setup-mini' no está instalado.


dpkg: error al procesar el paquete kbd (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de xubuntu-core:
 xubuntu-core depende de xorg; sin embargo:
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
         No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
                   El paquete `xorg' no está configurado todavía.


dpkg: error al procesar el paquete xubuntu-core (--configure):
 problemas de dependencias - se deja sin configurar
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
         dpkg: problemas de dependencias impiden la configuración de ubuntu-minimal:
 ubuntu-minimal depende de console-setup; sin embargo:
 El paquete `console-setup' no está configurado todavía.
 ubuntu-minimal depende de kbd; sin embargo:
 El paquete `kbd' no está configurado todavía.


dpkg: error al procesar el paquete ubuntu-minimal (--configure):
 problemas de dependencias - se deja sin configurar
Configurando pulseaudio (1:11.1-1ubuntu7.1) ...
dpkg: problemas de dependencias impiden la configuración de xserver-xorg-input-all:
 xserver-xorg-input-all depende de xserver-xorg-input-libinput; sin embargo:
 El paquete `xserver-xorg-input-libinput' no está configurado todavía.


dpkg: error al procesar el paquete xserver-xorg-input-all (--configure):
 problemas de dependencias - se deja sin configurar
Configurando pulseaudio-module-bluetooth (1:11.1-1ubuntu7.1) ...
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
         Procesando disparadores para libc-bin (2.27-3ubuntu1) ...
Se encontraron errores al procesar:
 keyboard-configuration
 xserver-xorg-core
 xserver-xorg-video-radeon
 xserver-xorg
 xserver-xorg-video-amdgpu
 xserver-xorg-input-wacom
 console-setup-linux
 xorg
 xserver-xorg-video-ati
 console-setup
 xserver-xorg-video-intel
 xubuntu-desktop
 xserver-xorg-input-libinput
 xserver-xorg-video-all
 kbd
 xubuntu-core
 ubuntu-minimal
 xserver-xorg-input-all
E: Sub-process /usr/bin/dpkg returned an error code (1)
josefranw@josefranw-3000-N200:~$ 



```

---

### Post by cruzer001 on 2018-06-06
Hello

> dpkg: error al procesar el paquete xserver-xorg-input-all (--configure)
Try the configure/repair command.
```
sudo dpkg --configure -a && sudo apt -f install
```
Please post any errors.

Your PPAs (insync/megasync) seem harmless, but to be sure temporary disable them by unchecking both in the "OtherSoftware" tab and try an update.  To enable just go back and recheck both.  Its in your menu or pull it up using the terminal.
```
software-properties-gtk
```

You can also try reinstalling xorg.  Do this in console (tty) mode by pressing...
Ctrl + Alt + F1

then sign in and enter
```
sudo apt install --reinstall xserver-xorg-core
```
To return to the desktop press
Ctrl + Alt + F7

I hope we hit on something

---

### Post by Yellow Pasque on 2018-06-07
This is the problem:
```
/var/lib/dpkg/info/keyboard-configuration.config: 11: /etc/default/keyboard: Syntax error: Unterminated quoted string
```

You can either edit /etc/default/keyboard file manually or move it out of the way and generate a fresh one:
```
sudo mv /etc/default/keyboard /etc/default/keyboard.bak
sudo dpkg-reconfigure keyboard-configuration
```

Once you do that, you should be able to proceed as normal. If you wish, you can delete the backup copy:
```
sudo rm /etc/default/keyboard.bak
```

---

### Post by josefranw on 2018-06-15
> **Temüjin said:**
> This is the problem:
```
/var/lib/dpkg/info/keyboard-configuration.config: 11: /etc/default/keyboard: Syntax error: Unterminated quoted string
```

You can either edit /etc/default/keyboard file manually or move it out of the way and generate a fresh one:
```
sudo mv /etc/default/keyboard /etc/default/keyboard.bak
sudo dpkg-reconfigure keyboard-configuration
```

Once you do that, you should be able to proceed as normal. If you wish, you can delete the backup copy:
```
sudo rm /etc/default/keyboard.bak
```


Thank you, I fixed it.

```
josefranw@josefranw-3000-N200:~$ sudo mv /etc/default/keyboard /etc/default/keyboard.bak[sudo] contraseña para josefranw: 
josefranw@josefranw-3000-N200:~$ sudo dpkg-reconfigure keyboard-configuration
/usr/sbin/dpkg-reconfigure: keyboard-configuration está roto o no está totalmente instalado
josefranw@josefranw-3000-N200:~$ sudo apt install keyboard-configuration
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
keyboard-configuration ya está en su versión más reciente (1.178ubuntu2).
El paquete indicado a continuación se instaló de forma automática y ya no es necesario.
  thermald
Utilice «sudo apt autoremove» para eliminarlo.
0 actualizados, 0 nuevos se instalarán, 0 para eliminar y 0 no actualizados.
18 no instalados del todo o eliminados.
Se utilizarán 0 B de espacio de disco adicional después de esta operación.
¿Desea continuar? [S/n] s
Configurando keyboard-configuration (1.178ubuntu2) ...
Your console font configuration will be updated the next time your system
boots. If you want to update it now, run 'setupcon' from a virtual console.
update-initramfs: deferring update (trigger activated)
Configurando xserver-xorg-core (2:1.19.6-1ubuntu4) ...
Configurando xserver-xorg-video-radeon (1:18.0.1-1) ...
Configurando xserver-xorg (1:7.7+19ubuntu7) ...
Configurando xserver-xorg-video-amdgpu (18.0.1-1) ...
Configurando xserver-xorg-input-wacom (1:0.36.1-0ubuntu1) ...
Configurando xorg (1:7.7+19ubuntu7) ...
Configurando xserver-xorg-video-ati (1:18.0.1-1) ...
Configurando xserver-xorg-video-intel (2:2.99.917+git20171229-1) ...
Configurando xserver-xorg-input-libinput (0.27.1-1) ...
Configurando xserver-xorg-video-all (1:7.7+19ubuntu7) ...
Configurando xubuntu-core (2.225) ...
Configurando xubuntu-desktop (2.225) ...
Configurando xserver-xorg-input-all (1:7.7+19ubuntu7) ...
Configurando console-setup (1.178ubuntu2) ...
update-initramfs: deferring update (trigger activated)
Configurando kbd (2.0.4-2ubuntu1) ...
Configurando ubuntu-minimal (1.417) ...
Configurando console-setup-linux (1.178ubuntu2) ...
Procesando disparadores para initramfs-tools (0.130ubuntu3) ...
update-initramfs: Generating /boot/initrd.img-4.15.0-22-generic
Procesando disparadores para libc-bin (2.27-3ubuntu1) ...
W: APT had planned for dpkg to do more than it reported back (51 vs 55).
   Affected packages: keyboard-configuration:i386
josefranw@josefranw-3000-N200:~$ sudo apt update
Des:1 http://security.ubuntu.com/ubuntu bionic-security InRelease [83,2 kB]    
Obj:2 http://archive.canonical.com/ubuntu bionic InRelease                     
Obj:3 http://ve.archive.ubuntu.com/ubuntu bionic InRelease                     
Obj:4 http://archive.canonical.com bionic InRelease                            
Des:5 http://ve.archive.ubuntu.com/ubuntu bionic-updates InRelease [83,2 kB]   
Obj:6 http://apt.insynchq.com/ubuntu bionic InRelease                          
Des:7 http://security.ubuntu.com/ubuntu bionic-security/main i386 DEP-11 Metadata [204 B]
Des:8 http://ve.archive.ubuntu.com/ubuntu bionic-backports InRelease [74,6 kB] 
Des:9 http://security.ubuntu.com/ubuntu bionic-security/universe i386 DEP-11 Metadata [2.456 B]
Des:10 http://ve.archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages [129 kB]
Des:11 http://ve.archive.ubuntu.com/ubuntu bionic-updates/main Translation-en [56,0 kB]
Des:12 http://ve.archive.ubuntu.com/ubuntu bionic-updates/main i386 DEP-11 Metadata [105 kB]
Des:13 http://ve.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 48x48 Icons [18,0 kB]
Ign:14 https://mega.nz/linux/MEGAsync/xUbuntu_17.04 ./ InRelease               
Des:15 http://ve.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 64x64 Icons [34,3 kB]
Des:16 http://ve.archive.ubuntu.com/ubuntu bionic-updates/universe i386 Packages [84,4 kB]
Des:17 http://ve.archive.ubuntu.com/ubuntu bionic-updates/universe i386 DEP-11 Metadata [120 kB]
Des:18 http://ve.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 48x48 Icons [120 kB]
Des:19 https://mega.nz/linux/MEGAsync/xUbuntu_17.04 ./ Release [961 B]         
Des:21 http://ve.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 64x64 Icons [190 kB]
Des:22 http://ve.archive.ubuntu.com/ubuntu bionic-backports/universe i386 DEP-11 Metadata [5.100 B]
Descargados 1.106 kB en 9s (125 kB/s)                                          
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Se puede actualizar 1 paquete. Ejecute «apt list --upgradable» para verlo.
josefranw@josefranw-3000-N200:~$ sudo apt upgrade
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Calculando la actualización... Hecho
El paquete indicado a continuación se instaló de forma automática y ya no es necesario.
  thermald
Utilice «sudo apt autoremove» para eliminarlo.
Se actualizarán los siguientes paquetes:
  cups-pk-helper
1 actualizados, 0 nuevos se instalarán, 0 para eliminar y 0 no actualizados.
Se necesita descargar 52,8 kB de archivos.
Se utilizarán 12,3 kB de espacio de disco adicional después de esta operación.
¿Desea continuar? [S/n] s
Des:1 http://ve.archive.ubuntu.com/ubuntu bionic-updates/main i386 cups-pk-helper i386 0.2.6-1ubuntu1.2 [52,8 kB]
Descargados 52,8 kB en 4s (13,3 kB/s)     
(Leyendo la base de datos ... 202006 ficheros o directorios instalados actualmente.)
Preparando para desempaquetar .../cups-pk-helper_0.2.6-1ubuntu1.2_i386.deb ...
Desempaquetando cups-pk-helper (0.2.6-1ubuntu1.2) sobre (0.2.6-1ubuntu1) ...
Configurando cups-pk-helper (0.2.6-1ubuntu1.2) ...
Instalando una nueva versión del fichero de configuración /etc/dbus-1/system.d/org.opensuse.CupsPkHelper.Mechanism.conf ...
Procesando disparadores para dbus (1.12.2-1ubuntu1) ...
josefranw@josefranw-3000-N200:~$ sudo apt autoremove
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Los siguientes paquetes se ELIMINARÁN:
  thermald
0 actualizados, 0 nuevos se instalarán, 1 para eliminar y 0 no actualizados.
Se liberarán 616 kB después de esta operación.
¿Desea continuar? [S/n] s
(Leyendo la base de datos ... 202005 ficheros o directorios instalados actualmente.)
Desinstalando thermald (1.7.0-5ubuntu1) ...
Procesando disparadores para man-db (2.8.3-2) ...
Procesando disparadores para dbus (1.12.2-1ubuntu1) ...
josefranw@josefranw-3000-N200:~$ sudo rm /etc/default/keyboard.bak
josefranw@josefranw-3000-N200:~$ sudo apt update
Obj:1 http://ve.archive.ubuntu.com/ubuntu bionic InRelease                     
Obj:2 http://ve.archive.ubuntu.com/ubuntu bionic-updates InRelease             
Obj:3 http://archive.canonical.com/ubuntu bionic InRelease                     
Obj:4 http://security.ubuntu.com/ubuntu bionic-security InRelease              
Obj:5 http://ve.archive.ubuntu.com/ubuntu bionic-backports InRelease           
Obj:6 http://apt.insynchq.com/ubuntu bionic InRelease                          
Obj:7 http://archive.canonical.com bionic InRelease                            
Ign:8 https://mega.nz/linux/MEGAsync/xUbuntu_17.04 ./ InRelease                
Des:9 https://mega.nz/linux/MEGAsync/xUbuntu_17.04 ./ Release [961 B]
Descargados 961 B en 7s (129 B/s)
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Todos los paquetes están actualizados.
josefranw@josefranw-3000-N200:~$ sudo apt upgrade
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Calculando la actualización... Hecho
0 actualizados, 0 nuevos se instalarán, 0 para eliminar y 0 no actualizados.
josefranw@josefranw-3000-N200:~$ 



```

---

### Post by Yellow Pasque on 2018-06-15
:guitar:

---

