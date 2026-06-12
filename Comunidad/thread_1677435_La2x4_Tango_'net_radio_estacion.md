---
title: "La2x4 Tango 'net radio estacion"
date: 2011-01-28
forum: Comunidad
---

### Post by Mark_in_Hollywood on 2011-01-28
Natty (v. 11.04) no jugará esta estación de radio por Internet en
Buenos Aires. [http://www.la2x4.gov.ar/](http://www.la2x4.gov.ar/) otra URL para este 
es [http://www.la2x4.gov.ar/index.swf](http://www.la2x4.gov.ar/index.swf). 

Por favor, amable, Buenos Aireseños, en contacto con esta ciudad de BA 
estación y pedirles que para mí, un niño blanco en el Estados 
Unidos, para hacer su estación compatible con Linux.


Pido disculpas por el mal castellano

---

### Post by juancarlospaco on 2011-01-29
It seems the streaming is not working, at least at the moment, i try with VLC and the URL dont respond:

```

juan@wind:~$** cvlc mms://2x4.telecomdatacenter.com.ar/2x4**
VLC media player 1.1.5 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0xa06668c] dummy interface: using the dummy interface module...
[0xa06d234] main access error: connection failed: Connection refused
[0xa06d234] access_mms access error: failed to open a connection (tcp)
[0xa06d234] main access error: connection failed: Connection refused
[0xa06d234] access_mms access error: failed to open a connection (tcp)
[0xa06d234] access_mms access error: cannot connect to server
[0xa06d234] main access error: Read error: Connection reset by peer
[0xa06d234] access_mms access error: failed to read answer
[0xb730065c] main input error: open of `mms://2x4.telecomdatacenter.com.ar/2x4' failed: (null)
[0xb730065c] main input error: Your input can't be opened

juan@wind:~$ ping 2x4.telecomdatacenter.com.ar
PING 2x4.telecomdatacenter.com.ar (200.82.126.78) 56(84) bytes of data.
^C
--- 2x4.telecomdatacenter.com.ar ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4000ms

```

The website is Flash based which is bad and annoying, 
but the streaming should work without Adobe Flash,
try to run this on the command line on your own PC:

```
xdg-open mms://2x4.telecomdatacenter.com.ar/2x4
```

Maybe works, maybe not; it didn't worked for me...
good luck!     ^_^

---

### Post by Mark_in_Hollywood on 2011-01-31
Thanks for your reply in English. 

I tried the radio station over the weekend, again. It was working fine in Windows. I tried it this morning in Linux and Movie Player gave the "an error occurred" message.

---

### Post by mama21mama on 2011-01-31
así parece no conecta:

```
mplayer mms://2x4.telecomdatacenter.com.ar/2x4/.wma?MSWMExt=.asf
```
```

mplayer mms://200.82.126.78/2x4/.wma?MSWMExt=.asf
```

---

### Post by Mark_in_Hollywood on 2011-02-03
Por favor, also persona contacta lo:

La2x4
FM 92.7

Sarmiento 151, piso 8 (C1042ABC)
Buenos Aires

Tel 54+11 5371-4646

I tried calling them and asking about whether they block Linux users, but there was no answer. 

Also, I cannot pull up their email address from the contacts page, although in the past, I have emailed about the problem.

Thank you for your time. I wouldn't keep asking for help with this, but they do have the best tango music on the 'net.

---

### Post by rikz10 on 2011-03-20
The internet radio 'la 2x4 (mms://2x4.telecomdatacenter.com.ar/2x4 ) works fine in windows, even using other streaming player different from WMP.  The problem is only with linux players (VLC, totem, rymthmbox, mplayer are the ones I've tried unsusccesfully). I wrote an email to the radio broadcast in Buenos Aires, and I received no replay at all.  In my email I also said that 'la2x4 sister radio, called 'radiociudad  (mms://radiociudad.telecomdatacenter.com.ar/radiociudad) generaly worked under Ubuntu.  So the problem is only with 'la 2x4 streaming. Both radios transmit using the same stream server, and both belongs to the City of Buenos Aires's goverment administration. Perhaps, If all 'la 2x4 listeners who use Linux could joint together, to ask the radio authorities a less restrictived treat for Linux users  I agree with Mark_in_Hollywood, they have the best tango music on the net. Best regards for all tango fans all around the world!

---

### Post by Mark_in_Hollywood on 2011-07-21
Banshee runs this without problem. So it's goodbye to VLC and Totem Movie for this.

---

### Post by renzoe on 2012-01-23
> **Mark_in_Hollywood said:**
> Banshee runs this without problem. So it's goodbye to VLC and Totem Movie for this.

Good morning, can anyone confirm this?
I have ubuntu 11.10 and banshee 2.2.1 and it's not working.

Greetz

---

### Post by Mark_in_Hollywood on 2012-02-06
Once again, La2x4 has moved it's Flash to work with Microsoft only. So, La2x4 is as tonto as Tango music is bellissima.

My Banshee shows the buffering stuck at 42%.

---

### Post by renzoe on 2012-02-08
> **Mark_in_Hollywood said:**
> Once again, La2x4 has moved it's Flash to work with Microsoft only. So, La2x4 is as tonto as Tango music is bellissima.

My Banshee shows the buffering stuck at 42%.

:( So sad.. I'm from Buenos Aires and used to listen the radio all day, I'm since 2 months in France, and I miss it too much.

I've never managed to make it work through Banshee though.

---

### Post by kindadarko on 2012-05-03
Español ---> Hola! tengo ubuntu lucid y tuve el mismo problema desde hace mas de un año, traté con banshee (y muchísimas otras opciones](*,)) y no funcionó para mí así que hoy hice trampa y estoy usando winamp v5.6233 a través de wine :sad: funciona horriblemente y tiene un par de problemas... PERO reproduce la 2x4 perfectamente  \\:D/  (mms://2x4.telecomdatacenter.com.ar/2x4), acabo de instalarlo usando sólo lo básico (no librería multimedia, pieles clásicas, etc). El verdadero problema es con la estación de radio que no permite linux, pude escuchar perfectamente muchísimas otras radios simplemente con mi ubuntu sin ningún problema y es verdaderamente enfermizo tener que instalar un programa en wine solamente por una simple estación de radio...

English ---> Hi! i've got ubuntu lucid and had the same problem since a year ago, i've tried banshee (and a lot more of optins ](*,)) and it didn't work for me so today i've cheated and i'm using winamp v5.6233 under wine :( it works awfully and it has some troubles... BUT it is playing La 2x4 perfectly \\:D/  (mms://2x4.telecomdatacenter.com.ar/2x4), i've just installed it with only the basic settings (no media library, classic skins, etc). The real problem is with this radio station that doesn't allows linux, i have listened perfectly a bunch of other radios with my ubuntu without trouble and it is really disgusting to have to install a program under wine just because of a single radio station...

---

### Post by renzoe on 2012-05-09
Thank you very much! Installing Winamp on Wine works :). Its a shame we have to do this but seems to be the only way on linux. I had ubuntu 11.10 32 bits and istalled the wine 1.2 (I had problems with the wine 1.3 beta), the winamp I installed through the "winetricks" app. As Kindarako said try to instally the basic -though I think I installled media library :s-. Long live Tango

Muchas Gracias!!

---

### Post by Mark_in_Hollywood on 2012-05-11
While I am GUESSING about this, it seems to me that La2x4 uses the latest Flash every chance they get. This breaks in Linux as we don't bother with Flash like Mr. Gates does. My Banshee is working as of 11-May-2012. 

I'm very happy to hear about the wine/winamp solution, however.

---

### Post by El Potro on 2012-05-12
Hola Mark,

no sé si estudiás español o sólo te gusta el tango. De todos modos te dejo una lista de radios online actualizada al 2012.

En las radios AM, a la madrugada (de Argentina) podés encontrarte generalmente con tangos, especialmente en algunas, como por ejemplo Splendid.

Que lo disfrutes pebete.

```
RADIOS ONLINE 2012

530 AM La Voz ...

http://200.68.81.65:8000/am530



550 AM Colonia

http://wmserver3.aginet.com.ar:19043



570 AM Argentina

http://am570.prodera.com.ar:8000



590 AM Continental

http://69.31.54.135/CONTINENTAL?streamtheworld_user=1&nobuf=1329884727000



630 AM Rivadavia

http://streamer5.towebs.com:56661/rivadavia.mp3



650 AM Reporter Belgrano

http://wmserver3.aginet.com.ar/AM650



690 AM K24 en Radio

rtmp://live_1H_2609171



710 AM Radio 10

http://www.radio10.am:8000/radio10.mp3



740 AM Rebelde

http://207.210.120.98:12040/;stream.nsv/;



750 AM AM750

http://vivo.radioam750.com.ar:8000/vivo.mp3



770 AM Cooperativa

http://streaming2.uosolutions.com:5000/;stream.nsv/;



790 AM Mitre

http://crp02d.cienradios.com.ar/Mitre790.mp3



830 AM Del Pueblo

rtmp://live_1_2825796



840 AM Gral Belgrano

http://www.streaming.siliconmediatech.com/am840/stream.asx



870 AM Nacional

http://208.85.241.150:8010/;stream.nsv/;



890 AM Libre

http://streamall.alsolnet.com/am890



910 AM La Red

rtmp://lared_3046437



950 AM 9 La Deportiva

http://mfile.akamai.com/123447/live/reflector:22236.asx?bkup



990 AM Splendid

http://pwstreaming.net:8616/;stream.nsv



1010 AM Onda Latina

rtmp://live_1H_3140625



1030 AM Del Plata

http://delplata.telecomdatacenter.com.ar/delplata



1050 AM Concepto

http://190.220.149.204:1267



1070 AM El Mundo

http://85.17.45.87:8470/vivo



1090 AM Popular

-



1110 AM De la Ciudad

http://radiociudad.telecomdatacenter.com.ar/radiociudad



1120 AM Tango

http://174.142.97.121/am1120



1190 AM América

http://wms1.streaming.redynet.com.ar/amamerica_22



1220 AM Cadena Eco

http://wmserver3.aginet.com.ar/CE1220



1230 AM Creativa

http://streaming.siliconmediatech.com/am1230/stream.asx



1240 AM Cadena Uno

http://streamair.alsolnet.com:8080/cadenauno1240



1260 AM Oliva

rtmp://live_1H_3632515



1280 AM RP Punto

rtmp://live_1H_3740421



1300 AM Identidad

http://streamair.alsolnet.com:8080/radioidentidadvideo



1310 AM AM 1310

rtmp://live_1H_3883265



1350 AM Buenos Aires

http://streamair.alsolnet.com:8080/radiobuenosaires



1530 AM Eco Porteña

http://wmserver3.aginet.com.ar/CE1280



1540 AM Amanecer

http://200.80.36.148:8050/;stream.nsv/;



1550 AM Urkupiña

rtmp://live_1H_4060578



1640 AM Bolivia

http://us12.toservers.com:8188/



1670 AM Basilio

http://www.alsolnet.com/stream/am1670/listen.asx



1710 AM AM 1710

-



Radios FM




87.5 FM Soldados

http://wmserver3.aginet.com.ar/FMSOLDADOS



87.9 FM UBA

http://radiouba.telecomdatacenter.com.ar/radiouba



88.1 FM Bajo Flores

rtmp://live_1H_7899343



88.1 FM Gospel

http://74.208.46.125/fmgospel1



88.3 FM Boedo

rtmp://live_1H_7987156



88.3 FM Eco Argentina

-



88.3 FM Mundo Latino

http://www.mundolatinofm883.com.ar/playradio.asx



88.3 FM Sur

http://giss.tv:8000/radiosur1027.mp3



88.5 FM Maria

http://www.radiomaria.org/media/argentina.asx



88.7 FM La Tribu

http://vivo.fmlatribu.com:8000/latribu.mp3



89.3 FM Gráfica

-



89.3 FM Sensitive

http://200.68.70.249:9000/;stream.nsv/;



90.1 FM La Boca

rtmp://liveH_8471578



90.1 FM FM90 Devoto

http://87.98.219.31:2544/;stream.nsv



90.3 FM Delta

http://208.80.54.77/DELTA_903?streamtheworld_user=1&nobuf=1330093980718



90.7 FM Flores

http://streaming.siliconmediatech.com/fmflores/stream.asx



90.9 FM Centro

http://unicast.vdo3.com/radiolive_RadioCentro



90.9 FM Univ Belgrano

http://streaming.radiolinks.com.ar:8108/;stream.nsv/;



90.9 FM Eco FM

-



91.3 FM Resurrección

-



91.7 FM Urquiza

http://www.fmurquiza.com/fmurquiza.asx



91.9 FM Fantastico

-



92.1 FM Identidad

http://fmidentidad.telecomdatacenter.com.ar/fmidentidad



92.3 FM La Radio

http://nexolife.com/astream/laradio923/listen.asx



92.5 FM Frecuencia Zero

http://cdigitalip.com.ar:8016/;stream.nsv/;



92.7 FM La 2x4

http://2x4.telecomdatacenter.com.ar/2x4



93.1 FM Late

http://late.radiolinks.com.ar:8052/;stream.nsv/;



93.5 FM Dilecta

http://streamingargentino1.com.ar:7124/



93.7 FM Rock

http://208.85.241.150:8162/;stream.nsv/;



93.9 FM Palermo

http://200.42.92.40/Palermo_1.mp3



94.3 FM Disney

rtmp://LATAM_Radio_Disney@58472_9101296



94.7 FM Palermo

http://200.42.92.40/Palermo_2.mp3



95.1 FM Metro

http://streaming.metro951.com/metro



95.5 FM ISER

http://streaming.localhost.net.ar:8002



95.5 FM Patricios

http://clients.serverstreamgroup.net:15056/



95.9 FM Rock & Pop

http://streaming.fmrockandpop.com/rockandpop



96.3 FM Jai

http://www.radiojai.com.ar/online/vivo/vivojai2.asx



96.5 FM Azul

http://radio.solumedia.com.ar:8028/;stream.nsv/;



96.7 FM Clásica

http://208.85.241.150:8154/;stream.nsv/;



96.9 FM Master

rtmp://live_1H_9392890



97.3 FM Inca

http://76.73.20.18:7050/;stream.nsv/;



97.5 FM Vale

http://200.43.193.190/vale



97.9 FM Cultura

http://50.30.46.200:8686/;stream.nsv/;



98.3 FM Mega

http://200.43.193.190/mega



98.7 FM RNA Folklorica

http://208.85.241.150:8158/;stream.nsv/;



99.1 FM Cadena 3

http://am700.telecomdatacenter.com.ar/am700



99.3 FM Libre

http://www.radiolibre.org.ar:8000/;stream.nsv/;



99.5 FM Federal

http://174.36.1.34:8038/;stream.nsv/;



99.9 FM La 100

http://crp02d.cienradios.com.ar/la100.mp3



100.1 FM La Colifata

-



100.3 FM Amadeus Cult Mus

http://50.30.46.200:8484/;stream.nsv/;



100.7 FM Blue

http://streaming.bluefm.com.ar/blue



100.9 FM Riachuelo

rtmp://live_1H_9732500



101.1 FM Latina

http://200.115.194.1:8080/RadioLatina



101.5 FM Pop Radio

http://200.43.193.190/popradio



101.9 FM KSK Radio

http://radios.fibertel.com.ar/kskradio



102.3 FM Aspen

http://200.89.168.16/aspen



102.5 FM La Colectiva

http://200.20.113.50:8000/lacolectiva.ogg



102.7 FM Belgrano

-



102.7 FM Pasión

-



102.9 FM Rhema

http://miradioenlaweb.com:5030/;stream.nsv/;



103.1 FM Vorterix Rock

rtmp://vorterix_10163484



103.7 FM TKM

http://200.43.193.190/radiotkm



104.1 FM LVG

http://giss.tv:8000/lvg.mp3.m3u



104.1 FM Station

http://www.station104.com.ar/pgm/radio.asx



104.3 FM Imagina

http://63.243.143.155/IMAGINA_ARGENTINA?streamtheworld_user=1&nobuf=1330095665187



104.7 FM Dakota

http://www.alsolnet.com/stream/fmdakota/vivo.asx



105.1 FM Parroquial

http://www.fmparroquial.com.ar/radio.asx



105.5 FM 40 Principales

http://69.31.54.140/LOS40_ARGENTINA?streamtheworld_user=1&nobuf=1330095739750



105.9 FM PQV Parque Vida

rtmp://liveH_10479109



106.3 FM Red Aleluya

http://streamair.alsolnet.com:8080/alfafm



106.5 FM Ecos Latinos

rtmp://jtv__gUbHkZZKHUXqWFt_10567734



106.7 FM Milenium

http://milenium.telecomdatacenter.com.ar/milenium



107.9 FM ESPN

mms://a183.l1318236841.c13182.l.lm.akamaistream.net/D/183/13182/v0001/reflector:36841
```

---

### Post by geoaraujo on 2012-05-12
> **El Potro said:**
> Hola Mark,

no sé si estudiás español o sólo te gusta el tango. De todos modos te dejo una lista de radios online actualizada al 2012.

En las radios AM, a la madrugada (de Argentina) podés encontrarte generalmente con tangos, especialmente en algunas, como por ejemplo Splendid.

Que lo disfrutes pebete.

```
RADIOS ONLINE 2012

530 AM La Voz ...

http://200.68.81.65:8000/am530



550 AM Colonia

http://wmserver3.aginet.com.ar:19043



570 AM Argentina

http://am570.prodera.com.ar:8000



590 AM Continental

http://69.31.54.135/CONTINENTAL?streamtheworld_user=1&nobuf=1329884727000



630 AM Rivadavia

http://streamer5.towebs.com:56661/rivadavia.mp3



650 AM Reporter Belgrano

http://wmserver3.aginet.com.ar/AM650



690 AM K24 en Radio

rtmp://live_1H_2609171



710 AM Radio 10

http://www.radio10.am:8000/radio10.mp3



740 AM Rebelde

http://207.210.120.98:12040/;stream.nsv/;



750 AM AM750

http://vivo.radioam750.com.ar:8000/vivo.mp3



770 AM Cooperativa

http://streaming2.uosolutions.com:5000/;stream.nsv/;



790 AM Mitre

http://crp02d.cienradios.com.ar/Mitre790.mp3



830 AM Del Pueblo

rtmp://live_1_2825796



840 AM Gral Belgrano

http://www.streaming.siliconmediatech.com/am840/stream.asx



870 AM Nacional

http://208.85.241.150:8010/;stream.nsv/;



890 AM Libre

http://streamall.alsolnet.com/am890



910 AM La Red

rtmp://lared_3046437



950 AM 9 La Deportiva

http://mfile.akamai.com/123447/live/reflector:22236.asx?bkup



990 AM Splendid

http://pwstreaming.net:8616/;stream.nsv



1010 AM Onda Latina

rtmp://live_1H_3140625



1030 AM Del Plata

http://delplata.telecomdatacenter.com.ar/delplata



1050 AM Concepto

http://190.220.149.204:1267



1070 AM El Mundo

http://85.17.45.87:8470/vivo



1090 AM Popular

-



1110 AM De la Ciudad

http://radiociudad.telecomdatacenter.com.ar/radiociudad



1120 AM Tango

http://174.142.97.121/am1120



1190 AM América

http://wms1.streaming.redynet.com.ar/amamerica_22



1220 AM Cadena Eco

http://wmserver3.aginet.com.ar/CE1220



1230 AM Creativa

http://streaming.siliconmediatech.com/am1230/stream.asx



1240 AM Cadena Uno

http://streamair.alsolnet.com:8080/cadenauno1240



1260 AM Oliva

rtmp://live_1H_3632515



1280 AM RP Punto

rtmp://live_1H_3740421



1300 AM Identidad

http://streamair.alsolnet.com:8080/radioidentidadvideo



1310 AM AM 1310

rtmp://live_1H_3883265



1350 AM Buenos Aires

http://streamair.alsolnet.com:8080/radiobuenosaires



1530 AM Eco Porteña

http://wmserver3.aginet.com.ar/CE1280



1540 AM Amanecer

http://200.80.36.148:8050/;stream.nsv/;



1550 AM Urkupiña

rtmp://live_1H_4060578



1640 AM Bolivia

http://us12.toservers.com:8188/



1670 AM Basilio

http://www.alsolnet.com/stream/am1670/listen.asx



1710 AM AM 1710

-



Radios FM




87.5 FM Soldados

http://wmserver3.aginet.com.ar/FMSOLDADOS



87.9 FM UBA

http://radiouba.telecomdatacenter.com.ar/radiouba



88.1 FM Bajo Flores

rtmp://live_1H_7899343



88.1 FM Gospel

http://74.208.46.125/fmgospel1



88.3 FM Boedo

rtmp://live_1H_7987156



88.3 FM Eco Argentina

-



88.3 FM Mundo Latino

http://www.mundolatinofm883.com.ar/playradio.asx



88.3 FM Sur

http://giss.tv:8000/radiosur1027.mp3



88.5 FM Maria

http://www.radiomaria.org/media/argentina.asx



88.7 FM La Tribu

http://vivo.fmlatribu.com:8000/latribu.mp3



89.3 FM Gráfica

-



89.3 FM Sensitive

http://200.68.70.249:9000/;stream.nsv/;



90.1 FM La Boca

rtmp://liveH_8471578



90.1 FM FM90 Devoto

http://87.98.219.31:2544/;stream.nsv



90.3 FM Delta

http://208.80.54.77/DELTA_903?streamtheworld_user=1&nobuf=1330093980718



90.7 FM Flores

http://streaming.siliconmediatech.com/fmflores/stream.asx



90.9 FM Centro

http://unicast.vdo3.com/radiolive_RadioCentro



90.9 FM Univ Belgrano

http://streaming.radiolinks.com.ar:8108/;stream.nsv/;



90.9 FM Eco FM

-



91.3 FM Resurrección

-



91.7 FM Urquiza

http://www.fmurquiza.com/fmurquiza.asx



91.9 FM Fantastico

-



92.1 FM Identidad

http://fmidentidad.telecomdatacenter.com.ar/fmidentidad



92.3 FM La Radio

http://nexolife.com/astream/laradio923/listen.asx



92.5 FM Frecuencia Zero

http://cdigitalip.com.ar:8016/;stream.nsv/;



92.7 FM La 2x4

http://2x4.telecomdatacenter.com.ar/2x4



93.1 FM Late

http://late.radiolinks.com.ar:8052/;stream.nsv/;



93.5 FM Dilecta

http://streamingargentino1.com.ar:7124/



93.7 FM Rock

http://208.85.241.150:8162/;stream.nsv/;



93.9 FM Palermo

http://200.42.92.40/Palermo_1.mp3



94.3 FM Disney

rtmp://LATAM_Radio_Disney@58472_9101296



94.7 FM Palermo

http://200.42.92.40/Palermo_2.mp3



95.1 FM Metro

http://streaming.metro951.com/metro



95.5 FM ISER

http://streaming.localhost.net.ar:8002



95.5 FM Patricios

http://clients.serverstreamgroup.net:15056/



95.9 FM Rock & Pop

http://streaming.fmrockandpop.com/rockandpop



96.3 FM Jai

http://www.radiojai.com.ar/online/vivo/vivojai2.asx



96.5 FM Azul

http://radio.solumedia.com.ar:8028/;stream.nsv/;



96.7 FM Clásica

http://208.85.241.150:8154/;stream.nsv/;



96.9 FM Master

rtmp://live_1H_9392890



97.3 FM Inca

http://76.73.20.18:7050/;stream.nsv/;



97.5 FM Vale

http://200.43.193.190/vale



97.9 FM Cultura

http://50.30.46.200:8686/;stream.nsv/;



98.3 FM Mega

http://200.43.193.190/mega



98.7 FM RNA Folklorica

http://208.85.241.150:8158/;stream.nsv/;



99.1 FM Cadena 3

http://am700.telecomdatacenter.com.ar/am700



99.3 FM Libre

http://www.radiolibre.org.ar:8000/;stream.nsv/;



99.5 FM Federal

http://174.36.1.34:8038/;stream.nsv/;



99.9 FM La 100

http://crp02d.cienradios.com.ar/la100.mp3



100.1 FM La Colifata

-



100.3 FM Amadeus Cult Mus

http://50.30.46.200:8484/;stream.nsv/;



100.7 FM Blue

http://streaming.bluefm.com.ar/blue



100.9 FM Riachuelo

rtmp://live_1H_9732500



101.1 FM Latina

http://200.115.194.1:8080/RadioLatina



101.5 FM Pop Radio

http://200.43.193.190/popradio



101.9 FM KSK Radio

http://radios.fibertel.com.ar/kskradio



102.3 FM Aspen

http://200.89.168.16/aspen



102.5 FM La Colectiva

http://200.20.113.50:8000/lacolectiva.ogg



102.7 FM Belgrano

-



102.7 FM Pasión

-



102.9 FM Rhema

http://miradioenlaweb.com:5030/;stream.nsv/;



103.1 FM Vorterix Rock

rtmp://vorterix_10163484



103.7 FM TKM

http://200.43.193.190/radiotkm



104.1 FM LVG

http://giss.tv:8000/lvg.mp3.m3u



104.1 FM Station

http://www.station104.com.ar/pgm/radio.asx



104.3 FM Imagina

http://63.243.143.155/IMAGINA_ARGENTINA?streamtheworld_user=1&nobuf=1330095665187



104.7 FM Dakota

http://www.alsolnet.com/stream/fmdakota/vivo.asx



105.1 FM Parroquial

http://www.fmparroquial.com.ar/radio.asx



105.5 FM 40 Principales

http://69.31.54.140/LOS40_ARGENTINA?streamtheworld_user=1&nobuf=1330095739750



105.9 FM PQV Parque Vida

rtmp://liveH_10479109



106.3 FM Red Aleluya

http://streamair.alsolnet.com:8080/alfafm



106.5 FM Ecos Latinos

rtmp://jtv__gUbHkZZKHUXqWFt_10567734



106.7 FM Milenium

http://milenium.telecomdatacenter.com.ar/milenium



107.9 FM ESPN

mms://a183.l1318236841.c13182.l.lm.akamaistream.net/D/183/13182/v0001/reflector:36841
```

Hola! Les dejo el link de Radio Clarín por si acaso. Siempre tango y música folclórica rioplatense.
[http://www.radioclarin.com/audio/directo.m3u](http://www.radioclarin.com/audio/directo.m3u)
Saludos!

---

### Post by Mark_in_Hollywood on 2012-05-16
Por El Potro:

yo dar las gracias por esto infos.

---

### Post by Mark_in_Hollywood on 2012-05-18
La 2X4 now has a Facebook presence at:

[http://www.facebook.com/pages/LA-2X4-FM-927/236245953091984](http://www.facebook.com/pages/LA-2X4-FM-927/236245953091984)

if you "Like" them you can post questions or complaints about not being able to receive the station's music stream. You must have joined Facebook to post at that page. But unlike the radio stations email address or web based email, maybe we can get a response from Buenos Aires. I tried calling the phone number they give, but it's a recorded message and my fluency in Spanish isn't that good.

They have a Twitter icon as well but I couldn't find a way to follow them.

---

### Post by renzoe on 2012-11-16
As of today (16 NOV 2012), la 2x4 [http://www.la2x4.gov.ar/](http://www.la2x4.gov.ar/) is working on the webstream :)
I'm using an Ubuntu 12.04, it loads with VLC player on the browser.

Saludos

---

### Post by Mark_in_Hollywood on 2012-11-16
I concur. I am streaming 16-Nov-2012. This is 12.04 Precise Pangolin and VLC media player 2.0.3 Twoflower.

---

