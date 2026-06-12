---
title: "errores con apt-get o synaptic - dpkg is broken?"
date: 2009-04-26
forum: General Help
---

### Post by brallan on 2009-04-26
i am unable to install new programs (in intrepid) using synaptic or apt-get. It's a bit odd, as it seems to be independent of the program i am trying to install on my eeepc:

sudo apt-get install transmission returns:

```
(Leyendo la base de datos ... dpkg: error al procesar /var/cache/apt/archives/python-bittorrent_3.4.2-11.1ubuntu2_all.deb (--unpack):
 files list file for package `soprano-daemon' is missing final newline
Se encontraron errores al procesar:
 /var/cache/apt/archives/python-bittorrent_3.4.2-11.1ubuntu2_all.deb
Proceso detenido por haber demasiados errores.

```

the problem seems to be in dpkg, as it repeats itself with other programs and even if i clean out the cache using:
```

sudo apt-get clean

```

look at sudo apt-get install k3b:

```
(Leyendo la base de datos ... dpkg: error al procesar /var/cache/apt/archives/libdbus-qt-1-1c2_0.62.git.20060814-2build1_i386.deb (--unpack):
 files list file for package `soprano-daemon' is missing final newline
Se encontraron errores al procesar:
 /var/cache/apt/archives/libdbus-qt-1-1c2_0.62.git.20060814-2build1_i386.deb
Proceso detenido por haber demasiados errores.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

anyone have an idea of how to fix this?

---

### Post by danwood76 on 2009-04-26
It looks like you have an error with the package soprano-daemon.
Try reinstalling that (and only that) using synaptic to see if it helps.

---

### Post by brallan on 2009-04-27
> **danwood76 said:**
> It looks like you have an error with the package soprano-daemon.
Try reinstalling that (and only that) using synaptic to see if it helps.

thanks for your answer.

tried that, but no matter what I try to install or remove, even removing soprano-daemon, I get the same error, and dpkg exits.

It is a fresh install of intrepid eeebuntu standard 2.0
with a few .debs like skype, picassa, and jubler installed. 

i had the same problem with the last install I did, and unable to resolve it, i decided to reinstall. I kept my home directory unchanged, so i think it may be some sort of thing related to config files on my home directory?

the only thing i can think of to do is to try and reinstall apt-get or dpkg or something like that, but can synaptic or aptitude do that?

---

### Post by danwood76 on 2009-04-27
have you tried doing a dpkg reconfigure?

```

sudo dpkg reconfigure soprano-daemon

```
you can also check if the package is broken with the following:
```

sudo dpkg -C

```
or you can try and completely remove the package manually:
```

sudo dpkg --force --purge soprano-daemon

```
This last one will ignore the error and continue anyway, then it might be possible to reinstall it afterwards.

-- edit --

Forgot to mention if the backage comes back broken then you can fix it using synaptic and selecting fix broken packages from the edit menu

---

