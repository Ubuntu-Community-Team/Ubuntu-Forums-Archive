---
title: "[SOLVED] Puc canviar l'idioma al PDFedit?"
date: 2008-06-30
forum: Catalan Team
---

### Post by ealbert on 2008-06-30
Hola companys!
He instal·lat el programa PDFedit 0.3.2 per provar-lo, però al iniciar-lo està en anglès i m'agradaria tenir-lo en català o si més no en espanyol.

Per instal.lar-lo he executat des de la terminal:
sudo apt-get install pdfedit

Agrairé un cop de mà.

---

### Post by lesergi on 2008-06-30
Hola!

El que pots fer és executar el següent:

```
export LANG="es_ES" && pdfedit
```

Això canviarà l'idioma de la sessió i únicament canviarà l'idioma del pdfedit.

He intentat definir el segon idioma a /etc/default/locale però sembla no funcionar...

Espere que açò t'ajude.

---

### Post by ealbert on 2008-06-30
Lesergi, molt agraït per la teva informació; ho he provat i deu ni do de la seva efectivitat. M'apuntaré aquesta instrucció en les meves notes

---

### Post by papapep on 2008-06-30
Ealbert, marca el fil com a resolt, si us plau: "Thread tools > Mark this thread as solved".

---

### Post by ealbert on 2008-07-01
Papapep, gràcies per la informació, no sabia on accedir per donar-lo per tancat, a partir d'ara ja no tinc disculpa, bon estiu!

---

