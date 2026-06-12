---
title: "E: No pude sincronizar «mmap» - msync (5: Error de entrada/salida)"
date: 2016-05-19
forum: Chile Team
---

### Post by alexei-robles on 2016-05-19
Hola
Soy nuevo en esto así que no tengo mucha de nada ^^'
El problema es el siguiente, tengo un live USB con volumen persistente de Ubuntu 14.04.4 LTS (el disco duro del note esta muerto y mientras no tenga dinero para uno nuevo tendre que usar ubuntu desde el pendrive), esta version me ha funcionado relativamente bien hasta ahora (se pega un poco a veces, pero eso es por los cambios que se guardan en el volumen persistente por la velocidad de escritura de los usb), pero hoy, luego de reiniciar el sistema firefox no queria abrir, lo intente solo desde el lanzador y no abre, las demas aplicaciones que tengo ahi abren sin problema. intente usando clean y update, pero solo da error, lo mismo al desinstalar desde el centro de software o de actualizar firefox solo en vez de todo el sistema, sigue saliendo lo mismo:
```
ubuntu@ubuntu:~$ sudo apt-get cleanubuntu@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty InRelease
Ign cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main Translation-es_ES
Ign cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main Translation-es
Ign cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main Translation-en_US
Ign cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/main Translation-en
Ign cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted Translation-es_ES
Ign cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted Translation-es
Ign cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted Translation-en_US
Ign cdrom://Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1) trusty/restricted Translation-en
Obj http://repo.steampowered.com precise InRelease                             
Ign http://archive.ubuntu.com trusty InRelease                                 
Obj http://security.ubuntu.com trusty-security InRelease                       
Obj http://ppa.launchpad.net trusty InRelease                                  
Obj http://archive.ubuntu.com trusty-updates InRelease                         
Obj http://security.ubuntu.com trusty-security/main amd64 Packages             
Obj http://repo.steampowered.com precise/steam Sources                         
Obj http://archive.ubuntu.com trusty Release.gpg                               
Obj http://security.ubuntu.com trusty-security/restricted amd64 Packages       
Ign http://ppa.launchpad.net trusty InRelease                                  
Obj http://archive.ubuntu.com trusty-updates/main amd64 Packages               
Obj http://security.ubuntu.com trusty-security/multiverse amd64 Packages       
Obj http://ppa.launchpad.net trusty InRelease                                  
Obj http://archive.ubuntu.com trusty-updates/restricted amd64 Packages         
Obj http://security.ubuntu.com trusty-security/universe amd64 Packages         
Obj http://repo.steampowered.com precise/steam amd64 Packages                  
Obj http://archive.ubuntu.com trusty-updates/multiverse amd64 Packages         
Obj http://security.ubuntu.com trusty-security/main Translation-en             
Obj http://ppa.launchpad.net trusty/main amd64 Packages                        
Obj http://archive.ubuntu.com trusty-updates/universe amd64 Packages           
Obj http://security.ubuntu.com trusty-security/multiverse Translation-en       
Obj http://repo.steampowered.com precise/steam i386 Packages                   
Obj http://ppa.launchpad.net trusty/main Translation-en                        
Obj http://archive.ubuntu.com trusty-updates/main Translation-en               
Ign https://private-ppa.launchpad.net trusty InRelease                         
Obj http://security.ubuntu.com trusty-security/restricted Translation-en       
Obj http://archive.ubuntu.com trusty-updates/multiverse Translation-en         
Obj http://security.ubuntu.com trusty-security/universe Translation-en         
Obj http://ppa.launchpad.net trusty Release.gpg                                
Obj http://archive.ubuntu.com trusty-updates/restricted Translation-en         
Obj http://ppa.launchpad.net trusty/main amd64 Packages                        
Obj http://archive.ubuntu.com trusty-updates/universe Translation-en           
Ign https://private-ppa.launchpad.net trusty InRelease                         
Obj http://archive.ubuntu.com trusty Release                                   
Obj http://ppa.launchpad.net trusty/main Translation-en                        
Obj https://private-ppa.launchpad.net trusty Release.gpg                       
Obj http://archive.ubuntu.com trusty/main amd64 Packages                       
Obj http://ppa.launchpad.net trusty Release                                    
Obj http://archive.ubuntu.com trusty/restricted amd64 Packages                 
Obj http://archive.ubuntu.com trusty/multiverse amd64 Packages                 
Obj http://ppa.launchpad.net trusty/main amd64 Packages                        
Obj https://private-ppa.launchpad.net trusty Release.gpg                       
Obj http://archive.ubuntu.com trusty/universe amd64 Packages                   
Obj https://private-ppa.launchpad.net trusty Release                           
Obj http://ppa.launchpad.net trusty/main Translation-en                        
Obj http://archive.ubuntu.com trusty/main Translation-es                       
Obj https://private-ppa.launchpad.net trusty Release                       
Obj https://private-ppa.launchpad.net trusty/main amd64 Packages               
Obj http://archive.ubuntu.com trusty/main Translation-en                   
Obj http://archive.ubuntu.com trusty/multiverse Translation-es                 
Obj http://archive.ubuntu.com trusty/multiverse Translation-en                 
Obj http://archive.ubuntu.com trusty/restricted Translation-es                 
Obj https://private-ppa.launchpad.net trusty/main amd64 Packages               
Obj http://archive.ubuntu.com trusty/restricted Translation-en           
Obj http://archive.ubuntu.com trusty/universe Translation-es                   
Obj http://archive.ubuntu.com trusty/universe Translation-en                   
Ign http://repo.steampowered.com precise/steam Translation-es_ES               
Ign http://repo.steampowered.com precise/steam Translation-es                  
Ign http://repo.steampowered.com precise/steam Translation-en_US               
Ign http://archive.ubuntu.com trusty/main Translation-es_ES                    
Ign http://repo.steampowered.com precise/steam Translation-en                  
Ign http://archive.ubuntu.com trusty/main Translation-en_US                    
Ign http://archive.ubuntu.com trusty/multiverse Translation-es_ES              
Ign http://archive.ubuntu.com trusty/multiverse Translation-en_US              
Ign http://archive.ubuntu.com trusty/restricted Translation-es_ES              
Ign http://archive.ubuntu.com trusty/restricted Translation-en_US              
Ign http://archive.ubuntu.com trusty/universe Translation-es_ES                
Ign http://archive.ubuntu.com trusty/universe Translation-en_US                
Ign https://private-ppa.launchpad.net trusty/main Translation-es_ES            
Ign https://private-ppa.launchpad.net trusty/main Translation-es               
Ign https://private-ppa.launchpad.net trusty/main Translation-en_US            
Ign https://private-ppa.launchpad.net trusty/main Translation-en               
Ign https://private-ppa.launchpad.net trusty/main Translation-es_ES            
Ign https://private-ppa.launchpad.net trusty/main Translation-es               
Ign https://private-ppa.launchpad.net trusty/main Translation-en_US            
Ign https://private-ppa.launchpad.net trusty/main Translation-en               
Leyendo lista de paquetes... ¡Error!                                           
E: No pude sincronizar «mmap» - msync (5: Error de entrada/salida)
E: No se pudieron analizar o abrir las listas de paquetes o el archivo de estado.
```

Alguna idea de qué podría ser? o Cómo solucionarlo?

Desde ya gracias

---

