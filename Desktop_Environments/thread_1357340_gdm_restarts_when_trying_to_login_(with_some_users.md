---
title: "gdm restarts when trying to login (with some users)"
date: 2009-12-17
forum: Desktop Environments
---

### Post by electronpositivo on 2009-12-17
I am curious thing happens with some users when trying to log on gdm. It is cloned equipment that I've changed the hostname and network settings by accessing a server ldap users.

The fact is that sometimes some users log on, apparently without giving any error. Simply reload gdm and falls again with the login screen. I solve it by deleting your home and when they try to log back there no problem (up to log a few days later).

I looked at the file. Xsession-errors of the users that this happens and this is its content:

```
 /etc/gdm/Xsession: Beginning session setup…
    Setting IM through im-switch for locale=es_ES.
    Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
    GNOME_KEYRING_SOCKET=/tmp/keyring-XvamQ6/socket
    SSH_AUTH_SOCK=/tmp/keyring-XvamQ6/socket.ssh
    GNOME_KEYRING_PID=1690

    (gnome-settings-daemon:1688): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL’ failed
    Unable to find a synaptics device.
    Checking for Xgl: not present.
    xset q doesn’t reveal the location of the log file. Using fallback /var/log/Xorg.0.log
    No whitelisted driver found
    aborting and using fallback: /usr/bin/metacity
    Advertencia del gestor de ventanas: Ocurrió un error al leer el archivo de sesión guardado /home/alumnos/4ESO/hovik/.config/metacity/sessions/1044222046c0e7bca7125985454573561100000016230025.ms: Ha ocurrido un error al abrir el archivo «/home/alumnos/4ESO/hovik/.config/metacity/sessions/1044222046c0e7bca7125985454573561100000016230025.ms»:·No existe el fichero ó directorio
    No se puede abrir el visor:
    Ejecute «gnome-panel –help» para ver una lista completa de las opciones de línea de órdenes.
    gnome-session: Fatal IO error 11 (Recurso temporalmente no disponible) on X server :0.0.
    gnome-settings-daemon: Fatal IO error 104 (Conexión reiniciada por el par) on X server :0.0.
    Advertencia del gestor de ventanas: Error fatal de E/S 11 (Recurso temporalmente no disponible) en la pantalla «:0.0».
```

Any idea?

---

