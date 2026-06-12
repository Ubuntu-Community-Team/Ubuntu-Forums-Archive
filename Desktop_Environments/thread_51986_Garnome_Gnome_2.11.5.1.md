---
title: "Garnome Gnome 2.11.5.1"
date: 2005-07-26
forum: Desktop Environments
---

### Post by SpEcIeS on 2005-07-26
I am having some difficulty compiling the latest gnome development package. Here is the error puck out:
[b]
camel.c:35:17: ssl.h: No such file or directory
camel.c: In function `camel_shutdown':
camel.c:55: warning: implicit declaration of function `NSS_Shutdown'
camel.c: In function `camel_init':
camel.c:87: warning: implicit declaration of function `NSS_InitReadWrite'
camel.c:87: error: `SECFailure' undeclared (first use in this function)
camel.c:87: error: (Each undeclared identifier is reported only once
camel.c:87: error: for each function it appears in.)
camel.c:89: warning: implicit declaration of function `NSS_NoDB_Init'
camel.c:95: warning: implicit declaration of function `NSS_SetDomesticPolicy'
camel.c:97: warning: implicit declaration of function `SSL_OptionSetDefault'
camel.c:97: error: `SSL_ENABLE_SSL2' undeclared (first use in this function)
camel.c:98: error: `SSL_ENABLE_SSL3' undeclared (first use in this function)
camel.c:99: error: `SSL_ENABLE_TLS' undeclared (first use in this function)
camel.c:100: error: `SSL_V2_COMPATIBLE_HELLO' undeclared (first use in this function)
make[6]: *** [camel.lo] Error 1
make[6]: Leaving directory `/backup/Downloads/garnome/garnome-2.11.5.1/desktop/evolution-data-server/work/main.d/evolution-data-server-1.3.5/camel'
make[5]: *** [all-recursive] Error 1
make[5]: Leaving directory `/backup/Downloads/garnome/garnome-2.11.5.1/desktop/evolution-data-server/work/main.d/evolution-data-server-1.3.5/camel'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/backup/Downloads/garnome/garnome-2.11.5.1/desktop/evolution-data-server/work/main.d/evolution-data-server-1.3.5'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/backup/Downloads/garnome/garnome-2.11.5.1/desktop/evolution-data-server/work/main.d/evolution-data-server-1.3.5'
make[2]: *** [build-work/main.d/evolution-data-server-1.3.5/Makefile] Error 2
make[2]: Leaving directory `/backup/Downloads/garnome/garnome-2.11.5.1/desktop/evolution-data-server'
make[1]: *** [../../desktop/evolution-data-server/cookies/main.d/install] Error 2
make[1]: Leaving directory `/backup/Downloads/garnome/garnome-2.11.5.1/desktop/control-center'
make: *** [paranoid-install] Error 2
[/b]
I am not really sure what is going on here, but openssl, libssl-dev and libssl are installed. Could someone help me out please?

---

### Post by Burgundavia on 2005-07-26
You are better off to track Breezy. I has all the development releases on Gnome already.

Corey

---

### Post by SpEcIeS on 2005-07-26
Perhaps, but I am only interested in compiling the developmental Gnome 2.11.5.1 for now. In theory, it should be possible, but it may be necessary to wait for the next garnome unstable package. :)

---

### Post by ubuntp on 2005-07-26
You need to install libssl-dev.

---

