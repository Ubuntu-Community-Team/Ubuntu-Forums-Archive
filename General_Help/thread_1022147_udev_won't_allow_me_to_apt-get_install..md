---
title: "udev won't allow me to apt-get install."
date: 2008-12-26
forum: General Help
---

### Post by Taidgh on 2008-12-26
Whenever I try to 'sudo apt-get install' anything, I get this:
```
Setting up udev (124-9) ...
dpkg: error processing udev (--configure):
 failed in buffer_read(fd): md5hash: Input/output error
Errors were encountered while processing:
 udev
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
My laptop freezes for a while after 'Setting up udev (124-9) ...'.
Pretty much the same thing happens after the Synaptic Update Manager runs.
Sorry for the n00bish-ness, it's my second day with Ubuntu.

---

### Post by Taidgh on 2008-12-26
I tried using the update manager and got this error message:
```
An error occurred
The following details are provided:
E: udev: failed in buffer_read(fd) 
```
Everything seems to fail once it gets to udev. What to do?

---

### Post by Taidgh on 2008-12-27
Is there any way for me to install or remove programs? This has rendered my system useless.

---

### Post by Taidgh on 2008-12-28
Bump.

---

### Post by Taidgh on 2008-12-29
Bumpety bump bump.

---

### Post by Taidgh on 2008-12-29
In that case, I guess I'll just format my hard drive and do a clean install of Ubuntu. Will that definitely fix the problem?

---

### Post by eborigene on 2011-07-22
I have the same problem. Didn't find any help on the net. Everbody gives hints about particular packages but not about reinstalling the apt-get itself.

Code (portuguese, sorry for those who do not understand but you can go to Google):

dpkg: erro ao processar apt (--configure):
 falha em buffer_read(fd): md5hash: Erro de Entrada/Saída de dados
Foram encontrados erros enquanto processava:
 apt
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

