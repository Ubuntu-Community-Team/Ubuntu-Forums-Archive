---
title: "problema de sonido en ubuntu 9.04"
date: 2009-08-01
forum: Colombia Team - Colombia
---

### Post by felsip on 2009-08-01
hola. soy nuevo en ubuntu y pues me ha gustado mucho pero tengo un problema con el sonido y es que no suena nada ni los videos de youtube o justin.tv en firefox y el reproductor de peliculas totem  ni el rhythmbox suenan y ya tengo instalado el flash player 10 y los codecs de audio correspondientes para los reproductores q trae ubuntu pero no consigo que suene. he estado viendo otros post pero no he logrado nada. asi q les agradezco la ayuda que me puedan brindar.
 Adjunto datos de mi pc  y datos q podrian adelantar una solucion:
Board: Asrock
sonido: sound blaster live value!
Ram: 2 gigas ddr 400 Mhz
video: ATI radeon 9550 de 256 Mb
HHD: maxtor 500Gb de 7200rpm (particionado para xp y ubuntu)


comandos ejecutados:


andres@ubuntu:~$ aplay -l
**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: Live [SBLive! Value [CT4670]], dispositivo 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdispositivos: 31/32
  Subdispositivo #0: subdevice #0
  Subdispositivo #1: subdevice #1
  Subdispositivo #2: subdevice #2
  Subdispositivo #3: subdevice #3
  Subdispositivo #4: subdevice #4
  Subdispositivo #5: subdevice #5
  Subdispositivo #6: subdevice #6
  Subdispositivo #7: subdevice #7
  Subdispositivo #8: subdevice #8
  Subdispositivo #9: subdevice #9
  Subdispositivo #10: subdevice #10
  Subdispositivo #11: subdevice #11
  Subdispositivo #12: subdevice #12
  Subdispositivo #13: subdevice #13
  Subdispositivo #14: subdevice #14
  Subdispositivo #15: subdevice #15
  Subdispositivo #16: subdevice #16
  Subdispositivo #17: subdevice #17
  Subdispositivo #18: subdevice #18
  Subdispositivo #19: subdevice #19
  Subdispositivo #20: subdevice #20
  Subdispositivo #21: subdevice #21
  Subdispositivo #22: subdevice #22
  Subdispositivo #23: subdevice #23
  Subdispositivo #24: subdevice #24
  Subdispositivo #25: subdevice #25
  Subdispositivo #26: subdevice #26
  Subdispositivo #27: subdevice #27
  Subdispositivo #28: subdevice #28
  Subdispositivo #29: subdevice #29
  Subdispositivo #30: subdevice #30
  Subdispositivo #31: subdevice #31
tarjeta 0: Live [SBLive! Value [CT4670]], dispositivo 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdispositivos: 8/8
  Subdispositivo #0: subdevice #0
  Subdispositivo #1: subdevice #1
  Subdispositivo #2: subdevice #2
  Subdispositivo #3: subdevice #3
  Subdispositivo #4: subdevice #4
  Subdispositivo #5: subdevice #5
  Subdispositivo #6: subdevice #6
  Subdispositivo #7: subdevice #7
tarjeta 0: Live [SBLive! Value [CT4670]], dispositivo 3: emu10k1 [Multichannel Playback]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
andres@ubuntu:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0a.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
00:0b.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 04)
00:0b.1 Input device controller: Creative Labs SB Live! Game Port (rev 01)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
01:00.1 Display controller: ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary)

---

### Post by jaume69 on 2009-09-02
Yo primero miraría en Preferencias de Sonido,qué dispositivos tienes instalados y probar si cambiando de dispositivo funciona,Alsa,Pulse,etc..
Pero supongo ya lo has probado...:)
O buscar el Driver de esa Targeta en **Google**.
No sé...

---

### Post by gcoronel on 2010-07-06
Hola. antes que nada Gracias por tu tiempo.

Yo no logro hacer andar la placa este es el resultado de mi terminal:


gustavo@gustavo-desktop:~$ sudo apt-get install mercurial
[sudo] password for gustavo: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
mercurial ya está en su versión más reciente.
0 actualizados, 0 se instalarán, 0 para eliminar y 1 no actualizados.
gustavo@gustavo-desktop:~$ uname -r
2.6.32-23-generic
gustavo@gustavo-desktop:~$ sudo apt-get install linux-headers-2.6.32-23-generic
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
linux-headers-2.6.32-23-generic ya está en su versión más reciente.
0 actualizados, 0 se instalarán, 0 para eliminar y 1 no actualizados.
gustavo@gustavo-desktop:~$ sudo apt-get install tvtime gnomeradio
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
tvtime ya está en su versión más reciente.
Se instalarán los siguientes paquetes NUEVOS:
  gnomeradio
0 actualizados, 1 se instalarán, 0 para eliminar y 1 no actualizados.
Necesito descargar 314kB de archivos.
Se utilizarán 1.876kB de espacio de disco adicional después de esta operación.
Des:1 [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid/universe gnomeradio 1.8-1 [314kB]
Descargados 314kB en 3s (78,7kB/s) 
Seleccionando el paquete gnomeradio previamente no seleccionado.
(Leyendo la base de datos ...  00%
208388 ficheros y directorios instalados actualmente.)
Desempaquetando gnomeradio (de .../gnomeradio_1.8-1_amd64.deb) ...
Procesando disparadores para hicolor-icon-theme ...
Procesando disparadores para desktop-file-utils ...
Procesando disparadores para python-gmenu ...
Rebuilding /usr/share/applications/desktop.es_AR.utf8.cache...
Procesando disparadores para man-db ...
Procesando disparadores para menu ...
Procesando disparadores para python-support ...
Configurando gnomeradio (1.8-1) ...

Procesando disparadores para menu ...
gustavo@gustavo-desktop:~$ hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
destination directory: v4l-dvb
abort: destination 'v4l-dvb' is not empty
gustavo@gustavo-desktop:~$ cd v4l-dvb/
gustavo@gustavo-desktop:~/v4l-dvb$ make
make -C /home/gustavo/v4l-dvb/v4l 

make[1]: se ingresa al directorio `/home/gustavo/v4l-dvb/v4l'
creating symbolic links...
make -C firmware prep
make[2]: Entering directory `/home/gustavo/v4l-dvb/v4l/firmware'
make[2]: Leaving directory `/home/gustavo/v4l-dvb/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/gustavo/v4l-dvb/v4l/firmware'
make[2]: Nothing to be done for `default'.
make[2]: Leaving directory `/home/gustavo/v4l-dvb/v4l/firmware'
Kernel build directory is /lib/modules/2.6.32-23-generic/build
make -C /lib/modules/2.6.32-23-generic/build SUBDIRS=/home/gustavo/v4l-dvb/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-23-generic'
  CC [M]  /home/gustavo/v4l-dvb/v4l/firedtv-1394.o
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:22:17: error: dma.h: No such file or directory
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:23:21: error: csr1212.h: No such file or directory
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:24:23: error: highlevel.h: No such file or directory
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:25:19: error: hosts.h: No such file or directory
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:26:22: error: ieee1394.h: No such file or directory
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:27:17: error: iso.h: No such file or directory
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:28:21: error: nodemgr.h: No such file or directory
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:41: warning: 'struct hpsb_iso' declared inside parameter list
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:41: warning: its scope is only this definition or declaration, which is probably not what you want
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c: In function 'rawiso_activity_cb':
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:57: error: dereferencing pointer to incomplete type
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:58: error: implicit declaration of function 'hpsb_iso_n_ready'
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:65: error: dereferencing pointer to incomplete type
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:66: error: implicit declaration of function 'dma_region_i'
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:66: error: dereferencing pointer to incomplete type
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:66: error: expected expression before 'unsigned'
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:68: error: dereferencing pointer to incomplete type
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:72: error: dereferencing pointer to incomplete type
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:86: error: implicit declaration of function 'hpsb_iso_recv_release_packets'
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c: In function 'node_of':
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:91: error: dereferencing pointer to incomplete type
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:91: warning: type defaults to 'int' in declaration of '__mptr'
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:91: warning: initialization from incompatible pointer type
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:91: error: invalid use of undefined type 'struct unit_directory'
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c: In function 'node_lock':
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:96: error: 'quadlet_t' undeclared (first use in this function)
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:96: error: (Each undeclared identifier is reported only once
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:96: error: for each function it appears in.)
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:96: error: 'd' undeclared (first use in this function)
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:97: warning: ISO C90 forbids mixed declarations and code
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:99: error: implicit declaration of function 'hpsb_node_lock'
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:100: error: 'EXTCODE_COMPARE_SWAP' undeclared (first use in this function)
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c: In function 'node_read':
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:108: error: implicit declaration of function 'hpsb_node_read'
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c: In function 'node_write':
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:113: error: implicit declaration of function 'hpsb_node_write'
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c: In function 'start_iso':
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:124: error: implicit declaration of function 'hpsb_iso_recv_init'
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:124: error: dereferencing pointer to incomplete type
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:126: error: 'HPSB_ISO_DMA_DEFAULT' undeclared (first use in this function)
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:135: error: implicit declaration of function 'hpsb_iso_recv_start'
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:138: error: implicit declaration of function 'hpsb_iso_shutdown'
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c: In function 'stop_iso':
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:149: error: implicit declaration of function 'hpsb_iso_stop'
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c: At top level:
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:164: warning: 'struct hpsb_host' declared inside parameter list
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c: In function 'fcp_request':
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:177: error: dereferencing pointer to incomplete type
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:178: error: dereferencing pointer to incomplete type
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c: In function 'node_probe':
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:192: error: dereferencing pointer to incomplete type
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:192: warning: type defaults to 'int' in declaration of '__mptr'
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:192: warning: initialization from incompatible pointer type
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:192: error: invalid use of undefined type 'struct unit_directory'
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:197: error: dereferencing pointer to incomplete type
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:198: error: dereferencing pointer to incomplete type
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:199: error: implicit declaration of function 'CSR1212_TEXTUAL_DESCRIPTOR_LEAF_DATA'
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:199: error: dereferencing pointer to incomplete type
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c: At top level:
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:258: warning: 'struct unit_directory' declared inside parameter list
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c: In function 'node_update':
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:260: error: dereferencing pointer to incomplete type
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c: At top level:
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:268: error: variable 'fdtv_driver' has initializer but incomplete type
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:269: error: unknown field 'name' specified in initializer
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:269: warning: excess elements in struct initializer
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:269: warning: (near initialization for 'fdtv_driver')
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:270: error: unknown field 'id_table' specified in initializer
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:270: warning: excess elements in struct initializer
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:270: warning: (near initialization for 'fdtv_driver')
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:271: error: unknown field 'update' specified in initializer
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:271: warning: excess elements in struct initializer
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:271: warning: (near initialization for 'fdtv_driver')
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:272: error: unknown field 'driver' specified in initializer
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:272: error: extra brace group at end of initializer
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:272: error: (near initialization for 'fdtv_driver')
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:275: warning: excess elements in struct initializer
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:275: warning: (near initialization for 'fdtv_driver')
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:278: error: variable 'fdtv_highlevel' has initializer but incomplete type
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:279: error: unknown field 'name' specified in initializer
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:279: warning: excess elements in struct initializer
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:279: warning: (near initialization for 'fdtv_highlevel')
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:280: error: unknown field 'fcp_request' specified in initializer
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:280: warning: excess elements in struct initializer
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:280: warning: (near initialization for 'fdtv_highlevel')
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c: In function 'fdtv_1394_init':
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:287: error: implicit declaration of function 'hpsb_register_highlevel'
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:288: error: implicit declaration of function 'hpsb_register_protocol'
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:291: error: implicit declaration of function 'hpsb_unregister_highlevel'
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c: In function 'fdtv_1394_exit':
/home/gustavo/v4l-dvb/v4l/firedtv-1394.c:298: error: implicit declaration of function 'hpsb_unregister_protocol'
make[3]: *** [/home/gustavo/v4l-dvb/v4l/firedtv-1394.o] Error 1
make[2]: *** [_module_/home/gustavo/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-23-generic'
make[1]: *** [default] Error 2
make[1]: se sale del directorio `/home/gustavo/v4l-dvb/v4l'
make: *** [all] Error 2
gustavo@gustavo-desktop:~/v4l-dvb$ 
gustavo@gustavo-desktop:~/v4l-dvb$ sudo make install
make -C /home/gustavo/v4l-dvb/v4l install
make[1]: se ingresa al directorio `/home/gustavo/v4l-dvb/v4l'
-e 
Removing obsolete files from /lib/modules/2.6.32-23-generic/kernel/drivers/media/video:

-e 
Removing obsolete files from /lib/modules/2.6.32-23-generic/kernel/drivers/media/dvb/cinergyT2:

-e 
Removing obsolete files from /lib/modules/2.6.32-23-generic/kernel/drivers/media/common:
ir-common.ko 
-e 
Removing obsolete files from /lib/modules/2.6.32-23-generic/kernel/drivers/media/dvb/frontends:

Installing kernel modules under /lib/modules/2.6.32-23-generic/kernel/drivers/media/:
/sbin/depmod -a 2.6.32-23-generic 
make -C firmware install
make[2]: Entering directory `/home/gustavo/v4l-dvb/v4l/firmware'
Installing firmwares at /lib/firmware: vicam/firmware.fw dabusb/firmware.fw dabusb/bitstream.bin ttusb-budget/dspbootcode.bin cpia2/stv0672_vp4.bin av7110/bootcode.bin 
make[2]: Leaving directory `/home/gustavo/v4l-dvb/v4l/firmware'
make[1]: se sale del directorio `/home/gustavo/v4l-dvb/v4l'
gustavo@gustavo-desktop:~/v4l-dvb$ modprobe -r saa7134_alsa saa7134
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
FATAL: Module saa7134_alsa is in use.
gustavo@gustavo-desktop:~/v4l-dvb$ modprobe saa7134
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.

---

