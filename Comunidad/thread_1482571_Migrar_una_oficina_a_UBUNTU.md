---
title: "Migrar una oficina a UBUNTU"
date: 2010-05-13
forum: Comunidad
---

### Post by diegochaz on 2010-05-13
Buenas tardes a todos,
Ante todo me presento. Mi nombre es Diego y la verdad que estoy sumamente contento haberlos encontrado, lastima que no pude conocerlos en la reunion social pasada, la proxima estare.

Ahora al kit de la cuestion, migrar... parece una palabra que apareja dolores de cabeza pero espero que con su ayuda me sea mas facil llevar. La realidad es la siguiente, debo hacer un cambio de SO en mi Oficina y Ubuntu me parecio lo mejor de lo que he probado. 
Ahora bien, tengo 10 Computadoras WinXP en distintas areas y 3 "Servers" (1. Servidor Dominio Local Debian con EBox, 2. Servidor Archivos y Xampp en WinXP, 3. Servidor de Seguridad con 8 Camaras)

Ahora que les conte mi layout les explico lo que deseo hacer:
1. Convertir las 10PCs a Ubuntu 10.04 -> No hay Drama
2. Agarrar un Servidor e instalarle Ubuntu Server para que sea: a. Servidor de archivos de las 10 Maquinas, no FTP sino, como Active Directory para que las maquinas solo tengan el SO y las carpetas personales esten este server -> Ni Idea como...
b. Administrador de Usuarios, para que al momento de compartir entre PCs se pueda determinar a quien habilitar y los privilegios -> Ni Idea como...

Espero que puedan ayudarme y espero sus colaboraciones.
Saludo atte.

Chaz!

---

### Post by guillermolisi on 2010-05-13
> **diegochaz said:**
> Buenas tardes a todos,
Ante todo me presento. Mi nombre es Diego y la verdad que estoy sumamente contento haberlos encontrado, lastima que no pude conocerlos en la reunion social pasada, la proxima estare.

Ahora al kit de la cuestion, migrar... parece una palabra que apareja dolores de cabeza pero espero que con su ayuda me sea mas facil llevar. La realidad es la siguiente, debo hacer un cambio de SO en mi Oficina y Ubuntu me parecio lo mejor de lo que he probado. 
Ahora bien, tengo 10 Computadoras WinXP en distintas areas y 3 "Servers" (1. Servidor Dominio Local Debian con EBox, 2. Servidor Archivos y Xampp en WinXP, 3. Servidor de Seguridad con 8 Camaras)

Ahora que les conte mi layout les explico lo que deseo hacer:
1. Convertir las 10PCs a Ubuntu 10.04 -> No hay Drama
2. Agarrar un Servidor e instalarle Ubuntu Server para que sea: a. Servidor de archivos de las 10 Maquinas, no FTP sino, como Active Directory para que las maquinas solo tengan el SO y las carpetas personales esten este server -> Ni Idea como...
b. Administrador de Usuarios, para que al momento de compartir entre PCs se pueda determinar a quien habilitar y los privilegios -> Ni Idea como...

Espero que puedan ayudarme y espero sus colaboraciones.
Saludo atte.

Chaz!
Active Directory es la implementacion MS de LDAP pero LDAP/AD es para  validar/autenticar usuarios en una red, no es un file server. Para file  server podes usar Samba, que tambien te permite validar usuarios pero  con otra base (combinable con LDAP si queres). Samba permite configurar privilegios y permisos a nivel de archivos.

Configurar LDAP me parece complejo y lo propio con Samba, dependiendo de los requerimientos del contexto, tambien. No digo "no se puede", solo es laborioso y salvo que ya tengas experiencia previa y/o suficiente tiempo como para armar un ambito de prueba y experimentar, mi recomendacion es que tengas algun soporte externo que te de una mano, un envion para que te pongas en marcha.

---

### Post by granjero on 2010-05-14
Hola, yo ando en una cuestión similar.

te dejo un link de como configurar samba que me fue muy útil. yo puse un ubuntu server 9.10 en el aula de computación con una carpeta compartida para que todos los usuarios guarden data.


[http://www.guia-ubuntu.org/index.php?title=Samba](http://www.guia-ubuntu.org/index.php?title=Samba)


salud!

---

### Post by z37a on 2010-05-15
Por que usar Samba si todos los equipos van a ser Linux? el Samba creanme anda mas lento y es un tanto mas complejo que usar NFS, aparte con NFS es mas transparente, solo ven una carpeta local(que en realidad esta en el servidor!).

Yo en mi casa dispongo de un Server Ubuntu compartiendo carpetas y otras funciones a 3 equipos, no es lo mismo que en una oficina ya que somos 3 usuarios, 3 pcs, ahí son 10 pcs y de seguro 10 usuarios(o un poco mas). Y en mi caso si bien administrativamente para 3 usuarios me alcanza uso NFS, la conexión vuela, anda mas rápido que con samba, no me preguntes el por que pero así lo note(ojo hablo de un pequeño % pero que se nota!).

Si te interesa mas esta alternativa pregunta nomas que puedo subir sin drama confs y datos de mi server sobre como lo tengo configurado, lo único por ahora esta corriendo 9.10 pero en poco lo migro a 10.04. Después las desktop tengo una con 9.10 i386, otra con 10.04 i386 y otra 10.04 AMD64, o sea bien mixto en versiones de ubuntu, ahhh y el server es 9.10 AMD64 jejeje.

PD: 10 licencias de WinXP + Office son unos 500 verdes mínimo por pc, lo cual serian uno 6000 verdes(No olvidar server) mas o menos que te ahorras al usar Linux, con eso creo que podes invertir en mejorar la infraestructura de hardware de ser necesario!!! No se por que pero me gusta aclarar estas cosas, siempre se me cruza por la cabeza el ahorro que tenes al usar esto!!!

---

### Post by alfplayer on 2010-05-15
AD se puede entender como la integración de un conjunto de tecnologías como LDAP, Kerberos y CIFS. El equivalente de los home en el servidor en windows serían los "perfiles itinerantes". Para eso podría ser útil csync o directamente rsync con NFS. Para la pregunta de los privilegios depende qué tipo de privilegios se quieren controlar; no conozco una solución integrada como AD en windows pero se podría controlar por ejemplo permisos de archivos con los "POSIX ACL".

---

### Post by edudelsur on 2010-06-04
> **z37a said:**
> Por que usar Samba si todos los equipos van a ser Linux? el Samba creanme anda mas lento y es un tanto mas complejo que usar NFS, aparte con NFS es mas transparente, solo ven una carpeta local(que en realidad esta en el servidor!).

Yo en mi casa dispongo de un Server Ubuntu compartiendo carpetas y otras funciones a 3 equipos, no es lo mismo que en una oficina ya que somos 3 usuarios, 3 pcs, ahí son 10 pcs y de seguro 10 usuarios(o un poco mas). Y en mi caso si bien administrativamente para 3 usuarios me alcanza uso NFS, la conexión vuela, anda mas rápido que con samba, no me preguntes el por que pero así lo note(ojo hablo de un pequeño % pero que se nota!).

Si te interesa mas esta alternativa pregunta nomas que puedo subir sin drama confs y datos de mi server sobre como lo tengo configurado, lo único por ahora esta corriendo 9.10 pero en poco lo migro a 10.04. Después las desktop tengo una con 9.10 i386, otra con 10.04 i386 y otra 10.04 AMD64, o sea bien mixto en versiones de ubuntu, ahhh y el server es 9.10 AMD64 jejeje.

PD: 10 licencias de WinXP + Office son unos 500 verdes mínimo por pc, lo cual serian uno 6000 verdes(No olvidar server) mas o menos que te ahorras al usar Linux, con eso creo que podes invertir en mejorar la infraestructura de hardware de ser necesario!!! No se por que pero me gusta aclarar estas cosas, siempre se me cruza por la cabeza el ahorro que tenes al usar esto!!!
   

Que tal ! A mi me interesa, si tenés material que puedas compartir al respecto, hace tiempo que quiero armar una red para compartir documentos en la sala de la escuela y se me ocurre que esta es una buena opción. te aclaro que no tengo muchos conocimientos de Admin. de redes linux pero tengo muchas ganas de aprender, ha! en la sala tenemos 16 máquinas todas en red vía suich

---

