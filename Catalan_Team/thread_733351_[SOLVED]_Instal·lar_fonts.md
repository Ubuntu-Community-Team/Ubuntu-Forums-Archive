---
title: "[SOLVED] Instal·lar fonts"
date: 2008-03-23
forum: Catalan Team
---

### Post by Joan Marc on 2008-03-23
Hola a tots,
Doncs això, que m'he descarregat unes fonts en format .ttf.
Com ho puc fer per instal·lar-les i fer-les servir des de qualsevol programa que utilitzi alguna eina de text?

Gràcies

---

### Post by papapep on 2008-03-23
Copia-les a **/usr/share/fonts**, i després fes:

> sudo fc-cache -f -v ;)

---

### Post by Joan Marc on 2008-03-23
Em diu que no tinc permís per copiar-les.

Com ho puc fer per terminal i utilitzant gksudo?

MErci

---

### Post by lluisanunez on 2008-03-23
gksudo nautilus :)

---

### Post by Joan Marc on 2008-03-23
Gràcies :):)

---

### Post by papapep on 2008-03-23
I per terminal:

```
sudo cp /el_camí_complert_a_on_siguin/fitxers_de_les_fonts /usr/share/fonts
```

:-P

---

### Post by CarlesOriol on 2008-03-24
O a la carpeta .fonts del teu usuari on no calen permisos especials.

Si sols tens un usuari és el més fàcil.

---

### Post by papapep on 2008-03-24
Si, però si després tens més usuaris has de pensar en ficar-ho al /usr/share/fonts per a fer-ho global al sistema :-P

---

### Post by Joan Marc on 2008-03-24
> **CarlesOriol said:**
> O a la carpeta .fonts del teu usuari on no calen permisos especials.

Si sols tens un usuari és el més fàcil.

Carles, jo no tinc una carpeta .fonts dintre del meu usuari... que s'ha de crear manualment?

> **papapep said:**
> I per terminal:

```
sudo cp /el_camí_complert_a_on_siguin/fitxers_de_les_fonts /usr/share/fonts
```

:-P

D'aquesta manera puc copiar qualsevol cosa a qualsevol carpeta?

Bé gràcies a tots :)

---

### Post by papapep on 2008-03-24
> D'aquesta manera puc copiar qualsevol cosa a qualsevol carpeta?


Si i, per tant, ho has de fer "amb carinyu", per no cascar res :-)

---

### Post by Joan Marc on 2008-03-24
He fet una prova copiant una foto d'una carpeta de l'escriptori, a la carpeta documents.
El fet és que s'ha copiat, però quan la vull obrir, em diu que tinc l'accés denegat.... a cas he de posar gksudo en comptes de sudo?

---

### Post by CarlesOriol on 2008-03-24
> **Joan Marc said:**
> Carles, jo no tinc una carpeta .fonts dintre del meu usuari... que s'ha de crear manualment?

Si no hi és crea-la... T'estalviaras de trencar res important sense voler.

---

