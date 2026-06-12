---
title: "Mod_security compile problem ???"
date: 2005-10-16
forum: Desktop Environments
---

### Post by dbee on 2005-10-16
Why won't my mod_security compile ?

root@ubuntu:/home/apachesrc/modsecurity-1.8.7/apache1 # gcc -o mod_security.o mod_security.c
mod_security.c:31:19: httpd.h: No such file or directory
mod_security.c:32:25: http_config.h: No such file or directory
mod_security.c:33:26: http_request.h: No such file or directory
mod_security.c:34:27: http_protocol.h: No such file or directory
mod_security.c:35:23: http_core.h: No such file or directory
mod_security.c:36:23: http_main.h: No such file or directory
mod_security.c:37:22: http_log.h: No such file or directory
mod_security.c:38:25: util_script.h: No such file or directory
mod_security.c:57: error: syntax error before "MODULE_VAR_EXPORT"
mod_security.c:57: warning: data definition has no type or storage class
mod_security.c:241: error: syntax error before "request_rec"

... this goes on for almost every line of the mod_sec program

---

