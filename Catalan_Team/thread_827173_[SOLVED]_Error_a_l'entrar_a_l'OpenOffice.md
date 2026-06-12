---
title: "[SOLVED] Error a l'entrar a l'OpenOffice"
date: 2008-06-12
forum: Catalan Team
---

### Post by cortsenc on 2008-06-12
Bones,
Al entrar a l'OpenOffice (en qualsevol de les seves funcions) em surt el següent error:

> S'ha produït un error en carregar el BASIC del document file:///usr/lib/openoffice/share/basic/WebWizard/script.xlb/:
Error general.
Error general d'entrada/sortida

Tot seguit, em surt el mateix però amb la ruta diferent:
> file:///usr/lib/openoffice/share/basic/WebWizard/dialog.xlb/

He consultat les carpetes, i no existeix la "WebWizard". La pregunta és, vosaltres teniu aquesta carpeta?

Gràcies

---

### Post by jaume69 on 2008-06-12
Jo tampoc la tinc se'm carrega bé. :confused:

---

### Post by oriolsbd on 2008-06-13
Hola,

Sembla que hi ha un bug obert al Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/205322](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/205322)

Pel que comenten, sembla aparèixer en no sé quins casos, quan es puja d'OpenOffice 2.3 a OpenOffice 2.4. Proposen dues possibles solucions:

- Borrar els directoris /home/el_teu_usuari/.openoffice.org i /home/el_teu_usuari/.openoffice.org2. Em sembla una opció massa dràstica.
- Editar els fitxer /home/el_teu_usuari/.openoffice.org2/usr/basic/script.xlc i /home/el_teu_usuari/.openoffice.org2/usr/basic/dialog.xlc i borrar en ambdós la següent línia:
<library:library library:name="WebWizard" xlink:href="file:///usr/lib/openoffice/share/basic/WebWizard/dialog.xlb/" xlink:type="simple" library:link="true" library:readonly="true"/>

Em sembla que aquesta segona opció és més assenyada.

Salut!

---

### Post by cortsenc on 2008-06-17
Gràcies **oriolsbd**,
He provat la segona opció i ha funcionat!!

Per cert, per si algú més li passa, per defecte se m'obria amb el Full de càlcul de OpenOffice.org però no em deixava guardar amb el mateix format .xlc. L'he hagut d'obrir amb l'editor de text del Gnome (Gedit).

Salut!

---

