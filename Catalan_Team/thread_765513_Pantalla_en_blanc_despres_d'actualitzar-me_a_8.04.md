---
title: "Pantalla en blanc despres d'actualitzar-me a 8.04"
date: 2008-04-24
forum: Catalan Team
---

### Post by MorlanXaos on 2008-04-24
Doncs si, m'he quedat amb un pam de nas, perquè al iniciar l'Ubuntu, i després d'el login, la pantalla  s'ha quedat en blanc.

He trobat alguna documentació per la red, on fan referencia a des-instal.lar el compiz.core.

I així ho he fet, des de la consola, (sudo apt-get remove compiz-core) al reiniciar l'Ubuntu, i ara ja esta solucionat. Crec que tindré que reinstal.lar del controladors de la tarjeta gráfica una altre vegada.

Pero hi ha una cosa que no em queda massa clara. El Grub, em dona opció a inciar el 8.04 amb el kernel 2.6.25-16 o amb el 2.6.24-14,

Quina diferencia hi ha entre utilitzar un o l'altre? suposo que el millor es utilitzar el 25-16, ja que deu ser l'ultim, però perque surten les dues opcions?

---

### Post by papapep on 2008-04-24
Per que tens les dues versions instal·lades (és normal, que t'instal·li el nou no significa que tregui els antics :-)) i et deixa triar quina vols carregar.

---

### Post by MorlanXaos on 2008-04-24
Llavors es pot des-instal.lar el kernel antic?
Si es així, quina es la millor manera de fer-ho?
Gracies

:)

---

### Post by RainCT on 2008-04-25
Pots desinsta&#320;lar lo des del Synaptic. El motiu de que t'apareixin els dos és que així si amb el nou deixa de funcionar-te algun component pots continuar fent servir el vell, però si ja has comprovat que no tens problemes hauria de ser segur desinsta&#320;lar el vell.

---

