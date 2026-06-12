---
title: "Configurando mi primer server ubuntu"
date: 2011-08-07
forum: Colombia Team - Colombia
---

### Post by plooxy on 2011-08-07
Un saludo foreros , necesito ayuda para montar un servidor casero , ya tiene intalado ubuntu server 11.04 soy un poco nuevo en linux pero aprendo rapido :) quiero el server para FTP,Maquinas Virtuales, VPN24/7 y firewall

**Maquina:**
Intel Dualcore 2.0
3 Gb ram
500gb
2 tarjetas de red

**Algunos de los programas con los que me e encontrado que me pueden servir son :**

Firestarter
Bind9
dnsmasq
proftp
virtualbox


**Esquema de la conexion :**

ADSL Router del ISP -> Swith/hub -> Servidor Ubuntu -> Router Wifi -> PC1,PC2...


por donde empezar ?

---

### Post by ubudog on 2011-09-12
(lo siento por mi Espanol :P)

Yo recomiendo no usar Firestarter.  Usa iptables.
Eso viene con Ubuntu, y esta activa.

Bueno, aqui estan unas enlaces para configurar las cosas que mencionaste.  Espero que esto te ayuda.

[Bind9 (traducido)]("http://translate.google.com/translate?sl=en&tl=es&js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&u=http%3A%2F%2Fwww.ubuntugeek.com%2Fdns-server-setup-using-bind-in-ubuntu.html&act=url")

[dnsmasq (traducido)]("http://translate.google.com/translate?sl=en&tl=es&js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&u=http%3A%2F%2Fembraceubuntu.com%2F2006%2F08%2F02%2Flocal-dns-cache-for-faster-browsing%2F&act=url")

[proftp (traducido)]("http://translate.google.com/translate?sl=en&tl=es&js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&u=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D79588&act=url")

Yo recomiendo [KVM]("http://translate.google.com/translate?sl=en&tl=es&js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&u=http%3A%2F%2Fblog.codefront.net%2F2010%2F02%2F01%2Fsetting-up-virtualization-on-ubuntu-with-kvm%2F&act=url") para el Virtualization.  

Espero que esto ayude! 

Saludos,
ubudog

---

### Post by MasterTato on 2011-11-23
Lo pudiste Configurar, cuenta que hiciste para q otros q no lo han logrado se guien por lo que hiciste....

---

