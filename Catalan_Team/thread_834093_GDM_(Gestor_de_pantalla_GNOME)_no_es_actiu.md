---
title: "GDM (Gestor de pantalla GNOME) no es actiu"
date: 2008-06-19
forum: Catalan Team
---

### Post by prostata on 2008-06-19
Vaig instal-lar Kubuntu-desktop via Synaptic, sobre hardy.

Un cop el vaig provar tant com vaig voler vaig decidir tornar a Gnome. Via Synaptic el vaig treure i desprès amb sudo aptitude purge per si de cas.

La qüestió és que encara les finestres d'entrada al SO continuen sen les de Kubuntu i les de sortida també. el que voldria seria tornar a tenir les finestres Entrada/Sortida típiques del Ubuntu, (Gnome) però quan vaig a Sistema=>Administració=>Finestra d'Entrada per fer el canvis em fa fora dient-me el que poso en el subject.

¿hi ha alguna forma de solucionar aquesta situació i tornar les finestres esmentades al seu origen??

Salutacion

---

### Post by crazyserver on 2008-06-19
Primer comprova que tinguis instal·lat el GDM, després, des de Gnome, pots anar a Sistema -->Administració --> Serveis. Trobaràs el GEstor gràfic KDM i el GDM, PRIMER activa el GDM, desp&#341;es desactiva el KDM. Potser es reinicien soles les X, si no ho fan, fes-ho tu quan vulguis fer el canvi!

Si no et funciona, ves a una sessió de terminal amb Ctrl+Alt+F2 per exemple, fas 
```
sudo /etc/init.d/kdm stop
startx

```Entraràs amb Gnome, fes el mateix que he explicat abans però aquest cop segur que no se't reinicien les X. surts de la sessió, aniràs a parar de nou al terminal i reinicia;) o fes:
```
sudo /etc/init.d/gdm start

```

Sort!

---

### Post by prostata on 2008-06-19
Gràcies per la resposta, però no ha funcionat, o jo no he sabut fer-lo funcionar, tot pot ser, seguiré treballant però... :-)

---

### Post by crazyserver on 2008-06-19
I... desinstalar KDM i reinstalar GDM? ho has provat?

---

### Post by prostata on 2008-06-20
Si, gràcies,

---

