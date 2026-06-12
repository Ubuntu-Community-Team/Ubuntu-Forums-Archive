---
title: "Firefox fora de linia"
date: 2008-05-02
forum: Catalan Team
---

### Post by CarlesOriol on 2008-05-02
Des de que he actualitzat a la hardy que cada cop que obro el firefox em surt com "fora de linia".

Algú sap com evitar-ho?

---

### Post by menut on 2008-05-02
```
sudo apt-get remove network-manager network-manager-gnome
```

A mí també em passava, ja que em connecto per mòdem USB i el Network Manager no m'ho detectava.

Per a l'Ubuntu és com si no hi hagués connexió, i el Firefox s'inicia en mode fora de línia.

---

### Post by CarlesOriol on 2008-05-02
No em connecto a internet per usb, no uso el nm-applet, tinc un script pel wifi.

En qualsevol cas he provat el que dius connectant per eth0 (calbejat) i el problema segueix igual.

---

