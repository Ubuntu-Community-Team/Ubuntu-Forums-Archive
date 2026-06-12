---
title: "[SOLVED] FireFox treballa fora de línia"
date: 2008-11-18
forum: Catalan Team
---

### Post by Manelitu on 2008-11-18
Hola,

Tinc un modem USB 3G Vodafone, el Huwaei 220, i quan faig la connexió i després obro el firefox sempre tinc que desactivar el treballa fora de línia per tal de navegar.

Inclus si el tenco i el trono a obrir tornar a estar activat el fora de linia.... es una mica empranyador i m'agradaria solucionar-lo.

Moltes gràcies.

---

### Post by indiosincracia on 2008-11-18
Benvingut Manelitu, prova d'impedir que el Firefox comuniqui amb el network manager.

gksudo gedit /etc/dbus-1/system.d/NetworkManager.conf

substitueix <allow send_interface="org.freedesktop.NetworkManager"/> per <deny send_interface="org.freedesktop.NetworkManager"/>
guarda els canvis i reinicia.

---

### Post by Manelitu on 2008-11-18
Perfecte, ja funciona. Edito el títol.

Moltes gràcies.

---

