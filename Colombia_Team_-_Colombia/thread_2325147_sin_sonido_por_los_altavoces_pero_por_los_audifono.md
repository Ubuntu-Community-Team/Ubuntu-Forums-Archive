---
title: "sin sonido por los altavoces pero por los audifonos si"
date: 2016-05-19
forum: Colombia Team - Colombia
---

### Post by frerere on 2016-05-19
mi chip es el IDT 92HD81B1X5. estaba en kubuntu 14.04 y después de una actualización me quede sin sonido. instalé ubuntu 16.04 y sigo sin sonido. he intentado muchos how to pero ninguno me ha servido.antes de perder el sonido tenia sonido solo por uno de los altavoces. estos son mis datos:
cat /proc/asound/cards
 0 [MID            ]: HDA-Intel - HDA Intel MID
                      HDA Intel MID at 0xd8400000 irq 28
cat /proc/asound/card*/codec* | grep Codec
Codec: IDT 92HD81B1X5
Codec: Intel IbexPeak HDMI
aplay -l
**** Lista de PLAYBACK dispositivos hardware ****
tarjeta 0: MID [HDA Intel MID], dispositivo 0: 92HD81B1X5 Analog [92HD81B1X5 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: MID [HDA Intel MID], dispositivo 1: 92HD81B1X5 Digital [92HD81B1X5 Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: MID [HDA Intel MID], dispositivo 3: HDMI 0 [HDMI 0]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

gracias por su tiempo y por la ayuda que me puedan proporcionar.

---

### Post by user1397 on 2016-05-20
Estas "dualbooting" con Windows u otro sistema operativo en la misma computadora?  Sale el sonido en Windows solo pero no en ubuntu?  

Si no, si fuera yo guardaria todos mis datos en un disco duro externo y reinstalaria ubuntu 16.04 para ver si funciona todo.  Tambien ve si hay un driver para instalar (ve en el software repositories programa)

---

### Post by QIII on 2016-05-20
@frerere -

This is an English-speaking forum.  Please choose a language-appropriate sub-forum under Ubuntu Loco Teams and I will move the thread there for you.

---

### Post by frerere on 2016-05-20
muévelo a colombia team-colombia

---

### Post by QIII on 2016-05-20
Saludos!

---

