---
title: "Me reconoce el disco duro externo sbd1 - pero no me deja ver la informacion"
date: 2023-09-18
forum: Colombia Team - Colombia
---

### Post by davidstiven on 2023-09-18
Buenas tardes!!

me pueden ayudar por favor con lo siguiente.

hace poco inicie en el mundo de UBUNTU y me ha ido de maravilla hasta el día de ayer que trate de abrir mi disco duro externo (SAMSUNG) donde manejo mi información del trabajo, cuando lo conecto -ubuntu me lo reconoce pero no me deja abrir la informacion sale el siguiente error 

**error mounting /dev/sbd1 at /media/davidstiveb/SAMSUNG:Unknown error when mounting /dev/sdb1**

he tratado de montarlo por la terminal pero no me deja montar el disco duro externo

alguien sabe como solucionarlo?

   
**Nota:** las demas USB me las reconce sin problemas

muchas gracias..

---

### Post by texpat on 2023-09-19
¿Has intentado con ntfsfix?

```

sudo ntfsfix /dev/sdb1

```

Como siempre, no copies y pegues comandos a ciegas. Mira por lo menos la manpage y hay más info por ahí en las redes.

¡Suerte!

---

### Post by davidstiven on 2023-09-19
Eres el mejor!!

me funciono de maravilla

Gracias...

---

