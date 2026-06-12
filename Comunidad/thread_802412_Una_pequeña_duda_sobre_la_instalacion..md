---
title: "Una pequeña duda sobre la instalacion."
date: 2008-05-21
forum: Comunidad
---

### Post by rxx266 on 2008-05-21
Que tal mis queridos amigos linuxeros, estoy sorprendido todo lo que ha evolucionado este sistema operativo, hoy en dia se pueden ver las ventajas, y beneficios que trae este sistema operativo, me acuerdo en una epoca, estaba interesado en linux, quise empezar por lo mas dificil, instale mi primer distro Slackware, creo que la version 9.0, aprendi,lo basico de él como compilar un kernel agregar o quitar un driver, compilar e instalar un programa, usar internet, configurar una conexion dialup,este sistema todavia no tenia binarios para correr, o rpm puff la verdad que experimente muchisimo,lo cierto es que esa epoca inclusive en esta todos les tiene miedo la linux estoy hablando para usuarios novatos, o aquellos usuario que quiren familiarizarce con el sistema, yo tambien me consideraba 1 en esa epoca, pero quiero decirles animense todos,creo que hay un,mito o leyenda en esta comunidad, no me estoy refiriendo literalmente a la de aqui,si no a todos no se por qué lo hacen será, porque son celosos de sistema operativo,o quieren que muy pocas persona tengan acceso al sistema pero hay gente que te lo hacen ver como una utopía que nunca vas a aprender como si fuese un muro que nunca vas cruzar,yo les digo a toda a esa gente, es que no retrasen el proyecto,sinceramente no lo hangan porque estan causando un daño innecesario. Bueno me introducido un poco, ahora paso a mi pregunta, me acuerdo cuando habia instalado slackware Cree, lo instalaba es una particion primario, con un sistema de arhivo EXT3, y partcion SWAP(Archivoc de intercambio), pero me surge la duda porque estube leyendo en al pagina oficial ubuntu española cuando habla sobre la instalacion no menciona la particion SWAP, ¿Esto es algo nuevo? ¿No hace falta crearla?

[http://doc.ubuntu-es.org/Instalar_un_disco_duro](http://doc.ubuntu-es.org/Instalar_un_disco_duro)

Desde ya muchas gracias todos

---

### Post by Mister X on 2008-05-21
La particion SWAP sigue existiendo y es necesaria para que el sistema a medida que lo necesita descargue al rigido paginas que no está ulitizando y pueda cargar lo que esta por usar.
Si tenes la suficiente cantidad de RAM probablemente el sistema no necesite usar este mecanismo, pero es muy recomendable que se reserve una particion para SWAP.
Con el comando top podes ver varios datos de la memoria, inclusive la cantidad de SWAP usada

---

### Post by rxx266 on 2008-05-21
> **Mister X said:**
> La particion SWAP sigue existiendo y es necesaria para que el sistema a medida que lo necesita descargue al rigido paginas que no está ulitizando y pueda cargar lo que esta por usar.
Si tenes la suficiente cantidad de RAM probablemente el sistema no necesite usar este mecanismo, pero es muy recomendable que se reserve una particion para SWAP.
Con el comando top podes ver varios datos de la memoria, inclusive la cantidad de SWAP usada

Muchas gracias, has sido ,muy amable de tu parte. ¿El calculo es el doble de ram  que tengamos instalado?

---

### Post by oktubrer on 2008-05-21
El doble de RAM era el cálculo original, pero actualmente con los tamaños que se manejan ya no es tan así
Yo tengo 1GB de RAM y cree la swap también de 1GB, y el 90% del tiempo ni siquiera la uso, y jamás pasé del 10% de uso de swap

---

### Post by euzkoarima on 2008-05-21
> **oktubrer said:**
> El doble de RAM era el cálculo original, pero actualmente con los tamaños que se manejan ya no es tan así
Yo tengo 1GB de RAM y cree la swap también de 1GB, y el 90% del tiempo ni siquiera la uso, y jamás pasé del 10% de uso de swap

Coincido, en mis anotaciones tengo

> Conclusiones sacadas del artículo: [http://etbe.coker.com.au/2007/09/28/swap-space/](http://etbe.coker.com.au/2007/09/28/swap-space/)

1. Para máquinas con menos de 1 Gbyte de RAM: lo mismo de swap que tengas de RAM
2. Para máquinas con 2-4 Gbytes de RAM: la mitad de swap que la que tengas de RAM
3. Para máquinas con más de 4 Gbytes de RAM: 2 Gbytes de RAM como máximo.

---

### Post by rxx266 on 2008-05-22
Muchas Gracias a todos.

---

