---
title: "Ubuntu 8.04 Domain Controller (SAMBA+LDAP)"
date: 2008-12-21
forum: Ecuador Team
---

### Post by jjarrinf on 2008-12-21
Logré hacer funcionar el DC con LDAP y SAMBA en Ubuntu 8.04, tengo algunos usuarios, un pc, puedo navegar por el directorio, añadir, quitar usuarios, etc.  El PC que añadí al dominio es un Windows XP, que está registrado con toda normalidad, incluso en el grupo local de administradores pude incluir a los usuarios que están en el LDAP del Ubuntu.  

Hasta ahí todo un éxito, pero el problema es que luego de que un usuario hace logon en el Windows XP (sin problemas), trabaja normalmente y luego hace logoff, no puede volver a entrar, es como que el XP deja de ver al servidor de dominio.  Lo extraño es que pasa un tiempo y nuevamente se puede hacer logon en el Windows XP.

¿Alguien ha tenido una experiencia similar que haya logrado resolver?

---

