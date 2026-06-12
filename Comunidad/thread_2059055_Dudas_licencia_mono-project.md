---
title: "Dudas licencia mono-project"
date: 2012-09-17
forum: Comunidad
---

### Post by sebasthian777 on 2012-09-17
Hola que tal, hace mucho que no posteo por aca, pero queria sacarme unas dudas (espero estar posteando en el subforo correcto)

Tengo un proyecto para realizar con un amigo, es una posibilidad laboral interesante, cuestion que nos solicitaron desarrollar un software bastante amplio y teniamos ganas de hacerlo sobre mono-develop con mono.

Y nos entro la duda de si podemos realmente vender software realizado sobre esta tecnologia. 

Alguno ya averiguo sobre esto? o tiene idea de como es?

Nuestro problema es que somos muy tecnicos y no entendemos todas las clausulas legales que conlleva mono...

Desde ya mil gracias :D

link de interes:
[http://www.mono-project.com/FAQ:_Licensing]("http://www.mono-project.com/FAQ:_Licensing")

---

### Post by clasificado on 2012-09-19
Respuesta rápida: SI. se puede vender software compilado con mono. 

Más precisamente hablando, se puede distribuir software compilado con mono sin necesidad de pagar regalías, siempre y cuando la dependencia con MONO sea dinámica.

Osea que el destino debe tener mono preinstalado

¿Y cuando hay que pagar? Cuando tu software necesita linkear de manera estática al libmono.so, por lo que también necesita distribuir MONO. Ahi ya si hay que pagar.

¿Cuando sucede esto? En pc no pasa nunca. Uno exige como requisito que mono esté preinstalado y el manejador de paquetes instala primero mono, y despues tu software. entonces no pasa nada

En android e iphone estás al horno. el manejador de paquetes no maneja nada, y es imposible instalar mono en el sistema, entonces hay que distribuirlo si o si (MonoTouch, o Mono for Android) y ahi tarasca

---

