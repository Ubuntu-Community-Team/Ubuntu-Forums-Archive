---
title: "[SOLVED] Problema amb k3b"
date: 2008-11-19
forum: Catalan Team
---

### Post by Dr.Rwh on 2008-11-19
Hola a tots, mireu tinc un problema, a veure si entre tots el solucionem :

Vaig instalar el k3b per gravar cd's i dvd's i tal , el cas és que avui intentava gravar un archiu, i em deia que no tenia permisos per fer-ho. Buscant a internet, em deien que era perque no tenia permisos adients, i qeu tenia que fer això :

```

chmod 4711 cdrdao
chmod 755 cdrecord

```

I jo inocent de mi, va i ho faig, i ara no em reconeix els cd's i tampoc em permet gravar res. De fet quan poso un cd a la disquetera, s'em realentitza molt el PC, s'em penja el firefox. i no se com fer els passos enrere 

Gràcies de bestreta, i salut!

---

### Post by papapep on 2008-11-19
/usr/bin/cdrdao l'has de tenir amb permisos 755, i /usr/bin/cdrecord és un enllaç a /usr/bin/wodim. L'enllaç l'has de tenir amb 777 i el wodim també amb 755.

---

### Post by Dr.Rwh on 2008-11-20
Solucionat Gràcies :)

---

