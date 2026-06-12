---
title: "volum de so amb la 8.04"
date: 2008-04-27
forum: Catalan Team
---

### Post by Albert Que on 2008-04-27
Bon dia,
m'he actualitzat el portàtil Toshiba satellite A200-1AG a la Ubuntu 8.04 des de la 7.10 i tinc dos problemes amb el so:

1. amb el volum a tope es continua sentint molt fluix. Sona correctament però molt baix. Tinc tots els controladors de so (a no ser que n'hi hagi algun més amagat) al màxim de volum. Amb la 7.10 no em passava.

2. si connecto els auriculars continua sonant pels altaveus (aquest problema ja el tenia amb la 7.10). Confiava que amb la nova versió ja no passés.

Algun suggeriment per arreglar-ho? pista d'on poden venir els problemes?

Agraït

---

### Post by menut on 2008-04-27
Jo no tenia cap problema al Gutsy i ara em passava el mateix que tu amb els auriculars. 

La solució és anar a "Aplicacions" > "So i vídeo" > "Control del volum" i a l'apartat que fica "Front", baixar el volum o posar-lo mut. Així, li treiem la senyal de so que arriba als altaveus frontals del portàtil.

Et deixo una captura del que he fet.

---

### Post by Albert Que on 2008-04-27
Gràcies de la resposta.
No funciona: si apago el frontal (com a la captura que poses) també deixa de sonar pels auriculars. Al revés no, si apago els auriculars (com a la captura que adjunto) deixa de sonar pels auriculars però continua sonant pels altaveus.
I el volum se sent baixíssim en els dos casos.

---

### Post by Albert Que on 2008-04-27
Arreglat el problema del volum, era una badada meva, perdoneu.

Ara em queda el de commutar frontal i auriculars, que ja s'arrossega de la versió anterior.

---

### Post by menut on 2008-04-27
Prova a sel·leccionar altres dispositius (si es que et surten) i mirar la configuració que tenen.

---

### Post by Rubunter on 2008-04-27
Jo tinc un Toshiba Satellite A200 12X i tambe em sortia el so pels dos llocs quan connectava els auriculars. Despres de molta investigacio ho vaig solucionar de la següent manera:

```
sudo gedit /etc/modprobe.d/alsa-base
```

I afegint la següent linia al final:

options snd-hda-intel model=lenovo

Guardes i reinicies.

Es possible que no et funcioni tot a la perfeccio, pero a mi des que he actualitzat al Hardy em va tot perfecte!

---

### Post by Albert Que on 2008-04-27
Efectivament. Acabava de trobar i aplicar aquesta solució per una altra banda i venia a apuntar que funciona.
O sigui que res més, confirmar que afegint aquesta línia va bé (almenys de moment).

Gràcies de nou, als dos.

---

