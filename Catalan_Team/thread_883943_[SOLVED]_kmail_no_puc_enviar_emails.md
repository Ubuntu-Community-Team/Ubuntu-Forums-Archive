---
title: "[SOLVED] kmail: no puc enviar emails"
date: 2008-08-08
forum: Catalan Team
---

### Post by giorgiograppa on 2008-08-08
Salutacions, companys!

Estic intentant adaptar-me al KMail i avui m'està donant problemes: puc rebre el correu amb tota normalitat, però no em deixa enviar-ne cap, sempre em diu: "Protocol de transport desconegut, no s'ha pogut enviar cap missatge."

Aquesta és la màxima informació que he obtingut. Tanmateix, el compte SMTP que dirigeix la sortida de missatges està configurat exactament igual que el seu homòleg al Thunderbird (i aquest sí que envia els missatges sense problemes):

[INDENT]Màquina: smtp.correo.yahoo.es
Port: 465
(Usuari i contrasenya correctes)
Xifratge: tsl (amb ssl obtinc el mateix resultat)[/INDENT]

La cosa estranya és que ahir, amb la mateix configuració, funcionava bé.

He buscat amb Google el missatge d'error, però no hi he trobat res de profit. Alguna pista?

Gràcies.

---

### Post by papapep on 2008-08-08
> Alguna pista?

Sí, això amb Gnome no passa....:-P

---

### Post by giorgiograppa on 2008-08-08
Aquesta me la temia i me l'esperava, Papapep. Ets molt dolent ;-) .

---

### Post by papapep on 2008-08-08
És que és inevitable, la meva neurona catxonda no se'n sap reprimir.... :-D

Respecte el teu k-problema, has provat a dir-li que empri SSL en vers de TLS?

---

### Post by giorgiograppa on 2008-08-08
He provat a posar SSL, he provat amb un altre compte de correu, he provat a demanar-li-ho per favor, per favor, per favor... Però continua comportant-se com si no hagués sentit parlar mai de l'SMTP!

---

### Post by giorgiograppa on 2008-08-08
Ara l'he canviat a un compte en gmail.com. A més del mateix error d'abans, ara em trau una finestra que diu:
"Expiració al servidor

smtp.gmail.com"

Això vol dir que s'ha mort? Gmail s'ha mort?

---

### Post by giorgiograppa on 2008-08-10
Bé, com que ja puc enviar emilis amb el **KMail** , crec que ha arribat el moment de tancar aquest fil. Abans, naturalment, deixaré una petita descripció de la situació actual (solució parcial, doncs).

Continuo sense poder enviar enviar res pels servidors smtp de Yahoo (smtp.correo.yahoo.es i smtp.mail.yahoo.it). He provat totes les configuracions: la que recomana Yahoo, la que s'obté amb el botó de "Comprova què és el que permet el servidor", més totes les combinacions que se m'han acudit. Si algú ho ha pogut fer (suposo que sí), li agrairé que m'expliqui com.


Puc enviar correu amb l'smtp de Gmail (smtp.gmail.com), però no amb la configuració que crea KMail amb aquell botó de "Comprova...", sinó amb la que recomana el propi Gmail: port 465, seguretat SSL, autenticació PLAIN (els de Gmail esmenten també TLS, però amb aquest no me n'he sortit).

Puc enviar correu amb el servidor smtp de la Universitat de València (postal.uv.es) i de l'Xtec (xmtp.xtec.cat) amb les configuracions que resulten del botó "Comprova...".

Imagino que molts esteu fent servir l'smtp de Yahoo amb el KMail, de manera que sospito que **el meu** KMail li té mania, potser per algun trauma infantil.

Com que ja he aconseguit el que necessitava, enviar correu pel KMail, deixo la resolució del misteri de l'antipatia KMail-Yahoo, per a després de les vacances.

I amb açò, declare clausurat aquest pantà, dic, aquest fil.

Moltes gràcies.

---

### Post by CarlesOriol on 2008-08-11
mmm...

He fet una prova d'usar amb el kmail un compte meu de yahoo.ecs i puc enviar però no puc rebre amb la mateixa configuració que a l'evolution...

No ho entenc...

-------------------------

edito: Amb el kmail de kde4 estic igual. I el curiós es que rebo el correu vell (guardat al servidor de yahoo de més de 3 mesos) però quan hi ha missatges nous em dona un error.

Aquests nois crec que estan adaptant el seu look & feel a les tecnologies de microsoft.

---

### Post by giorgiograppa on 2008-08-11
Gràcies, Carles!

Durant un parell de dies he arribat a pensar si no se m'hauria fos el cervell amb la calor :-D.

Bé, si no sóc l'únic amb aquest problema, vol dir que és un bug (o que té pinta de ser-ho)?

---

