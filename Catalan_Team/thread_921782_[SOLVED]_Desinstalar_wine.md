---
title: "[SOLVED] Desinstalar wine"
date: 2008-09-16
forum: Catalan Team
---

### Post by tanreb20 on 2008-09-16
Hola!!!!

Algu em podria explicar com esborrar COMPLETAMENT el wine, vaig provar de fer un ```
sudo aptitude remove --purge wine
``` pero em va deixar la carpeta, lav aig esborrar pero ni aixi aconsegueixo esborar-ho, o aixo crec.

Al menu segueix estant la carpeta wine i no sé si esborrarla completament i ja estaria llest.

Algu em pot dir q fer?

---

### Post by patrickfromspain on 2008-09-16
sudo dpkg --purge wine
cd
rm -rf .wine

---

