---
title: "Connecting To HAL"
date: 2009-06-03
forum: General Help
---

### Post by pratheeshp on 2009-06-03
Hai ALL,
I am trying to connect to the HALD through QDBus. I am using the following command.

bool success =  hal.connection().connect( "org.freedesktop.Hal", "/org/freedesktop/Hal/Manager",
"org.freedesktop.Hal.Manager", "DeviceAdded", newCard, SLOT(cardInsertedSignalHandler(const char *)));
Actually this should connect the "DeviceAdded" signal of the HALD to the "cardInsertedSignalHandler" slot. But this function returns failure . Can any one help me in this.......... Am I doing correct .. If not help me with the correct methode!!!!  
                      Thanx in advance

---

