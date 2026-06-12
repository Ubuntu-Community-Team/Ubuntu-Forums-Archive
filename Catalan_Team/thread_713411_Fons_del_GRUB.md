---
title: "Fons del GRUB"
date: 2008-03-02
forum: Catalan Team
---

### Post by eduardsola on 2008-03-02
Hola a tooots!

Com es fa per canviar la imatge de fons del GRUB (selector de sistemes operatius)?

És que he regirat altre cop la wiki del Catalan Team i he trobat una imatge de fons que m'agrada... i per no veure-ho tot negre, doncs me la vull posar, a veure què x)

Gràcies per avançat :)

---

### Post by orestesmas on 2008-03-02
No hi pots posar qualsevol imatge. Han de ser en format XPM, de 640x480 i 14 colors com a molt. Això et limita força el ventall. Pots provar de convertir una imatge amb més colors amb el programa "convert", però sovint els resultats són pobres si no és una imatge amb un color dominant.

En acabar l'has de posar a /boot/grub/splashimages i indicar-li al grub quina és dins del seu fitxer de configuració.

Tens un tutorial a [http://ruslug.rutgers.edu/~mcgrof/grub-images/]("http://ruslug.rutgers.edu/~mcgrof/grub-images/")

La versió 2 del Grub crec que millora aquest aspecte.

---

### Post by eduardsola on 2008-03-02
> **orestesmas said:**
> No hi pots posar qualsevol imatge. Han de ser en format XPM, de 640x480 i 14 colors com a molt. Això et limita força el ventall. Pots provar de convertir una imatge amb més colors amb el programa "convert", però sovint els resultats són pobres si no és una imatge amb un color dominant.

En acabar l'has de posar a /boot/grub/splashimages i indicar-li al grub quina és dins del seu fitxer de configuració.

Tens un tutorial a [http://ruslug.rutgers.edu/~mcgrof/grub-images/]("http://ruslug.rutgers.edu/~mcgrof/grub-images/")

La versió 2 del Grub crec que millora aquest aspecte.

Ho provaré demà.

Gràcies x)

---

### Post by SiscoGarcia on 2008-03-02
L'ubuntaire valencià [Vicent Cubells]("http://www.vcubells.net/") té un [tutorial al seu bloc]("http://www.vcubells.net/arxiu/2008/01/19/845/#comment-19575") on explica com fer-ho. Si no m'equivoco és una traducció del que ha apuntat l'Orestes, o si més no en fa referència.

---

