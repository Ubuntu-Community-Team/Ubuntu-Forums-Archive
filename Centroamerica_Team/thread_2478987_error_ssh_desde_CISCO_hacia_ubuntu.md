---
title: "error ssh desde CISCO hacia ubuntu"
date: 2022-09-11
forum: Centroamerica Team
---

### Post by zamorojo on 2022-09-11
buenas amig@s: 

tengo problemas a la hora de hacer ssh desde equipos CISCO hacia mi Ubuntu 22.04.1, tengo que hacer copias SCP desde maquina cisco y guardarlas en mi repositorio dentro de Ubuntu. 

ssh Ubuntu ==> Cisco = OK
ssh Cisco ==> Ubuntu  = Fail

error es el siguiente:
[Connection to 192.168.11.126 aborted: error status 0]
C2960C#
*Jan  2 00:40:13.830: %SSH-3-NO_MATCH: No matching kex algorithm found: client diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1 server curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,sntrup761x25519-sha512@openssh.com,diffie-hellman-group-exchange-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512,diffie-hellman-group14-sha256

he modificado mi archivo ssh_config varias veces pero no consigo sacarlo..
. alguien queme pueda orientar ..... Gracias !!!!

---

