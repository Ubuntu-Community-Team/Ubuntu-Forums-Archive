---
title: "terratec cinergy T²"
date: 2006-01-13
forum: Desktop Environments
---

### Post by feuervogel on 2006-01-13
hello!

i've just bought a terratec cinergy T² from tuxhardware.de, because i wanted to have an easy installation process.

the [product page]("http://www.tuxhardware.de/category152_70/product886/product_info.html") tells me to use xawtv. i've already installed dvb-utils and kernel 2.6.12-10, but if i want to start xawtv this happens:

julian@pc:~$ xawtv
This is xawtv-3.94, running on Linux/i686 (2.6.12-10-386)
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: Datei oder Verzeichnis nicht gefunden
v4l2: open /dev/video0: Datei oder Verzeichnis nicht gefunden
v4l: open /dev/video0: Datei oder Verzeichnis nicht gefunden
no video grabber device available

please help me! thanks!

---

### Post by Ampersand on 2006-01-13
If you run
```
lsusb
```
does it appear in the list?

---

### Post by feuervogel on 2006-01-13
[QUOTE=Ampersand]If you run
```
lsusb
```
does it appear in the list?[/QUOTE]

yes:

julian@pc:~$ lsusb
Bus 003 Device 002: ID 0ccd:0038 TerraTec Electronic GmbH Cinergy T^2 DVB-T Receiver

---

### Post by Ampersand on 2006-01-13
try unplugging it, then plugging it in and running 
```
dmesg | tail
```

This should tell you whether it's using /dev/video0 or somewhere else.

Also try using a different program, such as camorama or motv. Some programs are better at detecting hardware than others.

---

### Post by feuervogel on 2006-01-14
unplugging and plugging:

[4294998.297000] usb 3-2: USB disconnect, address 4
[4295002.463000] usb 3-2: new high speed USB device using ehci_hcd and address 5
[4295002.540000] DVB: registering new adapter (TerraTec/qanu USB2.0 Highspeed DVB-T Receiver).

---

### Post by fdimmling on 2006-01-14
I have the Terratec Cinergy T2 and it works out of the box with Kaffeine. I do not know if xawt is supporting DBV-T, however you can use the dvb-utils and xine if you dislike KDE programs.  But kaffeine has all you need, I use it in an Gnome environment. Maybe you have to reload the frequency table for your location and of course you have to make the frequency scan first before you can select a tv station. Here in Berlin you can even get digital radio stations.

Friedrich :smile: 

PS My first Cinergy T2 was broken and I had to get it replaced.

---

### Post by feuervogel on 2006-01-16
hallo fdimmling...ich hab jetzt mal die frequenzen neu geladen. nun klicke ich auf DVB => channels => start scan (de-Leipzig ist ausgew&#228;hlt). Dann scannt der ne weile, und bleibt bei 60% stehen, dr&#252;cke ich auf stopp scan, h&#228;ngt sich kaffeine auf.

for the english speaking people: when i scan to get channels the progress bar stops at 60% and kaffeine must be quitted with force and restarted.

---

### Post by RikoW on 2006-01-17
I had the same problem you have, feuervolgel. also with kaffeine + Cinergy T2.
What I did was connecting the tuner to a better antenna (with build in amplifier)/move to a different location to improve reception.
However, even then I had to restart the scan a few times until it went through.
After it did go through, I just plugged the antenna which came with the device back in and I' watching happily ever after.

I wanted kaffeine for recording. Before I was setting up xine for DVB. Here scanning worked much smoother:

1. create a channel list: 
scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/de-Hamburg > channels .conf
2. cp channels.conf ~/.xine
3. start xine, enable controls, and select channel

Good luck,

              Riko

---

### Post by feuervogel on 2006-01-19
yeah cool. i will try it with a better (active? amplified? don't know how to call it)) antenna. i have a [SIZE="1"]windows[/SIZE]-partition on my laptop, even there I had problems with receiving the whole bunch of channels. thanks for the help, i will return when i will have bought the new antenna.

---

### Post by feuervogel on 2006-01-19
hum:

> julian@pc:/usr/share/doc/dvb-utils/examples/scan/dvb-t$ ls -l | grep de
-rw-r--r--  1 root root  363 2005-04-15 06:49 au-Adelaide
-rw-r--r--  1 root root  262 2004-04-22 13:09 de-Berlin
-rw-r--r--  1 root root  337 2005-04-15 06:49 de-Braunschweig
-rw-r--r--  1 root root  401 2005-04-15 06:49 de-Bremen
-rw-r--r--  1 root root 1889 2005-04-15 06:49 de-Frankfurt
-rw-r--r--  1 root root  771 2005-04-15 06:50 de-Hamburg
-rw-r--r--  1 root root  333 2005-04-15 06:49 de-Hannover
-rw-r--r--  1 root root  691 2005-04-15 06:49 de-Kiel
-rw-r--r--  1 root root  354 2005-04-15 06:49 de-Koeln-Bonn
-rw-r--r--  1 root root  313 2005-04-15 06:49 de-Luebeck
-rw-r--r--  1 root root  367 2005-04-15 06:49 de-Ruhrgebiet
-rw-r--r--  1 root root  352 2004-04-22 13:09 nl-AlphenaandenRijn
-rw-r--r--  1 root root  311 2005-04-15 06:50 se-Skovde
-rw-r--r--  1 root root  329 2005-04-15 06:50 se-Sodertalje_Ragnhildsborg
-rw-r--r--  1 root root  270 2005-04-15 06:50 se-Uddevalla


nice, but there is none for leipzig :-/ where can i get it? or is kaffeine storing its frequencies? yeah, in my case:
> 
julian@pc:~/.kde/share/apps/kaffeine/dvb-t$ ls -l | grep Leipzig
-rw-r--r--  1 julian julian  343 2006-01-16 15:07 de-Leipzig


---

### Post by RikoW on 2006-01-20
The format of the scan files for Kaffeine and for dvb-utils is the same. So you could just do the dvb-utils scan I mentioned above with the file for Leibzig you found in your Kaffeine directory.

good luck!

     Riko

---

### Post by feuervogel on 2006-01-20
YEAH now i bought an active antenna with max. 36 dB and it works fine! thanks everybody!

can't install xine, but now i use gxine...quite nice!

---

### Post by CHUCKYCHUCK on 2006-07-06
could you make the remote control work ?
thx

---

### Post by fdimmling on 2006-07-07
> **CHUCKYCHUCK said:**
> could you make the remote control work ?
thx

After installing lirc I could use the basic functions of the remote control without any other changes or setup (Dapper!). Great!

Friedrich

---

