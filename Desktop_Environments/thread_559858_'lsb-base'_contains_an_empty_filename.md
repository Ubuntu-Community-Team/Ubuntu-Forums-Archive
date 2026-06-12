---
title: "'lsb-base' contains an empty filename"
date: 2007-09-25
forum: Desktop Environments
---

### Post by macro182 on 2007-09-25
Hi!

I've upgraded to Gutsy, after 2 days I get this error while I try to update my packages:

```
comune@ubuntu:~$ sudo apt-get upgrade
Lettura della lista dei pacchetti in corso... Fatto
Generazione dell'albero delle dipendenze in corso       
Reading state information... Fatto               
I seguenti pacchetti saranno aggiornati:
  libnm-glib0 libnm-util0 linux-headers-generic linux-image-386
  linux-image-generic network-manager xkb-data
7 aggiornati, 0 installati, 0 da rimuovere e 0 non aggiornati.
È necessario prendere 0B/998kB di archivi. 
Dopo l'estrazione, verranno occupati 0B di spazio su disco.
Continuare [S/n]? s
(Lettura del database ... dpkg: errore processando /var/cache/apt/archives/xkb-data_0.9-4ubuntu2_all.deb (--unpack):
 il file con la lista dei file del pacchetto `lsb-base' contiene un filename vuoto
Sono occorsi degli errori processando:
 /var/cache/apt/archives/xkb-data_0.9-4ubuntu2_all.deb
L'operazione è stata bloccata perché si sono verificati troppi errori.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

So I try to clean cache, reconfigure lsb-base, dpkg --configure -a,  but I always received the same error!

I'm in trouble, please help me! ;)

---

### Post by macro182 on 2007-09-26
Any advice? :p

P.S.
Probably I wrote in a wrong place, can I move this post on gutsy's section?

---

### Post by mlissner on 2007-10-26
I have pretty much the same problem. I'm fairly certain I didn't do anything to provoke it, and I have been running gutsy with no problems for a few weeks now (since beta).

---

