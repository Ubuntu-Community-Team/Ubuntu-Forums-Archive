---
title: "Portatil Acer 7250 i ubuntu 64bits"
date: 2008-08-22
forum: Catalan Team
---

### Post by venusfenix on 2008-08-22
bon dia a tots,

mica a mica, m'he anat acostumant al nou sistema operatiu fins al punt que per fi, tinc un portatil nou, un Acer 7250 (Turion 64x2) i he decidit instal.lar l'ubuntu 8.04 64 bits.

el problema que tinc es amb la wifi, no es pot connectar doncs no esta instalat el acer_acpi, pero segons tinc entens, ja ve instalat amb l'ubuntu. amb les comprobacions he vist que la tarja esta instalada, pero no hi ha manera de connectar-la. He seguit el passos que hi ha a la pagina [www.ubuntu.org](www.ubuntu.org), pero no em surto. Necessito assesorament de nivel baix.

Aprofito per preguntar, perque hi han vegades que quan vaig a instalar nous programes, o vull executar el synaptics, desde els menus no puc, o sigui, l'aplicacio comença a executar-se pero  es tancar, pero desde el terminal root, sempre s'executa.
potser que hagi instalat algun programa que doni problemes??

gracies,

---

### Post by papapep on 2008-08-22
> Aprofito per preguntar

Nooooop! :-) Una fil diferent per a cada pregunta, si us plau.

---

### Post by venusfenix on 2008-08-22
gracies per l'aclariment,
respecte al tema del wifi, quina resposta o solucio hi ha??

gracies,

---

### Post by papapep on 2008-08-22
Si persisteix el problema després de la reinstal·lació, necessitem saber més coses.

Fes a un terminal:

```
lspci
```

i enganxa el resultat, si us plau.

---

### Post by venusfenix on 2008-08-22
[B]00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7000M (rev a2) (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:04.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:04.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:04.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:04.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
[/B]

---

### Post by venusfenix on 2008-08-22
Gracies per tot,
al re-instalar, he vist que ha surtit una icona de maquinari, i estava instalat el driver de la wifi, pel que tinc entes, el problema es que s'activa pel butons "extras" del portatil, i aixo no esta instalat (?).

---

### Post by papapep on 2008-08-22
No acabo d'entendre el que has volgut dir.

---

### Post by venusfenix on 2008-08-22
primer de tot, perdona, potser estic liant el tema.
he estat mirant en blogs, etc... i n'hi ha molta gent amb portatil acer amb problemes similars, i tots coincideixen que el problema no es la instalació dels drivers de la tarja de la wifi, sino, que per activar-la es fa a traves del teclat, hi ha un buto especial per activar la wifi, al igual que n'hi ha per executar el navegador o el correu email.
parlen d'instalar "acer_acpi" pero per la version hardy heron, ya ve instalada. (?)

t'he aclarat o liat encara mes???

gracies per tot!!

---

### Post by patrickfromspain on 2008-08-22
segons aixo: [http://ubuntuforums.org/showthread.php?p=5323773](http://ubuntuforums.org/showthread.php?p=5323773) per activar la wifi, en un terminal, has de fer:

```

sudo -s
echo 1 > /proc/acpi/acer/wireless

```

si aixo no funciona, prova el següent:
```

sudo -s 
chmod 777 /proc/acpi/acer/wireless
echo 1 > /proc/acpi/acer/wireless

```

salut

---

### Post by SiscoGarcia on 2008-08-22
Perdoneu que m'hi posi pel mig, però l'enllaç proposat per venusfenix no em funciona, a la resta sí?
> **venusfenix said:**
> ..He seguit el passos que hi ha a la pagina [www.ubuntu.org](www.ubuntu.org), pero no em surto...

Adjunto captura del resultat que m'ha donat per 3 cops.

---

### Post by Rafel HiR on 2008-08-22
El mateix. No sé quines passes ha seguit :D

---

### Post by papapep on 2008-08-23
Independent del tema de l'enllaç, hauria de provar a veure si [el que diu el Patrick]("http://ubuntuforums.org/showpost.php?p=5644393&postcount=9") li funciona.

---

### Post by venusfenix on 2008-08-23
buenas!!
doncs em sembla que no funciona:

root@Shuttle:~# echo 1 > /proc/acpi/acer/wireless
root@Shuttle:~# sudo -s
root@Shuttle:~# chmod 777 /proc/acpi/acer/wireless
root@Shuttle:~# echo 1 > /proc/acpi/acer/wireless


no ha donat cap missatge d'error, pero al portatil seguim sense wifi....

snif...

---

### Post by papapep on 2008-08-23
Fes a un terminal:

```
cat /proc/acpi/acer/wireless
```

Si el que surt és "1", reinicia l'ordinador, i a veure si funciona.

---

### Post by venusfenix on 2008-08-23
jose@Shuttle:~$ cat /proc/acpi/acer/wireless
0
jose@Shuttle:~$ 


surt 0

(?) llavors (?)

---

### Post by papapep on 2008-08-23
Torna-hi. Ara fes:

```
sudo echo 1 > /proc/acpi/acer/wireless
```

(ara et demanarà al contrasenya)

i un cop fet això, torna a fer:

```
cat /proc/acpi/acer/wireless
```

a veure si ara ja té l'1.

Si és així, reinicia.

Si no té l'1, posa el que et surti en fer:

```
ls -la /proc/acpi/acer/wireless
```

---

### Post by venusfenix on 2008-08-23
jose@Shuttle:~$ sudo echo 1 > /proc/acpi/acer/wireless
bash: /proc/acpi/acer/wireless: Permission denied
jose@Shuttle:~$ sudo -s
[sudo] password for jose: 
root@Shuttle:~# cat /proc/acpi/acer/wireless
1
root@Shuttle:~# 


ha passat aixo
 passso a reinicia, i dic alguna cosa

---

### Post by venusfenix on 2008-08-23
jose@Shuttle:~$ sudo echo 1 > /proc/acpi/acer/wireless
bash: /proc/acpi/acer/wireless: Permission denied
jose@Shuttle:~$ sudo -s
[sudo] password for jose: 
root@Shuttle:~# cat /proc/acpi/acer/wireless
1
root@Shuttle:~# 


ha passat aixo
 passso a reinicia, i dic alguna cosa

---

### Post by patrickfromspain on 2008-08-23
compte! sudo echo molt segurament et donara error. Has de fer primer sudo -s, per entrar a un terminal de root, i despres l'ordre echo 1 > /proc/acpi/acer/wireless o tambe podries provar amb echo "enabled: 1" > /proc/acpi/acer/wireless

salut

---

### Post by venusfenix on 2008-08-24
jose@Shuttle:~$ sudo -s
root@Shuttle:~# echo 1 > /proc/acpi/acer/wireless
root@Shuttle:~# cat /proc/acpi/acer/wireless
1
root@Shuttle:~# echo "enabled: 1" > /proc/acpi/acer/wireless
bash: echo: write error: Invalid argument
root@Shuttle:~# 


m'hen surt error
igualment, ahir em surtia 1 pero al re-inicia la wireless continuaba sense funcionar.
avui h'he tornat i continua sense funcionar!

gracies a tots pel suport!

---

### Post by papapep on 2008-08-24
Hauries de ficar la ordre (**echo 1 > /proc/acpi/acer/wireless**) dins el fitxer /etc/profile, així s'executarà la ordre cada cop que engenguis l'ordinador.

Si fas:

```
sudo nano /etc/profile
```

L'hauries de ficar just abans o després de la última línia, que hauria de dir "umask 022", per no trencar l'script que hi ha més amunt.

podràs enganxar-hi el text. Per desar només et cal prèmer Ctrl+X, prèmer Intro, acceptant el nom de fitxer que et proposa, i ja està.

Respecte el wifi, no hi ha cap activitat wifi al gestor de xarxes? no en detecta cap ni una?

---

### Post by venusfenix on 2008-08-24
[IMG]/home/jose/Escriptori/captura-1.png[/IMG]

buenas,
he fet el que deies, pero continua sense funcionar.
***paso captura de pantalla perque vegis que el gestor ni tan sols hi ha la opcio de xarxa sense fils.***

he intentat passar un printscreen dels parametres de xarxa, pero no se com fer-ho.
igualment, nomes hi ha la configuracion de xarxa amb fil i conexio punt a punt.
encara no surt la conexio de xarxa sense fils.

...

---

### Post by papapep on 2008-08-24
Per adjuntar imatges has de fer-ho amb la icona del clip, no amb la de la muntanya. Si ho fas amb la de la muntanya et demana una url on tinguis la imatge penjada, per això no et va.

> buenas,
he fet el que deies, pero continua sense funcionar.

Respecte el teu problema, enganxa'ns el resultat de fer:

```
ifconfig
```

i també:

```
iwconfig
```

---

### Post by venusfenix on 2008-08-25
buenas,

els resultats aquesta nit, entre setmana nomes put possar-me per la tarde-nit.
nomes un comentari, no tinc icona amb un clip ???

gracies,

---

### Post by papapep on 2008-08-25
mmmmm....no tens uns icona com la que et marco a la imatge que adjunto??

---

### Post by venusfenix on 2008-08-25
no, nomes l'icona de sense format, negreta, cursiva, subratllat, color, url link, picture link i comments.
nomes aixo....

respecte a la prova, ho faré en unes 3-4 hores, ara estic a la feina.

Moltes gracies!

---

### Post by venusfenix on 2008-08-25
buenas,

el resultat esperat:


jose@Shuttle:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:38:68:9e:c4  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe68:9ec4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:183 errors:0 dropped:0 overruns:0 frame:0
          TX packets:249 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:178975 (174.7 KB)  TX bytes:31259 (30.5 KB)
          Interrupt:252 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:98 errors:0 dropped:0 overruns:0 frame:0
          TX packets:98 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4900 (4.7 KB)  TX bytes:4900 (4.7 KB)

jose@Shuttle:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

jose@Shuttle:~$

---

### Post by oriolsbd on 2008-08-25
Hola, Venusfenix.

Podràs veure la icona que diu en Papapep si, després de prémer el botó per respondre, prems el botó "Go Advanced". Llavors tindràs un editor amb moltes més opcions.

Salut!

Oriol.

---

### Post by venusfenix on 2008-08-26
he probat el "go advanced" i funciona!! moltes gracies,

per altre banda, el tema wifi, hi ha alguna conclusio???

gracies,

---

### Post by papapep on 2008-08-26
Rebuscant una miqueta, he trobat que fa uns mesos ja vam solucionar un tema molt semblant: [http://ubuntuforums.org/showthread.php?p=4905351](http://ubuntuforums.org/showthread.php?p=4905351)

El problema és que, com a mínim jo, en aquest moment no sóc capaç d'accedir a la pàgina [que sembla]("http://ubuntuforums.org/showpost.php?p=4904864&postcount=16") que donava la solució: [http://www.ubuntu-es.org/index.php?q=node/83813](http://www.ubuntu-es.org/index.php?q=node/83813)

Haurem d'esperar si d'aquí una estona o demà el servidor de ubuntu-es funciona (a no ser que el problema el tingui jo i realment sigui accessible...)

---

### Post by SiscoGarcia on 2008-08-26
Per si et serveix de consol a mi tampoc no em funciona. Ja es mes improbable que sigui un problema teu.

---

### Post by torracastanyes on 2008-08-26
Els servidors d'Ubuntu.es no van gaire lluents ja fa díes.
Algú els en va oferir un de nou fa poc, pero sembla que els Estatuts no els permeten acceptar donatius.

A veure si aquest ajuda:

[http://ubuntuforums.org/showthread.php?t=816780&highlight=acer+wifi](http://ubuntuforums.org/showthread.php?t=816780&highlight=acer+wifi)

---

### Post by papapep on 2008-08-27
Com que sembla que han pogut aixecar el servidor, i abans de que els torni a caure, he copiat "vílment" part del text de l'article:

> Saludos a todos, este es mi problema:

Uso un portatil Samsung r60plus. Viene equipado con una Atheros AR5007EG para conectar con redes sin cables. La orden lspci dice de mi dispositivo lo siguiente:

    02:00.0 Ethernet controller [0200]: Atheros Communications Inc. **AR242x 802.11abg** Wireless PCI Express Adapter [168c:001c] (rev 01)

Ubuntu 8.04 beta detecta la presencia del dispositivo pero, a pesar de tener los controladores restringidos Atheros Hardware Access Layer (HAL) y Support for Atheros 802.11 wireless LAN card habilitados, network-manager no detecta la presencia de dispositivo wifi alguno

[.....]

Solución aportada por luks911:

    He descargado el controlador [http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz)

    Desde una terminal de comandos, nos movemos al directorio donde por defecto se ha descargado el fichero

    cd ~

    toca descomprimirlo con

    sudo tar -xzvf madwifi-nr-r3366+ar5007.tar.gz

    nos movemos al nuevo directorio y compilamos

    sudo make

    borramos posibles instalaciones anteriores de madwifi

    sudo rm -rf /lib/modules/$(uname -r)/madwifi

    e instalamos el controlador

    sudo make install

    antes de reiniciar, me aseguro de habitilar los controladores restringidos desde Sistema -> Administración -> Controladores de hardware

    Mi interfaz inalámbrica funciona correctamente, toca todas las señales a su alcance y conecta. No sufre ningún tipo de "desconfiguración" al reiniciar.


---

### Post by venusfenix on 2008-08-27
Buenas,

sembla que te bona pinta, nomes un problema, el link per descarregar els drivers, funciona pero no hi han drivers, nomes un readme que et desvia a una altre adreça i res. No hi han drivers.... :(

---

### Post by venusfenix on 2008-08-27
jose@Shuttle:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:38:68:9e:c4  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe68:9ec4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:707 errors:0 dropped:0 overruns:0 frame:0
          TX packets:825 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:656246 (640.8 KB)  TX bytes:153102 (149.5 KB)
          Interrupt:252 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:204 errors:0 dropped:0 overruns:0 frame:0
          TX packets:204 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11982 (11.7 KB)  TX bytes:11982 (11.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:4c:23:29:6e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Memory:f2200000-f2210000 

wlan0:avahi Link encap:Ethernet  HWaddr 00:1e:4c:23:29:6e  
          inet addr:169.254.3.234  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Memory:f2200000-f2210000 

jose@Shuttle:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jose@Shuttle:~$ 
jose@Shuttle:~$ 


Ultimas noticias!!!!

no se com ho he fet.... pero......... resultats!!!!!!

encara no funciona, pero almenys ja n'hi han drivers instalats!!!

ja surten les opcions i tot!!!
pero al terminal hi diu que l'alimentacio esta apagada!!

VAMOS ESPARTANOS!!!

---

### Post by papapep on 2008-08-27
> encara no funciona, pero almenys ja n'hi han drivers instalats!!!


Doncs per no funcionar, a la captura de pantalla veig una [ssid]("http://en.wikipedia.org/wiki/Essid") identificada :-)

---

### Post by venusfenix on 2008-08-28
CORRECTE!!

no nomes aixo, sino que scanejava correctament, vull dir que tenia un llistat amb totes les wifies dels veïns, i vaig aprofitar per configurar la de casa meva, pero al desconectar el cable, el tema va caure.

al fer iwconfig i veure que power management off.

igualment, avui continuaré buscant i re-buscant.
pero cualsevol consell es benvingut!!

gracies,

---

### Post by venusfenix on 2008-08-28
buenas a tots!!

estic tornan a mirar el tema, pero a diferencia d'ahir, avui no em surt el llistat de Essid que veu la meva wifi.
no l'entent que pasa....

per fi surt l'opcio a xarxes, pero es com si no estigues, pero ahir semblava que funcionaba o almenys ho va fer durant una estona.....

(?)

---

### Post by venusfenix on 2008-08-28
Sres,

fent un resum, molt resumit.

a l'opcio xarxes, per fi, hi surt l'opcio de conexió sense fils.
quant hi vaig aquesta opció, hi puc escanejar les essid que n'hi han al veïnat.
per altre bande, al router, hi veu el portatil conectat, malgrat tot, no put navegar per internet, ni pidgin, ni emails...

que puc fer??

gracies,

---

### Post by imagenius on 2008-08-28
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by oriolsbd on 2008-08-28
Hola.

Podria ser un problema amb el network-manager. Per què no proves d'instal·lar-te el Wicd?

En Papapep ha comentat en diversos fils que ell tenia molts problemes amb la xarxa, i que el Wicd li va solucionar (perquè el predeterminat de Gnome té molts problemes). Jo no fa massa l'he recomanat a un amic que també tenia problemes amb la xarxa, i diu que ha estat "mà de sant".

Com que no te'l podràs instal·lar per Synaptic perquè no tens xarxa, t'adjunto el fitxer .deb de l'última versió (la que ara mateix hi ha a la seva web).

Per instal·lar-lo, desa'l a qualsevol directori. Obre un terminal i ves al directori on l'hagis desat. Primer hauràs de desinstal·lar l'administrador de xarxa de Gnome:

```
sudo apt-get remove network-manager network-manager-gnome
```

Després, ja pots instal·lar el Wicd:
```
sudo dpkg -i wicd_1.4.2-1_all.deb
```

Per si vols buscar més informació, la web és aquesta: [http://wicd.sourceforge.net](http://wicd.sourceforge.net)

Salut!

Oriol.

---

### Post by alfaalbert on 2008-08-28
Hola:

Tengo un problema similar pero con otro tipo de Acer, aunque creo que podría ser la misma solución. 

Tengo dos sistemas operativos en mi ACER TravelMate 5720: WINDOWS VISTA (WV) AND UBUNTU 8.04. Con WV no tengo ningún problema, pero con ubuntu no me reconoce ninguna conexión wireless. En España (estoy en el extranjero por estudios) utilicé conexión vía módem por cable y no tuve ningún problema.

Por último, el botón de activar el wireless no me funciona en ubuntu. A continuación dos reportes del Terminal: 1. lspci, 2. sudo lshw -C networky 3. iwconfig:

albert@albert-laptop:~$ lspci 
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03) 00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03) 00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03) 00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03) 00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) 00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03) 00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) 00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) 00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03) 00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) 00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) 00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) 00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) 00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03) 00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) 00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03) 00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03) 02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02) 04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02) 0f:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller 0f:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller 0f:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) 0f:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller albert@albert-laptop:~$


albert@albert-laptop:~$ sudo lshw -C network [sudo] password for albert:    *-network                       description: Ethernet interface        product: NetLink BCM5787M Gigabit Ethernet PCI Express        vendor: Broadcom Corporation        physical id: 0        bus info: pci@0000:02:00.0        logical name: eth0        version: 02        serial: 00:1d:72:32:90:be        capacity: 1GB/s        width: 64 bits        clock: 33MHz        capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation        configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 firmware=5787m-v3.23 latency=0 link=no module=tg3 multicast=yes port=twisted pair   *-network        description: Wireless interface        product: PRO/Wireless 3945ABG Network Connection        vendor: Intel Corporation        physical id: 0        bus info: pci@0000:04:00.0        logical name: wmaster0        version: 02        serial: 00:1f:3c:2f:61:04        width: 32 bits        clock: 33MHz        capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless        configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g albert@albert-laptop:~$ iwconfig lo        no wireless extensions. eth0      no wireless extensions. irda0     no wireless extensions. wmaster0  no wireless extensions. wlan0     IEEE 802.11g  ESSID:""  Nickname:""           Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated              Tx-Power=27 dBm              Retry min limit:7   RTS thr:off   Fragment thr=2346 B              Power Management:off           Link Quality:0  Signal level:0  Noise level:0           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0           Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
albert@albert-laptop:~$

---

### Post by SiscoGarcia on 2008-08-28
alfaalbert, recorda que ets al fòrum d'ubuntaires **en català**, i pel que fa al teu problema no tinc cap resposta però m'ha estranyat l'idioma que has fet servir.

---

### Post by venusfenix on 2008-08-29
ho he fet, pero, sense resultat....
es mes, ara en torna a no executar el paquet synaptics, ni el cataleg d'aplicacions.

em fes un pas endavant i un altre endarrere...

---

### Post by papapep on 2008-08-29
Quin missatge et dóna en intentar executar el Synaptic?

> ho he fet, pero, sense resultat....

Què has fet en concret? Instal·lar el wicd? has provat tots els mòduls, a veure si algun et funciona? (veure imatge adjunta)

---

### Post by venusfenix on 2008-08-30
simplement, intenta obrir-se l'aplicacio i al cap d'una estona, es tanca i res mes.
el cataleg d'aplicacions, s'executa pero a l'aplicar (un cop seleccionat alguna aplicacio) es queda l'ordinador com penjat, no demana el password, simplement es queda el mouse en modo rellotge i va passan el temps.
respecte al wicd no he probat totes les opcions. Anire fent i dic alguna cosa al respecte.

Gracies,

---

### Post by papapep on 2008-08-30
Executa'l a un terminal, per veure els errors que et mostra:

```
sudo synaptic
```

---

### Post by venusfenix on 2008-09-01
Buenas!!
encara no m'he pogut posar, de totes maneres, tant rapid pogui posar-me, tant rapid publicaré el resultat.

la feina ... "sin ella, pero tampoco con ella"

gracies igualment,

---

### Post by venusfenix on 2008-09-03
buenas
he tornat....
finalment he pogut posar-me davant de l'ordinar.
he tornat a canviar, ho sento molt, pero soc tecno-pijo i quan he vist el kubuntu, m'ha semblat millor (esteticament) i con tenia una col.lecció de problemes, pues eso, a començar.
He re-instal.lat el tema, pero aquest cop Kubuntu.
sembla que tot funciona correctament, excepte la wifi, i el control de volum que te el portatil (la rodeta per pujar-baixar).
he seguit el vostres passos, desde principi a final, i dir-vos que he aconseguit d'instal.lar els driver de la wifi, i com la vegada anterior, la tarja escanejar las xarxes, pero no pot conectar-se (igual que la vegada anterior).
he seguit els comentaris, i desinstal.lat el network-manager i instal.lat el wicd, pero sense resultats.
en aquest moment, he desfet el ultim canvi i continuu sense poguer conectar-me a la meva wifi.

gracies per la vostra paciencia!!

---

### Post by venusfenix on 2008-09-07
Buenas....

he tornat, com ja he comentat, el tema no funciona, he tornat a fer tot, tal i com dieu, no ho hi ha manera, es mes, en el moment que he tret el network manager i instalo el wicd, hem quedo sense la conexió per cable tambe.
i tinc que tornar a instalar el network manager i llavors la conexió per cable torna a funciona, pero la wifi, com a molt, hem mostra les xarxes disponibles pero no es conecta. He probat de treure-li la encriptació WEP al router, i continua sense funcionar.
con lo cual, me quedo con lo puesto.

pero hi ha alguna solució???

la agrairia molt!!

gracies a tots!!!!

---

### Post by venusfenix on 2008-09-07
buenas, mes noticies,
sembla que funciona pero nomes amb l'ethernet.
en altres paraules, m'he adonat que ara va mes depresa que abans, i m'he fixat que el router te les llums de cable i wifi sincronitzades i a tope.
m'he ficat en el router i em confirma que el portatil esta conectat dos vegades amb dues conexions distintes (diferents mac), hi ha trafic per ethernet y per wlan, pero el tema es que quan desconecto el cable, la wifi tambe far shutdown.
??? que passa????

"Estamos cerca"

per si pot servir:

jose@Shuttle:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:38:68:9e:c4  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe68:9ec4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5792 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6376 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:781285 (762.9 KB)  TX bytes:631197 (616.4 KB)
          Interrupt:252 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:202 errors:0 dropped:0 overruns:0 frame:0
          TX packets:202 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10100 (9.8 KB)  TX bytes:10100 (9.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:4c:23:29:6e  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:4cff:fe23:296e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:76165 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70975 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:78031594 (74.4 MB)  TX bytes:6800191 (6.4 MB)
          Interrupt:19 Memory:f2200000-f2210000 

jose@Shuttle:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Francesca"  Nickname:"Francesca"
          Mode:Managed  Frequency:2.467 GHz  Access Point: 00:19:5B:97:CA:C0   
          Bit Rate=54 Mb/s   
          Power Management:off
          Link Quality:100/100  Signal level:-26 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:21906  Invalid misc:18137   Missed beacon:0

jose@Shuttle:~$ 

espero noticies!!!

gracies,

---

### Post by venusfenix on 2008-09-07
Buenas un altre cop,

una pista, pero que nomes m'ha funcionat durant una sessio.
despress d'adonar-me que esta conectada a la wifi i ethernet, he anat al terminal i he fet un sudo ifdown eth0
llavors, ha començat a funcionar al wifi per tota ella sola.
al re-iniciar, el tema o efecte a desaparegut...
com tornar???

gracies,

---

