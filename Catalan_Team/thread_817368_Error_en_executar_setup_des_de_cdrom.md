---
title: "Error en executar setup des de cdrom"
date: 2008-06-03
forum: Catalan Team
---

### Post by trinkus on 2008-06-03
Tinc un programa del que ja vaig instalar una versio anterior. En intentar executar el setup de la nova em surt el seguent, algu sap a que pot ser degut i que puc fer per solucionar-ho? Gracies per endavant!


roger@roger-laptop:/media/cdrom$ sh setup
Preparing to install COMSOL...
FATAL ERROR (Can't run the COMSOL installer when current working directory is on the CD path), Installation aborted.

Installation failed.
roger@roger-laptop:/media/cdrom$

---

### Post by RainCT on 2008-06-03
Doncs el que et diu, que no executius el setup estant dins del directori /media/cdrom.

---

### Post by trinkus on 2008-06-04
Resulta que he copiat el disc al disc dur, l'he executat des d'alla i diu EXACTAMENT el mateix...

---

### Post by papapep on 2008-06-04
El que havies de provar no era a copiar el programa al disc i executar-lo des d'allà, sinó sortir del directori del cdrom i executar-lo:

```
/home/elteuusuari$ sh /media/cdrom/setup
```

---

### Post by trinkus on 2008-06-04
Quina tonteria... no se m'havia acudit... en tot cas moltissimes gracies!

---

