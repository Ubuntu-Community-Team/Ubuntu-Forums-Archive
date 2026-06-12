---
title: "Console Only ?"
date: 2005-03-27
forum: Desktop Environments
---

### Post by WickedKlown on 2005-03-27
How Do i Disable X and GDM i only want console

---

### Post by dcraven on 2005-03-27
Give this a shot:
```

# update-rc.d gdm remove

```
Now gdm won't start when you restart the machine. To kill it when it's already running (ie. you are in GNOME now), just type
```

# /etc/init.d/gdm stop

```
That'll kill it dead.

HTH,
~djc

---

### Post by WickedKlown on 2005-03-27
THANKS!!!! see i got my NIX box om my lan and i just access it over ssh so i dident need X running takeing up CPU & MEM  iis there a way to login 2 x over lan if i ever needed it ?

---

### Post by dcraven on 2005-03-27
I would imagine 
```

# /etc/init.d/gdm start

```
would do it. Then ssh with the -X flag like this
```

# ssh -X [remotehost]

```
Then any X apps should be forwarded to your local machine's display.

HTH,
~djc

---

### Post by ubuntu_demon on 2005-04-02
[QUOTE=dcraven]I would imagine 
```

# /etc/init.d/gdm start

```
would do it. Then ssh with the -X flag like this
```

# ssh -X [remotehost]

```
Then any X apps should be forwarded to your local machine's display.

HTH,
~djc[/QUOTE]
 isn't vnc or freenx a better option ?

---

### Post by dcraven on 2005-04-02
[QUOTE="demon666_nl"] isn't vnc or freenx a better option ?[/QUOTE]
I don't think so, but of course it depends on your usage patterns or habits. If you want to use the remote machine as a desktop, then I think you are correct. But if you only want to see the output of one specific program and remain at the command line then there isn't as much point to adding the extra latency.

Cheers,
~djc

---

### Post by ubuntu_demon on 2005-04-02
[QUOTE=dcraven]I don't think so, but of course it depends on your usage patterns or habits. If you want to use the remote machine as a desktop, then I think you are correct. But if you only want to see the output of one specific program and remain at the command line then there isn't as much point to adding the extra latency.

Cheers,
~djc[/QUOTE]
 I don't think it adds much extra latency as vnc compresses (and freenx even more compresses)

---

