---
title: "Gnome start up is very slow"
date: 2005-08-26
forum: Desktop Environments
---

### Post by toships on 2005-08-26
Hi all,

After I input my login information it takes a long time to launch the gnome desktop. There is an unusually large delay during the "session-manager" launch (seen on the splash screen). I am not sure what caused this but earlier it used to be much faster, but now I have to wait about 2-3 minutes on this. 

I am attaching the contents .xsession-errors file below

 -----
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "santosh"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/unknown:/tmp/.ICE-unix/19071
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
--------

Thanks in advance.
Santosh.

---

### Post by toships on 2005-08-26
Sorry forgot to add, I am using Hoary distribution.

---

### Post by ACK!! on 2005-08-26
[QUOTE=toships]Hi all,

After I input my login information it takes a long time to launch the gnome desktop. There is an unusually large delay during the "session-manager" launch (seen on the splash screen). I am not sure what caused this but earlier it used to be much faster, but now I have to wait about 2-3 minutes on this. 

I am attaching the contents .xsession-errors file below

 -----
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "santosh"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/unknown:/tmp/.ICE-unix/19071
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
--------

Thanks in advance.
Santosh.[/QUOTE]


I have the same errors but my gnome opens as quickly or slowly (depending on your point of view) as it ever has.

---

