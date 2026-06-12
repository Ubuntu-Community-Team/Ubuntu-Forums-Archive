---
title: "[SOLVED] Com trobar fitxers o directoris [Era:eliminar restes de programes]"
date: 2008-08-06
forum: Catalan Team
---

### Post by climent on 2008-08-06
He estat trastejant amb un joc per a l'innombrable que he instal·lat mitjançant el Wine. Però a l'hora de desinstal·lar-lo m'ha deixat unes carpetes molt emprenyadores que pengen de l'opció "aplicacions-wine" de la barra de menús. He fet, em sembla a mi, totes les remove, clean, etc, etc. Algú pot dir-me on trobar la ruta d'accés per esborrar-les?

---

### Post by sianeu on 2008-08-06
No fa gaire vaig descobrir un cercador brutal: obre terminal i escriu

locate "nomdefitxer"

Salut

---

### Post by papapep on 2008-08-06
A un terminal:

```
sudo updatedb
```

un cop hagi acabat de processar, fes:

```
sudo locate nomdelfitxer_o_carpeta_que busques
```

i t'ensenyarà on és.

---

### Post by climent on 2008-08-07
Sí, senyors! Prova superada! Gràcies.

---

