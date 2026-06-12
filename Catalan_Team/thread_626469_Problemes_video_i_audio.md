---
title: "Problemes video i audio"
date: 2007-11-29
forum: Catalan Team
---

### Post by antiheroes on 2007-11-29
Tenc un problema quan intent reproduir audio amb Ubuntu 7.10. Amb qualsevol reproductor** em deixa reproduir una cançó, i a la següent es penja el programa** (en aquest cas Exaile).

També em passa** el mateix amb video**. Per exemple, puc veure un video a Youtube, però al segon vídeo que intent mirar es penja es navegador (Firefox).

Ja he provat de formatetjar, reinstalar... però no he trobat la solució

_He obert es reproductor amb la consola, a me'm si sabeu de quina errada es tracta i com es pot solucionar:_

[I]antiheroes@antiheroes-laptop:~$ exaile
Created db for thread Thread-1
{'Thread-1': <sqlite3.Connection object at 0x89dc278>}
Closed db for thread Thread-1
Using multimedia keys from: gnome
loading tracks...
done loading tracks...
loading songs
Clearing tracks cache
Importing /home/antiheroes/.exaile/saved/playlist0000.m3u
/usr/share/exaile/xl/trackslist.py:125: GtkWarning: gdk_pixbuf_copy_area: assertion `src_x >= 0 && src_x + width <= src_pixbuf->width' failed
  star.copy_area(0, 0, star_size, star_size, full_image, star_size * x, 0)
Last playlist loaded
Loading page 0
sh: jackd: not found
sh: jackd: not found
Terminado (killed)[/I]

**Agrairia qualsevol tipus de suggerència...** Aquest problema em desespera!

Gràcies!

---

### Post by CarlesOriol on 2007-11-29
Quina versió d'ubuntu tens? És un ubuntustudio?? És molt extrany usar el dimoni jackd sols per escoltar música.

---

### Post by antiheroes on 2007-11-30
Us ubuntu 7.10 amb escriptori Gnome... saps alguna solució per aquest problema. He tornat formatejar, però me tornarà a passar. Per favor si saps qualque cosa per intentar arreglar-ho m'ho dius... Gràcies!

---

### Post by papapep on 2007-11-30
Tingues present que aquest no és el comportament normal de la 7.10, per tant, reinstal·la-la i si et trobes amb problemes ja mirarem com solucionar-ho.

---

### Post by antiheroes on 2007-11-30
ja he reinsta·lat tot, però supòs que em tornarà a donar problemes, si sabeu qualque solució anticipada o a que es deu això m'ho podrieu posar aquí. El que no sé es a que es refereix amb ubuntustudio en Carles...

---

### Post by papapep on 2007-11-30
L'ubuntustudio és una versió de Ubuntu específica per a tractar audio i video. Fes un cop d'ull aquí: [https://wiki.ubuntu.com/JosepS%c3%a0nchez/documentaci%c3%b3/Versions_Ubuntu](https://wiki.ubuntu.com/JosepS%c3%a0nchez/documentaci%c3%b3/Versions_Ubuntu)

Respecte el tema de "preveure" problemes, és com si anessis al metge a demanar-li que et recepti medicines sense estar malalt en previsió del que puguis agafar...no funcionaria gaire bé :-D

---

### Post by antiheroes on 2007-11-30
Crec que ja he trobat sa solució en es problema. He anat al synaptic y he posat jackd i m'ha sortit un paquet per instalar... si no me va bé provaré amb això... ja veurem. No tancaré això per si un cas no va bé... gràcies!

---

### Post by papapep on 2007-11-30
Però tens clar que et faci falta el jackd??? Se t'ha tornat a presentar el mateix problema??

---

### Post by antiheroes on 2007-11-30
Ara per ara no s'ha tornat presentar perquè vaig formatejar ahir. Si es torna a presentar aquest problema instalaré el jackd a me'm si es soluciona. Si no us demanaré consell una altra vegada.

---

### Post by papapep on 2007-11-30
Jo t'aconsello que no facis res sense preguntar (a no ser que sàpigues el que fas...). Recorda que això no és el sistema operatiu del que, suposo, que provens.

---

### Post by antiheroes on 2007-11-30
ok, idò si me sorgeix el problema vos demanaré. Supòs que sorgirà d'aquí un parell de dies... esperem que no!

---

### Post by antiheroes on 2007-11-30
ok! idò vos demanaré! Supòs que sorgirà el problema d'aquí un parell de dies! Esperem que no!

---

### Post by CarlesOriol on 2007-11-30
no............................. no insta&#320;lis el jackd. A mi em va extranyar que tinguessis un programa que el cerques.

---

### Post by antiheroes on 2007-12-01
Eis! Per ara això no me dona problemes... Si me em torna a passar vos ho comunicaré aquí o obriré un altre foro!

---

### Post by orestesmas on 2007-12-01
Home, no espantis a la gent, que experimentar, carregar-te el S.O. 50 vegades, reinstal·lar, etc., és bonic. Una de les gràcies de GNU/Linux és que en el procés aprens moltes coses, i això no passa amb altres sistemes operatius.

De manera que si la gent té temps i té les seves dades en lloc segur, que provi el que vulgui i que pregunti els dubtes.

---

