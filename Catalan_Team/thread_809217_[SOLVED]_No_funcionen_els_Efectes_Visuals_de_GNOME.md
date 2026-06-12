---
title: "[SOLVED] No funcionen els Efectes Visuals de GNOME"
date: 2008-05-27
forum: Catalan Team
---

### Post by LitusMayol on 2008-05-27
Bones!

Ja torno a ser aquí! 
A veure us explico. No puc activar els *Efectes Visuals*. Si vaig a *Sistema>Preferències>Aparença>Efectes Visuals* i clico damunt de "*Normal*" o "*Extra*" desapareien totes les finestres del l'escriptori i el fons d'escriptori i torna a aparèixer tot (i deu tarda un parell de segons, no més) i llavors m'apareix un quadre amb el missatge següent "*No s'han pogut habilitar els efectes de l'escriptori*" i una sola opció "*D'acord*".


Algú em pot ajudar?


Merci de nou! ;)

---

### Post by crazyserver on 2008-05-27
Quin problema no tens Litus? XD

Quin driver uses? Si uses ati, millor usar el driver ati que el fglrx, i si uses nvidia millor el nvidia k el nv... COm ho pots saber quin uses... doncs ara no ho sé XD

Sort!

---

### Post by crazyserver on 2008-05-27
Ah! el que si sé es que pots mirar si tens acceleració gràfica fent:
glxinfo |grep rendering

---

### Post by patrickfromspain on 2008-05-27
estaria be que diguessis quina grafica tens!

---

### Post by LitusMayol on 2008-05-27
```
litus@mayolets-desktop:~$ glxinfo |grep rendering
direct rendering: Yes
litus@mayolets-desktop:~$ 

```

Coses de la informàtica... he reiniciat l'ordinador ho he tornat a probar i..*Taxan!* funciona. 

No sé perquè, però ja funciona!

Merci als dos de totes maneres ;)

---

