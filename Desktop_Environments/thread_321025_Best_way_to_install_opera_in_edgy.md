---
title: "Best way to install opera in edgy"
date: 2006-12-18
forum: Desktop Environments
---

### Post by jferrando on 2006-12-18
What is the best way to install opera browser in edgy?
I have tryed adding the opera repository, but I get one error:

[FONT="Courier New"]deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free[/FONT]

[FONT="Courier New"]#apt-get update
...
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) edgy-backports/multiverse Sources
Descargados 1061B en 1s (887B/s)
Leyendo lista de paquetes... Hecho
**W: GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 033431536A423791**
W: Tal vez quiera ejecutar 'apt-get update' para corregir estos problemas
root@portjordi2:/etc/apt# apt-get install opera
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo información de estado... Hecho
No se pudieron instalar algunos paquetes. Esto puede significar que
usted pidió una situación imposible o, si está usando la distribución
inestable, que algunos paquetes necesarios no han sido creados o han
sido movidos fuera de Incoming.

Como sólo solicito una única operación, es extremadamente posible que el
paquete simplemente no sea instalable y debería de rellenar un informe de
error contra ese paquete.
La siguiente información puede ayudar a resolver la situación:

Los siguientes paquetes tienen dependencias incumplidas:
  **opera: Depende: libqt3c102-mt (>= 3:3.2.1) pero no es instalable**
E: Paquetes rotos
root@portjordi2:/etc/apt#[/FONT]

Any idea?

---

### Post by Jimi... on 2006-12-18
I installed it last night, all I did was download it from the Opera website, opened it and clicked install. Didn't bother using terminal to do it though.

---

### Post by paparucino on 2006-12-18
> **jferrando said:**
> 

Did you try to install that library?

---

