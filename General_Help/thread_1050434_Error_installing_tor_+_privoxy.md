---
title: "Error installing tor + privoxy"
date: 2009-01-25
forum: General Help
---

### Post by ztrange on 2009-01-25
Yesterday I installed tor + privoxy but it didn't work, so I uninstalled it or so I thaught...

Now, I discovered about some configurations I must have done for them to work but when I try to reinstall I get the following output:

```
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido       
Inicializando el estado de los paquetes... Hecho
Se configurarán los siguientes paquetes que están ahora parcialmente instalados:
  tor tor-geoipdb 
0 paquetes actualizados, 0 nuevos instalados, 0 para eliminar y 0 sin actualizar.
Necesito descargar 0B de ficheros. Después de desempaquetar se usarán 0B.
Escribiendo información de estado extendido... Hecho
Configurando tor (0.2.0.31-1) ...
Raising maximum number of filedescriptors (ulimit -n) to 32768.
Starting tor daemon: tor...
Jan 25 15:36:01.921 [notice] Tor v0.2.0.31 (r16744). This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Jan 25 15:36:01.923 [notice] Initialized libevent version 1.3e using method epoll. Good.
Jan 25 15:36:01.923 [notice] Opening Socks listener on 127.0.0.1:9050
Jan 25 15:36:01.923 [warn] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Jan 25 15:36:01.923 [warn] Failed to parse/validate config: Failed to bind one of the listener ports.
Jan 25 15:36:01.923 [err] Reading config failed--see warnings above.
invoke-rc.d: initscript tor, action "start" failed.
dpkg: error al procesar tor (--configure):
 el subproceso post-installation script devolvió el código de salida de error 1
dpkg: problemas de dependencias impiden la configuración de tor-geoipdb:
 tor-geoipdb depende de tor (>= 0.2.0.31-1); sin embargo:
 El paquete `tor' no está configurado todavía.
dpkg: error al procesar tor-geoipdb (--configure):
 problemas de dependencias - se deja sin configurar
No se ha escrito ningún informe de Apport porque el mensaje de error indica que es un error proveniente de un fallo anterior.
               Se encontraron errores al procesar:
 tor
 tor-geoipdb
E: Sub-process /usr/bin/dpkg returned an error code (1)
Un paquete no se pudo instalar. Intentado recuperarse:
Configurando tor (0.2.0.31-1) ...
Raising maximum number of filedescriptors (ulimit -n) to 32768.
Starting tor daemon: tor...
Jan 25 15:36:03.119 [notice] Tor v0.2.0.31 (r16744). This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Jan 25 15:36:03.128 [notice] Initialized libevent version 1.3e using method epoll. Good.
Jan 25 15:36:03.129 [notice] Opening Socks listener on 127.0.0.1:9050
Jan 25 15:36:03.129 [warn] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Jan 25 15:36:03.129 [warn] Failed to parse/validate config: Failed to bind one of the listener ports.
Jan 25 15:36:03.129 [err] Reading config failed--see warnings above.
invoke-rc.d: initscript tor, action "start" failed.
dpkg: error al procesar tor (--configure):
 el subproceso post-installation script devolvió el código de salida de error 1
dpkg: problemas de dependencias impiden la configuración de tor-geoipdb:
 tor-geoipdb depende de tor (>= 0.2.0.31-1); sin embargo:
 El paquete `tor' no está configurado todavía.
dpkg: error al procesar tor-geoipdb (--configure):
 problemas de dependencias - se deja sin configurar
Se encontraron errores al procesar:
 tor
 tor-geoipdb
Leyendo lista de paquetes... Hecho                   
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho

```

Im sorry it is not in english but I dont know how could I show it to you in english...

Well, any help will be appreciated in order to remove the "old" tor installation and make a brand new one.
Edit: If I use remove and then install, I get similar output.

---

### Post by ztrange on 2009-01-26
bump...

---

### Post by ztrange on 2009-02-08
Anyone...??

---

