---
title: "El disc dur extern no es conecta"
date: 2008-09-25
forum: Catalan Team
---

### Post by tanreb20 on 2008-09-25
Hola.

Des que vaig instalar el disk manager em passa una cosa curiosa:

Cuan conecto el disk dur extern em diu que no es pot montar el volum, pero si l'obro amb el disk manager em permet montar-lo i posar-lo al fstab amb aquest resultat:

```
#Entry for /dev/sdb1 :
UUID=42CCF0FBCCF0E9D5   /media/Externat ntfs    defaults,nls=utf8,umask=0222   00
```

Pero no vui que surti al fstab, xq en principi no  hi hauria de ser, i si trec el disk manager llavors si que no el monta.

Si el poso al fstab, fent un

```
sudo mount -a
```

funciona, pero clar... m'interessa qeu es monti solet quan el conecto o el desconecto

---

### Post by papapep on 2008-09-26
S'ha parlat repetides vegades del tema al fòrum. Busca una mica i trobaràs uns quants fils.

---

