---
title: "método de aprendizaje linux??"
date: 2010-05-06
forum: Comunidad
---

### Post by granjero on 2010-05-06
buenas gente. 
laburo en un instituto de enseñanza y estoy tratando de desinstalar güindows en todos lados.

ya cambié los servidores de las aulas de computación (un ubuntu server compartiendo una carpeta via samba)  y un par de máquinas de data entry. que laburan con open office y thunderbird. (mi jefe no quiso usar el evolution no se por qué)
pero siento que necesito saber más para continuar con la migración.

me interesó esto [http://www.ulteo.com/home/en/home](http://www.ulteo.com/home/en/home)

pero no me le animo con lo que se..

y ando buscando un pdf o un libro o algo para arrancar desde 0. 
que tenga ejercicios y ejemplos que me ayuden a entender...


existe tal cosa?


salud!

):P

---

### Post by Fistandantilus on 2010-05-11
Hola granjero!.
Contame un poco mas sobre como esta compuesta la red a ver si te puedo dar una mano y lo que tenes en mente.

Por ej:
- N Workstations para empleados de la institución.
- N Workstations para alumnos.
- Servidores 
  . Proxy?, Ej: Squad
  . SSO - Autenticación/Autorizaciones? Ej: OpenLDAP+Krb
  . Archivos/Directorios? Ej: Samba, NFS
  . Mail?  Ej: Zimbra


Lo de Ulteo no lo conocía, esta copado la verdad. Pero bue todo depende de que es lo que necesitas y de lo que dispones.  Si por ejemplo tenes muchas maquinas viejas capaz te conviene mas un appserver onda ulteo, citrix(es pago) o simplemente hacerlas funcionar como terminales bobas que directamente levanten un escritorio remoto a un server(con mucha ram).

Otro punto a considerar es si la red va a ser homogénea (todos linux) o heterogénea (linux y win).

Manuales? PDF? Ejecicios? mmm... mucho google :S

Saludos!.

---

### Post by DrKenobi on 2010-05-12
"Pica todos los botones hasta que te dejen ir." Homero J. Simpson

Para mi esta es una de las mejores formas de aprender, pero en tu caso tendria mas cuidado porque tu jefe se enojaria un poco.

Te paso un link que tengo hace bastante, aunque nunca lo use: [http://www.jesusda.com/docs/ebooks/index.html]("http://www.jesusda.com/docs/ebooks/index.html") Despues podes contarme q tal esta el material de esta pagina.

Suerte!

---

### Post by kmai on 2010-05-12
No se si te servirá, pero aca hay información adicional sobre Ultreo:

[http://www.ulteo.com/home/en/ovdi/openvirtualdesktop/downloadnow](http://www.ulteo.com/home/en/ovdi/openvirtualdesktop/downloadnow)

Está en inglés ya que es el sitio oficial de ultreo.

De cualquier forma, lo voy a probar en una VM a ver cómo funciona.

Saludos!

Kevin

---

### Post by granjero on 2010-05-12
gracias gente por las respuestas....

ya estuve picando todos los botones... y no es tan fácil como eso....

DrKenobi, estoy bajando unos ebooks de ahí...

kmai, yo estoy probando en una VM ulteo pero como lo que me falta a mi es la base de muchas cosas me esta costando un montón.

tengo que aprender a hacer un dominio propio para usar con ulteo. así que voy a ir a las bases primero y luego voy a volver a probar con ulteo...

salud!

---

