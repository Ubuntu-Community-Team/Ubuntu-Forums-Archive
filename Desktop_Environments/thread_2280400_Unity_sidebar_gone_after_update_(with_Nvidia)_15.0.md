---
title: "Unity sidebar gone after update (with Nvidia) 15.04"
date: 2015-05-30
forum: Desktop Environments
---

### Post by pt3lford on 2015-05-30
Hi,
Every couple of weeks one of the regular updates seems to break my install. Typically this results in me re-running the NVIDIA installer and all is well.

This time re-running the installer has given me back the ability to log in, but unity has disappeared (the side bar and top bar). I'm currently using twm as a workaround, but its not ideal.

My .xsession-errors has the following:

```
upstart: upstart-event-bridge main process (1914) terminated with status 1
upstart: upstart-event-bridge main process ended, respawning
upstart: upstart-event-bridge main process (1936) terminated with status 1
upstart: upstart-event-bridge main process ended, respawning
..
upstart: at-spi2-registryd main process ended, respawning
upstart: at-spi2-registryd main process ended, respawning
upstart: unity7 main process (2053) killed by KILL signal
upstart: unity7 main process ended, respawning
upstart: unity7 main process (2533) terminated with status 1
upstart: unity7 main process ended, respawning
..
upstart: unity7 respawning too fast, stopped
upstart: update-notifier-crash (/var/crash/_usr_share_apport_apport-gtk.0.crash) main process (1945) terminated with status 1
upstart: indicator-bluetooth main process (2107) killed by TERM signal
upstart: indicator-power main process (2108) killed by TERM signal
upstart: indicator-datetime main process (2109) killed by TERM signal
upstart: indicator-printers main process (2113) killed by TERM signal
upstart: indicator-session main process (2114) killed by TERM signal
upstart: indicator-application main process (2125) killed by TERM signal

and I have a _usr_lib_unity_unity-panel-service.2000.crash file in /var/crash

Trying to start unity from a terminal seems to hang around here:

compiz (core) - Info: Starting plugin: session
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: commands
compiz (core) - Info: Starting plugin: commands
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
```

Not really sure where to start. I have tried apt-get update, package repair, but so far no real progress.

Thanks,
Peter.

---

### Post by wildmanne39 on 2015-05-30
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by buzzingrobot on 2015-05-30
Tell us about your hardware, especially the video card, which Nvidia driver is installed, and how you installed it.

---

