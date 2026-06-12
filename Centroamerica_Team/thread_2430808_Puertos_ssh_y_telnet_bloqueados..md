---
title: "Puertos ssh y telnet bloqueados."
date: 2019-11-07
forum: Centroamerica Team
---

### Post by fmendoza5190 on 2019-11-07
Buenas tardes estimados.

Tengo un inconveniente con un servidor en producción con ubuntu server 9.04 :frown:](*,).

El cual estaba funcionando correctamente, pero por cuestiones de mantenimiento físico se tuvo que reiniciar :mrgreen:. Cuando inicio el servidor todo parecía normal, hasta el momento en que me quise conectar vía ssh que no funciono. Verifique el servicio del ssh y al reiniciarlo no mostraba ningun mensaje de error ni funcionaba. Verifique los puertos que estaban abiertos y extrañamente los puertos 22 y 23 no estaban habilitados, procedi a agregar los puertos al iptables y aun así no funcionaba.:cry: Como ultima opción reinstale el servicio de ssh y luego instale openshh server. Sin obtener frutos que procedimiento puedo seguir aparte de los ya mencionados?

De antemano muchas gracias. :D

---

### Post by TheFu on 2019-11-07
9.04 apoyo acabado en 2010!

18.04 es el actual "LTS", Apoyo de Plazo Largo, lanzamiento.
Existen grandes riesgos al ejecutar versiones no compatibles.

[https://ubuntu.com/about/release-cycle](https://ubuntu.com/about/release-cycle) explanar

** from google translate.  I hope the result isn't too lost-in-translation.

---

### Post by uRock on 2019-11-07
¿Quiso decir 19.04 (2019) o 9.04 (2009)?

---

### Post by fmendoza5190 on 2019-11-08
9.04 (2009) :(

---

### Post by uRock on 2019-11-08
Fue un lanzamiento impresionante, pero muy anticuado.

Una instalación limpia de 18.04LTS o 19.10 debería darle un sistema de trabajo.

---

