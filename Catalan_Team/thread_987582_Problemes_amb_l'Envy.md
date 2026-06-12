---
title: "Problemes amb l'Envy"
date: 2008-11-19
forum: Catalan Team
---

### Post by lFossil on 2008-11-19
Acabo d'instal·lar  l'ubuntu 8,10 i em pensava que ja hi venia el compiz de serie així que m'he descarregat l'envy però al moment de fer-lo anar m'ha donat aquest error
[[IMG]http://img90.imageshack.us/img90/6787/capturafinestrasensettojf1.th.png[/IMG]](http://img90.imageshack.us/my.php?image=capturafinestrasensettojf1.png)[[IMG]http://img90.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)]

A què es deu?

---

### Post by lo gambusí on 2008-11-19
No has posat bé l'enllaç, lFossil, i no es veu res.

---

### Post by tanreb20 on 2008-11-19
Bé.. t'ho diu clarament, que hi ha hagut un error i consultis l'arxiu:


des de un terminal fes:

```
gedit /var/log/envy-installer.log
```

i copiens el que posa.

---

### Post by lFossil on 2008-11-19
python pulse.py ati uninstall 
root@jasiel-laptop:/usr/share/envy# python pulse.py ati uninstall
S'està llegint la llista de paquets... Fet
S'està construint l'arbre de dependències       
S'està llegint la informació d'estat... Fet
0 actualitzats, 0 nous a instal·lar, 3 reinstal·lats, 0 a eliminar i 0 no actualitzats.
Es necessita obtenir 0B/2968kB d'arxius.
After this operation, 0B of additional disk space will be used.
(S'està llegint la base de dades ... hi ha 111308 fitxers i directoris instal·lats actualment.)
S'està preparant per a reemplaçar libgl1-mesa-glx 7.2-1ubuntu2 (fent servir .../libgl1-mesa-glx_7.2-1ubuntu2_i386.deb) ...
S'està desempaquetant el reemplaçament de libgl1-mesa-glx ...
S'està preparant per a reemplaçar libgl1-mesa-dri 7.2-1ubuntu2 (fent servir .../libgl1-mesa-dri_7.2-1ubuntu2_i386.deb) ...
S'està desempaquetant el reemplaçament de libgl1-mesa-dri ...
S'està preparant per a reemplaçar libglu1-mesa 7.2-1ubuntu2 (fent servir .../libglu1-mesa_7.2-1ubuntu2_i386.deb) ...
S'està desempaquetant el reemplaçament de libglu1-mesa ...
S'està configurant libgl1-mesa-glx (7.2-1ubuntu2) ...
S'està configurant libgl1-mesa-dri (7.2-1ubuntu2) ...
S'està configurant libglu1-mesa (7.2-1ubuntu2) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
ENVY: Operation Completed

---

### Post by lFossil on 2008-11-19
No sé que m'ha passat però he reiniciat l'ordinador i no em funciona, s'inicia, sobre la pantalla de càrrega però quan acava de carregar-se surt la pantalla en negre i surten unes quantes frases, per alguna banda e vist que deia alguna cosa de ATI i ENVIDIA, potser e tocat alguna cosa de l'Envy.

Com que no he aconseguit res després de reiniciar moltíssimes vegades, he provat tornant a instal·lar l'ubuntu de nou però tampoc em deixa, no sé què hi deu passar algú em pot ajudar si us plau?

---

### Post by lFossil on 2008-11-20
crec que se m'ha quedat a mitja instalació i quan obric ll'ordinador em surt 

GRUB loadin, please wait...
Error 15


i es queda així, no sé que fer

---

### Post by lFossil on 2008-11-20
Al final he pogut instal·lar altre cop l'ubuntu, de moment no tinc cap més problema.

---

