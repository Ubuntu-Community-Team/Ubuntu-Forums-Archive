---
title: "linux-source where ??"
date: 2006-08-12
forum: Desktop Environments
---

### Post by originof on 2006-08-12
hi to all...
If i try ```
sudo apt-get install linux-source
``` i can't find the source of kernel in /usr/src

Can anyone help me ?
This is the output of apt-get (is in italian :D )

```
manuel@ubuntu-desktop:~$ sudo apt-get install linux-source
Lettura della lista dei pacchetti in corso... Fatto
Generazione dell'albero delle dipendenze in corso... Fatto
I seguenti pacchetti NUOVI (NEW) saranno installati:
  linux-source
0 aggiornati, 1 installati, 0 da rimuovere e 0 non aggiornati.
È necessario prendere 23,4kB di archivi.
Dopo l'estrazione, verranno occupati 53,2kB di spazio su disco.
Get:1 http://security.ubuntu.com dapper-security/main linux-source 2.6.15.24 [23,4kB]
Scaricato 23,4kB in 0s (30,2kB/s)
Selezionato il pacchetto linux-source, che non lo era.
(Lettura del database ... 150989 file e directory attualmente installati.)
Spacchetto linux-source (da .../linux-source_2.6.15.24_all.deb) ...
Configuro linux-source (2.6.15.24) ...

```

](*,) ](*,)

---

### Post by asimon on 2006-08-12
After installing linux-source you should find the kernel sources in a packed archive like /usr/src/linux-source-2.6.15.tar.bz2 .

---

### Post by az on 2006-08-12
Use the linux-headers to compile stuff for your running kernel.  You do not need the full source to compile extra drivers.

---

