---
title: "Configurar TV-LCD via DVI a Ubuntu"
date: 2008-09-15
forum: Catalan Team
---

### Post by gcarles on 2008-09-15
Hola. Sóc nou i espero poder compartir problemes i solucions.

Pretenc connectar una TV LCD via DVI-HDMI a l'ubuntu. Tinc una nVidia. Tocant el xorg.conf (manualment i amb el nvidia-settings) he aconseguit configurar-ho per tal de veure dos monitors amb escriptori extès, que vegi resolucions diferents, etc. El que no aconsegueixo del tot és deixar la TV amb DVI com a monitor principal (veure-hi allà la pantalla de login).

Si reinicio el pc connectant NOMES la sortida VGA, es carreguen les X normalment. Si després desconnecto el cable VGA i connecto el DVI, i llavors reinicio les X, va bé. Ara bé, si engego el PC amb la sortida DVI no es veu res. Clar, a mi m'agradaria deixar només la tele amb DVI. Hi ha algun procés que detecta els monitors que funciona a part del xorg.conf?

També em passa que si està funcionant correctament i amb el comandament de la TV canvio d'entrada i torno a la entrada HDMI llavors no es veu res i haig de reiniciar les X per recuperar el senyal. Pot ser que es perdi la sincronia d'alguna manera?

Sabeu perquè pot ser?

Moltes gràcies.
Salut!

---

### Post by SiscoGarcia on 2008-09-15
Hola gcarles, benvingut/da al fòrum (per cert, passat pel [fil de benvinguda]("http://ubuntuforums.org/showthread.php?t=562776") i pel d'instruccions de [funcionament del fòrum]("http://ubuntuforums.org/showthread.php?t=599965"))!

Sento no poder donar-te la solució que esperes, però a canvi et diré que vagis amb compte amb les connexions d'aquest tipus [hdmi]("http://es.wikipedia.org/wiki/High-Definition_Multimedia_Interface") perquè són [sistemes de restricció digital]("http://ca.wikipedia.org/wiki/DRM") ([DRM]("http://www.defectivebydesign.org/") en anglès) que a la llarga et portaran més problemes que alegries, ja que és tot el contrari a l'[esperit lliure]("http://www.fsfeurope.org/documents/freesoftware.ca.html") que plana sobre [GNU]("http://www.fsfeurope.org/documents/gnuproject.ca.html")/Linux-ubuntu i el programari lliure en general. Vull dir que se'm fa una mica contradictori voler fer anar ubuntu amb sistemes DRM, però potser només és la meua opinió :confused:

Després d'aquest totxo espero haver ajudat a aclarir conceptes, tot i que potser no és el que esperaves trobar ;)

---

### Post by gcarles on 2008-09-16
Gràcies. Sí, ja havia visitat la "benvinguda", ja intentaré ser "eficaç".

Bé, la meva motivació és per tal de veure resolució a 1920x1080, que sí que aconsegueixo amb la connexió dvi-hdmi. Però no dec comprendre del tot com funciona el tema ja que no aconsegueixo fer-ho anar normalment (haig d'aixecar-me del sofà i fer el "vall" de cables cada vegada). El meu muntatge pretén ser media-center, per això vull la TV i sense monitor.

Gràcies de nou. Seguiré provant...

---

