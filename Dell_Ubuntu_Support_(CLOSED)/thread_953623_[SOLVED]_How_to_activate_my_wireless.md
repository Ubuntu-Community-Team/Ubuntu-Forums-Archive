---
title: "[SOLVED] How to activate my wireless"
date: 2008-10-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by beidache on 2008-10-20
Hello, I have a connection problem, my wireless is not detected by my computer when I write  iwconfig this is what I get 

fernando@Petacho:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:4  Signal level:190  Noise level:162
          Rx invalid nwid:0  invalid crypt:5  invalid misc:0

Does anybody can hell me?
Thanks in advance

---

### Post by Terl on 2008-10-20
I have a Dell 1501 laptop.  I used this to get it going:  [http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

---

### Post by beidache on 2008-10-20
Thanks for your answer but Im alreday have the wireless install, is detecting the diferent wireless signal but is not making connection,

---

### Post by beidache on 2008-10-20
Thanks for your answer but Im already have the wireless install, is detecting the different wireless signal but is not making connection,

---

### Post by solaceinsilence9 on 2008-10-20
if it is detecting the wifi connection but is unable to connect, id say check your settings to make sure you have the right passphrase typed in. Also, is your router set up for a certain type of encryption, i.e. WEP? If so make sure those settings are correct also.

---

### Post by beidache on 2008-10-22
Th<nks for your answer but what you mean with "check your settings to make sure you have the right passphrase typed in"? sorry Im new in ubuntu so if you can explain me from the basics I will appreciate that

---

### Post by rasmus91 on 2008-10-22
which distro are you using? which version of network manager?

---

### Post by beidache on 2008-10-22
This is what I just did, first i reboot my computer change from ubuntu 8.04 64bit to ubuntu 8.04 32 bit, and i installed this:

petacho@petacho-lap:~$ echo -e 'blacklist bcm43xx\nblacklist wl' | sudo tee -a /etc/modprobe.d/blacklist 
[sudo] password for petacho: 
blacklist bcm43xx 
blacklist wl 
petacho@petacho-lap:~$ sudo apt-get install ndiswrapper-utils-1.9 
Leyendo lista de paquetes... Hecho 
Creando árbol de dependencias       
Leyendo la información de estado... Hecho 
Se instalaron de forma automática los siguientes paquetes y ya no son necesarios. 
  linux-headers-2.6.24-19-generic linux-headers-2.6.24-19 
Utilice «apt-get autoremove» para eliminarlos. 
Se instalarán los siguientes paquetes extras: 
  ndiswrapper-common 
Paquetes sugeridos: 
  ndiswrapper-source 
Se instalarán los siguientes paquetes NUEVOS: 
  ndiswrapper-common ndiswrapper-utils-1.9 
0 actualizados, 2 se instalarán, 0 para eliminar y 0 no actualizados. 
Necesito descargar 30,4kB de archivos. 
Se utilizarán 213kB de espacio de disco adicional después de desempaquetar. 
¿Desea continuar [S/n]? s 
Des:1 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) hardy/main ndiswrapper-common 1.50-1ubuntu1 [11,4kB] 
Des:2 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) hardy/main ndiswrapper-utils-1.9 1.50-1ubuntu1 [19,0kB] 
Descargados 30,4kB en 3s (8913B/s)            
Seleccionando el paquete ndiswrapper-common previamente no seleccionado. 
(Leyendo la base de datos ...  
113998 ficheros y directorios instalados actualmente.) 
Desempaquetando ndiswrapper-common (de .../ndiswrapper-common_1.50-1ubuntu1_all.deb) ... 
Seleccionando el paquete ndiswrapper-utils-1.9 previamente no seleccionado. 
Desempaquetando ndiswrapper-utils-1.9 (de .../ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb) ... 
Configurando ndiswrapper-common (1.50-1ubuntu1) ... 
Configurando ndiswrapper-utils-1.9 (1.50-1ubuntu1) ... 
petacho@petacho-lap:~$ mkdir ~/bcm43xx; cd ~/bcm43xx 
petacho@petacho-lap:~/bcm43xx$ sudo apt-get install cabextract 
Leyendo lista de paquetes... Hecho 
Creando árbol de dependencias       
Leyendo la información de estado... Hecho 
Se instalaron de forma automática los siguientes paquetes y ya no son necesarios. 
  linux-headers-2.6.24-19-generic linux-headers-2.6.24-19 
Utilice «apt-get autoremove» para eliminarlos. 
Se instalarán los siguientes paquetes NUEVOS: 
  cabextract 
0 actualizados, 1 se instalarán, 0 para eliminar y 0 no actualizados. 
Necesito descargar 53,9kB de archivos. 
Se utilizarán 188kB de espacio de disco adicional después de desempaquetar. 
Des:1 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) hardy/universe cabextract 1.2-2 [53,9kB] 
Descargados 53,9kB en 2s (19,9kB/s) 
Seleccionando el paquete cabextract previamente no seleccionado. 
(Leyendo la base de datos ...  
114020 ficheros y directorios instalados actualmente.) 
Desempaquetando cabextract (de .../cabextract_1.2-2_i386.deb) ... 
Configurando cabextract (1.2-2) ... 
petacho@petacho-lap:~/bcm43xx$ wget [ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe) 
--00:53:39--  [ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe) 
           => `sp34152.exe' 
Resolviendo ftp.compaq.com... 161.114.23.171 
Conectando a ftp.compaq.com|161.114.23.171|:21... conectado. 
Identificándose como anonymous ... ¡Conectado! 
==> SYST ... hecho.    ==> PWD ... hecho. 
==> TYPE I ... hecho.  ==> CWD /pub/softpaq/sp34001-34500 ... hecho. 
==> PASV ... hecho.    ==> RETR sp34152.exe ... hecho. 

    [   <=>                               ] 4,494,456     14.19K/s             

00:57:21(20.19 KB/s) - `sp34152.exe' guardado [4494456] 

petacho@petacho-lap:~/bcm43xx$ cabextract sp34152.exe 
Extracting cabinet: sp34152.exe 
  extracting bcm1xsup.dll 
  extracting bcm43xx.cat 
  extracting bcm43xx64.cat 
  extracting Bcmnpf64.sys 
  extracting bcmwl5.inf 
  extracting bcmwl5.sys 
  extracting bcmwl564.sys 
  extracting bcmwliss.dll 
  extracting bcmwlnpf.sys 
  extracting bcmwlpkt.dll 
  extracting bcmwls.ini 
  extracting bcmwls32.exe 
  extracting bcmwls64.exe 
  extracting bcmwlu00.exe 
  extracting data1.cab 
  extracting data1.hdr 
  extracting data2.cab 
  extracting ikernel.ex_ 
  extracting is.exe 
  extracting launcher.ini 
  extracting layout.bin 
  extracting setup.exe 
  extracting Setup.ini 
  extracting setup.inx 
  extracting setup.iss 
  extracting sp34152.cva 

All done, no errors. 
petacho@petacho-lap:~/bcm43xx$ sudo ndiswrapper -i bcmwl5.inf 
installing bcmwl5 ... 
petacho@petacho-lap:~/bcm43xx$ ndiswrapper -l 
bcmwl5 : driver installed 
	device (14E4:4311) present (alternate driver: ssb) 
petacho@petacho-lap:~/bcm43xx$ sudo depmod -a 
petacho@petacho-lap:~/bcm43xx$ sudo modprobe ndiswrapper 
petacho@petacho-lap:~/bcm43xx$ sudo cp /etc/network/interfaces /etc/network/interfaces.orig 
petacho@petacho-lap:~/bcm43xx$ echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces 
auto lo 
iface lo inet loopback 

petacho@petacho-lap:~/bcm43xx$ sudo ndiswrapper -m 
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ... 

************************************************************************ 
* 
* The update-modules command is deprecated and should not be used! 
* 
************************************************************************ 

petacho@petacho-lap:~/bcm43xx$ echo 'ndiswrapper' | sudo tee -a /etc/modules 
ndiswrapper 
petacho@petacho-lap:~/bcm43xx$ echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant 
ENABLED=0 
petacho@petacho-lap:~/bcm43xx$ lshw -C network 
WARNING: you should run this program as super-user. 
  *-network               
       description: Wireless interface 
       product: BCM4311 802.11b/g WLAN 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:0c:00.0 
       logical name: eth1 
       version: 01 
       serial: 00:1b:fc:00:87:b3 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11 
  *-network 
       description: Ethernet interface 
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:09:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:18:8b:c6:6c:bb 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5752-v3.19 ip=192.168.1.101 latency=0 module=tg3 multicast=yes

I hope you can help me, thanks

---

### Post by beidache on 2008-10-23
I just did it I put:

You also need to blacklist b43 and ssb:
Code:

echo -e 'blacklist b43\nblacklist ssb' | sudo tee -a /etc/modprobe.d/blacklist

After that, to test your wireless:
Code:

sudo modprobe -r b43 ssb ndiswrapper wl bcm43xx
sudo modprobe ndiswrapper
sudo iwlist scan

Hope that helps.

Ayuthia 

And my problem was solved

---

