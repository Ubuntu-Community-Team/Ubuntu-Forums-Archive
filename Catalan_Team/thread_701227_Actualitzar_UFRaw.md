---
title: "Actualitzar UFRaw"
date: 2008-02-19
forum: Catalan Team
---

### Post by lluisalguero on 2008-02-19
Hola,
estic intentant actualitzar el UFRaw, però no sé com fer-ho, fa estona que dono tombs per internet i per fòrums i no hi veig la forma de sortir-me'n
Actualment estic fent servir la versió 0.11 del UFRaw i pel que m'ha semblat entendre els arxius RAW de la meva càmara (Canon EOS 40D), aquesta versió no la suporta, em surten uns colors molt distorsionats.
Concretament el programe em diu:
```
There ara not white balance presets for your camera model.
Check UFRaw's webpage for information on how to get your camera supported
```

Mirant a la web de UFRaw he anat remenant i pel que he entés necesito la versió 0.13. He mirat al Synaptic i només hi fica la versió 0.11. M'he baixat la 0.13 (paquet. deb) i em dona un error al voler instalar-lo:[COLOR="Red"] Error: Depency is not satisfiable: libc6[/COLOR]

Pel que entenc, necesito aquest arxiu que hi depen: libc6. Com que encara no domino massa el tema, he fet (segurament que malament):

```
lluis@lluis-laptop:~$ sudo apt-get install libc6
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
Reading state information... Fet           
libc6 ja es troba en la versió més recent.
0 actualitzats, 0 nous a instal·lar, 0 a eliminar i 2 no actualitzats.
lluis@lluis-laptop:~$ 

```

I em sobta que diu que ja tinc la versió més recent...i ha estat aquí quan ja m'he perdut...Alguna suggerència?

---

### Post by patrickfromspain on 2008-02-19
d'on t'has baixat el deb? Segurament deu estar compilat per gutsy o per debian testing, que fan servir un libc6 mes nou.

salut!

---

### Post by lluisalguero on 2008-02-19
L'he baixat d'aquí
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=ufraw&subword=1&version=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=ufraw&subword=1&version=all)

és la 0.13-1build1: amd64 i386 powerpc ja que he vist que és l'única que fica que és la v0.13

---

### Post by papapep on 2008-02-19
T'has baixat la versió per Hardy...tu tens Hardy posat o Gutsy???

---

### Post by lluisalguero on 2008-02-19
> **papapep said:**
> T'has baixat la versió per Hardy...tu tens Hardy posat o Gutsy???

Tinc Gutsy instal·lat, i ja sé que m'he baixat la versió per a Hardy...però és que és l'única que veig que és la 0.13 !!!

---

### Post by patrickfromspain on 2008-02-19
doncs t'hauras d'esperar a que et posis hardy.... o compilar-la tu mateix.

salut!

---

### Post by papapep on 2008-02-19
Per cert Lluís, i fent servir l'afegit de l'ufraw pel Gimp i modificant el balanç de blancs des d'el mateix programa no t'aniria bé?? Ho dic com a alternativa.

---

### Post by lluisalguero on 2008-02-19
Patrick: crec que m'esperaré al Hardy...mentrestant faré anar el ACR en WXP

papapep: he estat mirant a web de fotografia on estic suscrit, i m'han confirmat que es un problema que no va resoldre el creador del programa (o al menys això és el que m'entés)

---

### Post by papapep on 2008-02-19
Però un cop hagis importat la fotografia en format raw amb l'extensió ufraw pel Gimp, què t'impedirà ajustar el balanç de blancs amb les eines del Gimp mateix? o se m'escapa alguna cosa?

---

