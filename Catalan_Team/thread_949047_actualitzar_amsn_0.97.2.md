---
title: "actualitzar amsn 0.97.2"
date: 2008-10-15
forum: Catalan Team
---

### Post by lFossil on 2008-10-15
Bones, ja fa bastant de temps que se m'obri una finestra d'actualització del amsn al iniciar aquest, però el cas és que no consegueixo fer-ho.

Provo fen:
sudo apt-get update
sudo apt-get dist-upgrade

però ni així ho aconsegueixo, algú em sabria dir què fer?

Gràcies per adelantat!

---

### Post by _DarkEagle_ on 2008-10-16
No pots actualitzar de la manera habitual per que als repositoris no està actualitzat.

El que pots fer es:

Primer borrar-lo:

```
apt-get remove amsn
```

Un cop borrat, l'instal·larem directament de la web, amb el autopackage, no és difícil.

Anem a la web: [http://www.amsn-project.net/linux-downloads.php](http://www.amsn-project.net/linux-downloads.php)

Si fem anar Tcl/Tk 8.4 descarreguem: [http://prdownloads.sourceforge.net/amsn/amsn-0.97.2-1.tcl84.x86.package](http://prdownloads.sourceforge.net/amsn/amsn-0.97.2-1.tcl84.x86.package)

Per contra, si fem anar Tcl/Tk 8.5 descarreguem: [http://prdownloads.sourceforge.net/amsn/amsn-0.97.2-1.tcl85.x86.package](http://prdownloads.sourceforge.net/amsn/amsn-0.97.2-1.tcl85.x86.package)

Un cop descarregat l'arxiu, li donem permisos d'execució:

chmod +x amsn-0.97.2-1.tcl85.x86.package

i l'executem: ./amsn-0.97.2-1.tcl85.x86.package

Seguim les instruccions que en surten per pantalla

Problemes que ens podem trobar:

Si fem anar Tcl/Tk 8.5 però també tenim instal·lades les TCl/Tk 8.4 al sistema, per defecte es fan anar les 8.4, el que hem de fer es anar als scripts del amsn i canviar la paraula **wish** per **wish8.5**

Els scripts a modificar seran:

/usr/bin/amsn
/usr/bin/amsn-remote
/usr/bin/amsn-remote-CLI

Com veureu, el amsn instal·lat es podria desinstalar per: Aplicacions -> Utilitats del Sistema -> Manage 3rd party software

Espero que no m'hagi deixat res ...

Salut !

---

