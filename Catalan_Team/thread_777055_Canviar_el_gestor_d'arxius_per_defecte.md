---
title: "Canviar el gestor d'arxius per defecte"
date: 2008-05-01
forum: Catalan Team
---

### Post by borgg on 2008-05-01
Salut amics ubuntarires,

Algú té la més mínima idea de com es pot canviar el gestor d'arxius per defecte a l'ubuntu, el nautilus, pel per exemple, pcmanfm?

He estat buscant en aplicacions preferides i aquesta opció no hi és, gràcies!

---

### Post by papapep on 2008-05-01
Sembla ser que s'han de modificar un parell de fitxers de configuració.

/usr/share/applications/nautilus-computer.desktop
/usr/share/applications/nautilus-home.desktop

Cal modificar (amb drets d'administrador) a ambdós fitxers la línia que comença per **Exec**, per que en vers de:

```
Exec=nautilus --no-desktop computer:
```

hi posi:

```
Exec=pcmanfm
```

Sobretot, fes-ne una còpia abans de tocar-los per si passa qualsevol daltabaix:

```
sudo cp /usr/share/applications/nautilus-computer.desktop /usr/share/applications/nautilus-computer.desktop.backup
```

i el mateix amb l'altre fitxer.

---

### Post by borgg on 2008-05-02
Moltes gràcies papapep,

En quan tingui una mica de temps ho provaré, espero no carregar-me el sistema ^^

---

