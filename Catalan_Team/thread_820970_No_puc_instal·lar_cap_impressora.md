---
title: "No puc instal·lar cap impressora"
date: 2008-06-06
forum: Catalan Team
---

### Post by Miquel Ubuntero on 2008-06-06
bones.
Fa poc que he instal·lat de nou Ubuntu 8.04
Avui he fet: Sistema - Administració - Impressió
i no inicia el servei d'instal·lació d'impressores. Sencillament no passa res.
Es pot iniciar des de Terminal?
Sabeu què puc fer?

Moltes gracies.

---

### Post by papapep on 2008-06-07
Hauries de mirar quins paquets de cups tens instal·lats:

```
sudo aptitude search cups|grep i\ 
```

**Atenció que ha d'haver un espai en blanc darrera al barra \.**

---

### Post by orestesmas on 2008-06-07
I també si tens el cups funcionant:

```

ps axf | grep cupsd

```

Si no et surt una línia /usr/bin/cupsd, el pots iniciar amb 

```

sudo invoke-rc.d cupsys start 

```

i mira els missatges que et surten, no fos cas que dóni algun error.

---

### Post by Miquel Ubuntero on 2008-06-07
Hola Papapep.
A veure que et sembla aixó:
miquel@miquel-desktop:~$ sudo aptitude search cups|grep i\.
p   apcupsd-cgi                     - APC UPS Power Management (web interface)  
p   apcupsd-doc                     - APC UPS Power Management (documentation/ex
i   bluez-cups                      - Bluetooth printer driver for CUPS         
p   brother-cups-wrapper-ac         - Cups Wrapper drivers for ac brother printe
p   brother-cups-wrapper-bh7        - Cups Wrapper drivers for bh7 brother print
p   brother-cups-wrapper-common     - Common files for Brother cups wrapper pack
p   brother-cups-wrapper-extra      - Cups Wrapper drivers for extra brother pri
p   brother-cups-wrapper-laser      - Cups Wrapper drivers for laser brother pri
p   brother-cups-wrapper-laser1     - Cups Wrapper drivers for laser1 brother pr
p   brother-cups-wrapper-mfc9420cn  - Cups Wrapper drivers for mfc9420cn brother
i   cups-pdf                        - PDF printer for CUPS                      
i   cupsddk                         - CUPS Driver Development Kit               
i   cupsddk-drivers                 - CUPS Driver Development Kit - Driver files
i   cupsys                          - Common UNIX Printing System(tm) - server  
i   cupsys-bsd                      - Common UNIX Printing System(tm) - BSD comm
i   cupsys-client                   - Common UNIX Printing System(tm) - client p
i   cupsys-common                   - Common UNIX Printing System(tm) - common f
i   cupsys-driver-gutenprint        - printer drivers for CUPS                  
p   eggcups                         - notification area icon for printing jobs  
p   gkrellmapcupsd                  - gkrellm plugin displaying the current proc
p   gnome-cups-manager              - CUPS printer admin tool for GNOME         
i   hal-cups-utils                  - CUPS integration with HAL                 
v   libcupsimage-dev                -                                           
i   libcupsimage2                   - Common UNIX Printing System(tm) - image li
p   libcupsimage2-dev               - Common UNIX Printing System(tm) - image de
v   libcupsys-dev                   -                                           
i   libcupsys2                      - Common UNIX Printing System(tm) - libs    
p   libcupsys2-dev                  - Common UNIX Printing System(tm) - developm
i   libgnomecups1.0-1               - GNOME library for CUPS interaction        
p   libgnomecups1.0-dev             - GNOME library for CUPS interaction (header
p   libgnomecupsui1.0-1c2a          - UI extensions to libgnomecups             
p   libgnomecupsui1.0-dev           - UI extensions to libgnomecups (headers)   
p   libnet-cups-perl                - Provides an interface for printing with CU
i   python-cups                     - Python bindings for CUPS                  
v   selinux-policy-cups             -                                           
p   selinux-policy-refpolicy-cups   - Security-Enhanced Linux Reference Policy C

i a veure que diu en orestesmas, perqué a mí em sembla xino ;)

miquel@miquel-desktop:~$ ps axf | grep cupsd
 4951 ?        Ss     0:00 /usr/sbin/cupsd
 7911 pts/0    S+     0:00      \_ grep cupsd
miquel@miquel-desktop:~$ 

Ja hem direu.
Gracies moltes.

---

