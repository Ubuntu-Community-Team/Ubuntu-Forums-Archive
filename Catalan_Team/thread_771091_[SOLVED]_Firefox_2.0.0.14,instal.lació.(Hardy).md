---
title: "[SOLVED] Firefox 2.0.0.14,instal.lació.(Hardy)"
date: 2008-04-27
forum: Catalan Team
---

### Post by jaume69 on 2008-04-27
Hola,que vull instal.lar el Firefox 2.0.0.14 desde la web i em surt un problema que no puc instal.larlo.

Quan executo l'arxiu bin de Firefox no fa res.I desde el terminal diu que falta una llibreria que no trobo enlloc. ¿?

Gràcies.


________________________

---

### Post by Joan Marc on 2008-04-27
Has de marcar el bin com a executable:
Botó dret (sobre el bin)>Propietats>Permisos> i marca "Permet executar aquest fitxer com a un programa".

Salut

---

### Post by jmaspons on 2008-04-27
És més fàcil si l'instal·les des del gestor de paquets. Als repositoris de ubuntu Hardy hi tens el firefox 2 o el 3 versió beta però que funciona bé malgrat que encara no hi ha la traducció al català.

Salut!

---

### Post by papapep on 2008-04-27
> malgrat que encara no hi ha la traducció al català

Fa uns quants dies que ja està traduït, per l'alliberament de la versió definitiva. :-)

---

### Post by patrickfromspain on 2008-04-27
l'error que et dona, que esta be saber-ho, es que et falta el libstdc++5. Es facil solucionar-ho: sudo apt-get install libstdc++5

---

### Post by Joan Marc on 2008-04-27
Els que teniu la versió 3 beta, podeu carregar una captura?
Esque acabo d'actualitzar a Hardy, i no hi trobo massa la diferència, i a Ajuda em diu que és la versió 3.0b5.

Merci.

---

### Post by papapep on 2008-04-27
I quina diferència esperes trobar??? Si et diu que és la 3.0b5, doncs aquesta és...a la barra de la finestra també t'ho ha de dir.

---

### Post by menut on 2008-04-27
Diferències a primera vista:

[LIST]
[*]Quan escrius una URL que anteriorment ja has visitat, surt un nou desplegable conforme vas escribint amb les diferents web de l'historial
[*]En descarregar quelcom, a la barra d'estat, a la dreta, t'indica quantes descàrregues tens i quant temps queda fins que finalitzin
[*]Nou tractament de fitxers i podcasts
[/LIST]

---

### Post by niculau on 2008-04-27
despres de 5 penjades (dues de les quals m'han obligat a reiniciar el sistema) he decidit instal·lar el firefox 2.0

Quan estigui la versió final ja hi tornarem

---

### Post by jaume69 on 2008-04-27
[QUOTE="patrickfromspain"]l'error que et dona, que esta be saber-ho, es que et falta el libstdc++5. Es facil solucionar-ho: sudo apt-get install libstdc++5[/QUOTE]
No hi és a Synàptic,hi ha alguna versió semblant.

[QUOTE="Joan Marc"]Has de marcar el bin com a executable:
Botó dret (sobre el bin)>Propietats>Permisos> i marca "Permet executar aquest fitxer com a un programa".

Salut [/QUOTE]
Tampoc fa res,li dones al bin de Firefox i ni obrint-lo desde terminal(quan t'ho demana)no fa res,sembla que s'obri el terminal però res.

[QUOTE="Jmaspons"]És més fàcil si l'instal·les des del gestor de paquets. Als repositoris de ubuntu Hardy hi tens el firefox 2 o el 3 versió beta però que funciona bé malgrat que encara no hi ha la traducció al català.

Salut! [/QUOTE]
Suposo que és el que faré,per força!!..
Amb el Firefox 3 tens la avantatge que el cursor no es para en algun element de Flash.
Que no sé si be del navegador o dels avenços que li han fet al Touchpad.

[QUOTE="Joan Marc"]Els que teniu la versió 3 beta, podeu carregar una captura?
Esque acabo d'actualitzar a Hardy, i no hi trobo massa la diferència, i a Ajuda em diu que és la versió 3.0b5.

Merci. [/QUOTE]
[**_Si_**]("http://img187.imageshack.us/img187/3828/pantallazoui0.png")

_____________________________________
Merci.          :popcorn:

---

### Post by Joan Marc on 2008-04-28
Oh! merci a tots.
Ho deia perque amb la versió de windows hi ha diferència gràfica en els menús, en canvi a la de linux no, nomès per això dubtava.

Saluts!

---

### Post by patrickfromspain on 2008-04-28
el libstdc++5 esta al repositori universe, mira de que el tinguis activat, que hi ha de ser.

salut!

---

### Post by jaume69 on 2008-05-02
Doncs si,amb aquest paquet (libstdc++5) ja funciona.
L´únic que ara no em deixa instal.lar extensions(2.0.0.14),a la cónsola d'errors em diu:
> Error: oldInstallLocation has no properties
Fitxer font: file:///home/jaume/firefox/components/nsExtensionManager.js
Línia: 3054

No chrome package registered for chrome://button/skin/button.png .

Mercès.:popcorn:      :mad:

---

