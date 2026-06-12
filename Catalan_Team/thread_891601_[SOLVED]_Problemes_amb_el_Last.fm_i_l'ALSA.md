---
title: "[SOLVED] Problemes amb el Last.fm i l'ALSA"
date: 2008-08-16
forum: Catalan Team
---

### Post by premianenca on 2008-08-16
A veure si em podeu donar un cop de mà, reuslta que quan vaig passar-me a l'Ubuntu vaig instal·lar el software del Last.fm però sempre que l'obria em deia "El sistema de reproducció ALSA no existeix o no està en execució".

 

He estat mirant diverses webs, fòrums i tota la pesca, però cap de les coses que s'hi deien m'ha funcionat.

 

Algun usuari del Last des de l'Ubuntu em podria donar un cop de mà?

---

### Post by LitusMayol on 2008-08-16
Què vols dir? Que no et transmet les teves reproduccions al **Last.fm**?

Jo tinc un usuari, [LitusMayol]("www.last.fm/user/LitusMayol") (sóc original amb el pseudònims, eh! xD) i a mi em transmet bé. 

Vaig tenir el mateix problema que tu al principi. No t'has de baixar el seu software. Fes servir el **Rythmbox**( assumeixo que tens **Ubuntu**, si tens **Kubuntu** usa l'**Amarok**) i vés a "*Edita > Connectors*". Busca el connector "*Last.fm*" i prem a "*Configura*". Et demanara el nom d'usuari i la contrasenya, un cop hagis activat el connector, cada vegada que escoltis música amb el **Rythmbox** la transmetrà al **Last.fm** (això si, a vegades pot tardar i enlloc d'enviar-les al moment les envia quan en té 5 o 6 en cua).


Proba-ho!

---

### Post by premianenca on 2008-08-17
Sí, tinc Ubuntu i utilitzo el Rythmbox, però les indicacions que m'has donat no em serveixen ja que em dóna el mateix error que al principi.

---

### Post by patrickfromspain on 2008-08-17
Prova a entrar al Last fm, i sota Tools -> Options, busca radio i alla prova a canviar la tarja de so.

Salut

---

### Post by premianenca on 2008-08-17
Res, segueix donant-me error...

---

### Post by lo gambusí on 2008-08-17
jo a tu te conec... xD

---

### Post by CarlesOriol on 2008-08-17
pasuspender -- lastfm

---

### Post by used-to-be-s-man on 2008-08-18
Hola, a mi em pasa exactament el mateix, buscant informació he trobat un forum ( [http://ubuntuforums.org/showthread.php?t=676590](http://ubuntuforums.org/showthread.php?t=676590) ) on es diu que tancant tot i després posant a la consola:"sudo /etc/init.d/alsa-utils reset" tornes a obrir last.fm i llavors funciona, però no podràs escoltar res més. És a dir, pel que jo he entés (i no en tinc un nivell d'anglès gaire bo xDDD) lasst.fm fa us de tot el ALSA, per tant o escoltas com sempre... tot (es a dir, amarok... youtube... goear... el que sigui) o escoltes last.fm.... la cual cosa... no mola

A veure si a partir d'aquest fil que he linkat algú ens sap donar una solució :(

Salut a tothom!!!!

---

### Post by premianenca on 2008-08-18
Res, segueix-ho igual.:(

---

### Post by LitusMayol on 2008-08-18
Jo em sembla que m'he perdut.

Què és el que no et va? No transmet cançons al **Last.fm** o bé no pots reproduir la ràdio (sigui quina sigui). 


Si és le primer cas... no ho sé. Jo ja t'he dit abans que hauria fet, però en vista de que no ha funcionat... No se m'acut com arreglar-ho. Ho sento.


Si és el segon... Has probat d'escoltar la radio a travès del web en lloc de usant el seu software? A mi el software no m'ha funcionat mai. I el web sempre l'he utilitzat, que si *My Recommendations*, *My Radio*, *Tag's Radio*...


Apa, ànims que entre tots algú en treurà l'entrellat!

---

### Post by premianenca on 2008-08-18
Bé, ja ho he arreglat! Gràcies a en LitusMayol! El que m'havia dit està bé, el que passa és que no havia fet una cosa bé!


Gràcies a tots!

---

### Post by papapep on 2008-08-18
Què t'ha funcionat en concret?? explica-ho bé i així si algú altre s'hi troba ho tindrà fàcil per arreglar-ho ;-)

---

