---
title: "HP NL571AA DisplayLink install to Debian Stretch"
date: 2019-02-13
forum: Debian
---

### Post by x3ua on 2019-02-13
I followed instructions below, but got only green screen.
[https://github.com/AdnanHodzic/displaylink-debian](https://github.com/AdnanHodzic/displaylink-debian)

```
$ xrandr --listproviders
Providers: number : 1
Provider 0: id: 0x46 cap: 0xb, Source Output, Sink Output, Sink Offload crtcs: 4 outputs: 3 associated providers: 0 name:Intel


```

```
$ systemctl status dlm.service
&#9679; dlm.service - DisplayLink Manager Service
   Loaded: loaded (/lib/systemd/system/dlm.service; enabled; vendor preset: enabled)
   Active: active (running) since Wed 2019-02-13 15:26:12 EET; 7min ago
  Process: 707 ExecStartPre=/bin/sh -c modprobe evdi || (dkms install evdi/4.4.24 && modprobe evdi) (code=exited, status=0/SUCCESS)
 Main PID: 721 (DisplayLinkMana)
    Tasks: 11 (limit: 4915)
   CGroup: /system.slice/dlm.service
           &#9492;&#9472;721 /opt/displaylink/DisplayLinkManager

```

```
$ uname -r
4.9.0-8-amd64

```

Does anyone know about these adapters? It should work with Linux.

---

