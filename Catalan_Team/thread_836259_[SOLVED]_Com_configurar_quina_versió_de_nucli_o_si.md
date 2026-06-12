---
title: "[SOLVED] Com configurar quina versió de nucli o sistema operatiu arrencar"
date: 2008-06-21
forum: Catalan Team
---

### Post by grundt on 2008-06-21
A l'engegar l'ordinador, m'apareix la possibilitat d'entrar amb el windows xp , o amb 8 classes diferents d'ubuntu, cada cop n'hi ha més.
Com puc deixar l'ubuntu més recent i el seu recovery mode?

---

### Post by pespin on 2008-06-21
Això deu ser perquè tens més d'un kernel instal·lat.

Fes a la terminal un:

> sudo aptitude search linux-image-2.6

i enganxa aquí el que surti

---

### Post by RainCT on 2008-06-21
Deixa't de tonteries, es molt més fàcil:

Insta&#320;la el paquet «startupmanager» des del Synaptic, i llavors vés a Sistema -> Administració -> StartUp-Manager, espera que es carregui i un cop s'obri vés a la pestanya «Avançat» , marca la opció «Limita el nombre de nuclis del menú d'arrencada» i al camp que hi ha a sota tria 2 o 3 (sempre convé tenir com a mínim un de més per si arriba un nou que no funciona).

(No ho he provat, però hauria de funcionar).

---

### Post by jaume69 on 2008-06-21
Jo tenia el **Startupmanager**(Gutsy)i va molt bé,ja l´instal.laré quan pugui..

Jo el que feia quan m´actualitzaven el **Kernel**,era esborrar el vell i quedar-me amb el nou,contan que aquest últim vagi bé!.

_____________________________

El que voldria saber és si es pot canviar el ordre d´arrancada de **S.O.** que hi ha al inici?.I com?.
(Jo prefereixo que primer inici Ubuntu en lloc de Vista,però tot és bó saber-ho)

---

### Post by grundt on 2008-06-21
He fet lo de l'startupmanager, per comoditat.

FUnciona!

Gràcies a tots.

---

### Post by CarlesOriol on 2008-06-21
Però això de l'startupmanager no desinsta&#320;la els núclis i cada un et pot ocupar vora 100 Mb... millor elimina (amb molt de compte) els que no usis amb el synaptic.

---

### Post by grundt on 2008-06-21
Com?

Amb el synaptic he de borrar aquests nuclis?

---

### Post by pespin on 2008-06-21
Amb l'ordre que t'he dit pots veure ràpidament quins nuclis tens instal·lats i llavors és qüestió d'esborrar-los tots menys l'últim.

---

### Post by jaume69 on 2008-06-21
[QUOTE="Jo mateix"]El que voldria saber és si es pot canviar el ordre d´arrancada de S.O. que hi ha al inici?.I com?.
(Jo prefereixo que primer inici Ubuntu en lloc de Vista,però tot és bó saber-ho) [/QUOTE]

-He vist que instal.lant **Startupmanager** pots triar el **S.O.** que estigui per defecte,suposo que vol dir el que arrencarà primer.

:neutral:

---

### Post by RainCT on 2008-06-21
> **jaume69 said:**
> He vist que insta&#320;lant Startupmanager pots triar el S.O. que estigui per defecte,suposo que vol dir el que arrencarà primer

Suposes bé :).

---

### Post by grundt on 2008-06-22
Doncs em surt això.


v   linux-image-2.6                 -                                           
c   linux-image-2.6.20-15-generic   - Linux kernel image for version 2.6.20 on x
i   linux-image-2.6.20-16-generic   - Linux kernel image for version 2.6.20 on x
i   linux-image-2.6.22-14-generic   - Linux kernel image for version 2.6.22 on x
p   linux-image-2.6.24-16-386       - Linux kernel image for version 2.6.24 on i
p   linux-image-2.6.24-16-generic   - Linux kernel image for version 2.6.24 on x
p   linux-image-2.6.24-16-openvz    - Linux kernel image for version 2.6.24 on O
p   linux-image-2.6.24-16-rt        - Linux kernel image for version 2.6.24 on I
p   linux-image-2.6.24-16-server    - Linux kernel image for version 2.6.24 on x
p   linux-image-2.6.24-16-virtual   - Linux kernel image for version 2.6.24 on x
p   linux-image-2.6.24-16-xen       - Linux kernel image for version 2.6.24 on T
p   linux-image-2.6.24-18-386       - Linux kernel image for version 2.6.24 on i
i   linux-image-2.6.24-18-generic   - Linux kernel image for version 2.6.24 on x
p   linux-image-2.6.24-18-openvz    - Linux kernel image for version 2.6.24 on O
p   linux-image-2.6.24-18-rt        - Linux kernel image for version 2.6.24 on I
p   linux-image-2.6.24-18-server    - Linux kernel image for version 2.6.24 on x
p   linux-image-2.6.24-18-virtual   - Linux kernel image for version 2.6.24 on x
p   linux-image-2.6.24-18-xen       - Linux kernel image for version 2.6.24 on T
p   linux-image-2.6.24-19-386       - Linux kernel image for version 2.6.24 on i
i   linux-image-2.6.24-19-generic   - Linux kernel image for version 2.6.24 on x
p   linux-image-2.6.24-19-openvz    - Linux kernel image for version 2.6.24 on O
p   linux-image-2.6.24-19-rt        - Linux kernel image for version 2.6.24 on I
p   linux-image-2.6.24-19-server    - Linux kernel image for version 2.6.24 on x
p   linux-image-2.6.24-19-virtual   - Linux kernel image for version 2.6.24 on x
p   linux-image-2.6.24-19-xen       - Linux kernel image for version 2.6.24 on T

---

### Post by pespin on 2008-06-22
Bé, si t'hi fixes els que tenen una "i" davant són els nuclis que tens instal·lats. Són aquests:

> 
i linux-image-2.6.20-16-generic - Linux kernel image for version 2.6.20 on x
i linux-image-2.6.22-14-generic - Linux kernel image for version 2.6.22 on x
i linux-image-2.6.24-18-generic - Linux kernel image for version 2.6.24 on x
i linux-image-2.6.24-19-generic - Linux kernel image for version 2.6.24 on x


El que has de fer és desinstal·lar tots els que no necessitis (normalment tots menys l'últim). Això és fa amb:

```
sudo aptitude remove linux-image-2.6.20-16-generic linux-image-2.6.22-14-generic linux-image-2.6.24-18-generic
```

En desintal·lar els nuclis ja no huarien d'aparèixer tantes entrades al iniciar :)

---

