---
title: "Conexón internet movil UNE modem 4g lte"
date: 2013-03-12
forum: Colombia Team - Colombia
---

### Post by dedalusjoyce on 2013-03-12
Queridos amigos

estoy intentando poner a funcionar el modem 4G lte de internet movil de UNE en el Pc de un amigo, he tratado de configurarlo por el asistente poniendo el país (Colombia), el proveedor (UNE), APN ([www.une.net.co](www.une.net.co)), [FONT=Helvetica]Numero *99#, [/FONT][FONT=Helvetica]Nombre de usuario: une, [/FONT][FONT=Helvetica]Contraseña: une, [/FONT][FONT=Helvetica]nombre de AP: [www.une.net.co](www.une.net.co) . poniendo en [/FONT][FONT=Helvetica]Ajustes de PPP solo el CHAP, pero [/FONT]hasta el momento no lo he logrado, ¿pueden ayudarme?.

cuando le doy lsusb, ifconfig e iwconfig me sale lo siguiente:
$ lsusb 
Bus 005 Device 001: ID 1d6b:0001 LinuxFoundation 1.1 root hub 
Bus 004 Device 008: ID 19d2:0166 ONDACommunication S.p.A. 
Bus 004 Device 001: ID 1d6b:0001 LinuxFoundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 LinuxFoundation 1.1 root hub 
Bus 002 Device 002: ID 093a:2510 PixartImaging, Inc. Hama Optical Mouse 
Bus 002 Device 001: ID 1d6b:0001 LinuxFoundation 1.1 root hub 
Bus 001 Device 004: ID 0951:1603Kingston Technology DataTraveler 1GB/2GB Pen Drive 
Bus 001 Device 001: ID 1d6b:0002 LinuxFoundation 2.0 root hub  

$ ifconfig 
eth0      Link encap:Ethernet direcciónHW 00:11:11:6b:36:b7  
          ACTIVO DIFUSIÓN MULTICAST MTU:1500  Métrica:1 
          Paquetes RX:0 errores:0perdidos:0 overruns:0 frame:0 
          Paquetes TX:0 errores:0perdidos:0 overruns:0 carrier:0 
          colisiones:0 long.colaTX:1000
          Bytes RX:0 (0.0 B)  TXbytes:0 (0.0 B) 


lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1 Másc:255.0.0.0 
          Dirección inet6: ::1/128Alcance:Anfitrión 
          ACTIVO BUCLE FUNCIONANDO MTU:16436  Métrica:1 
          Paquetes RX:16 errores:0perdidos:0 overruns:0 frame:0 
          Paquetes TX:16 errores:0perdidos:0 overruns:0 carrier:0 
          colisiones:0 long.colaTX:0 
          Bytes RX:960 (960.0 B)  TXbytes:960 (960.0 B) 


~$ iwconfig 
lo        no wireless extensions. 
eth0      no wireless extension

---

### Post by dedalusjoyce on 2013-03-17
[COLOR=#333333][FONT=Ubuntu]Intente instalando el paquete usb-modeswitch por aquello de que reconociera el modem como tal y no como una unidad de almacenamiento, y sigo sin poder conectarme, también traté expulsando la unidad y esperando a que vuelva a cargar el modem y tampoco lo he logrado. La versión de Ubuntu es 10.04 LTS - Lucid. ¿alguna idea?[/FONT][/COLOR]

---

### Post by dedalusjoyce on 2013-03-18
Adjunto el mensaje de usb-devices del modem

T:  Bus=04 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  6 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=0167 Rev=00.00
S:  Manufacturer=ZTE,Incorporated
S:  Product=ZTE LTE Technologies MSM
S:  SerialNumber=MF821_FFFS111111
C:  #Ifs= 6 Cfg#= 1 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 4 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 5 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

---

