---
title: "Problemes amb &quot;linux-image&quot; i &quot; linux-ubuntu-modules&quot;"
date: 2008-06-24
forum: Catalan Team
---

### Post by Joan Marc on 2008-06-24
> **Joan Marc said:**
> [...] tinc uns quants errors am l'ubuntu... dos d'ells són els que surten a la captura d'una actualització que vaig fer just desp&#341;es de seguir els passos del teu tutorial [...].

[[IMG]http://img403.imageshack.us/img403/1299/capturashanaplicatelscaut6.th.png[/IMG]](http://img403.imageshack.us/my.php?image=capturashanaplicatelscaut6.png)

> **papapep said:**
>  [...] Això t'està dient simplement que el paquet s'ha d'acabar de configurar. Això ha de ser d'una actualització que has d'haver fet els últims dies.

Fes:

```
sudo dpkg --configure --pending
```

i, en teoria, t'ha de solventar el problema [...].

Com dic aquí a dalt, i extret [d'aquest fil]("http://ubuntuforums.org/showthread.php?t=837439"), a una actualització quan abans havia seguit el tutorial que exposa en **patrickfromspain** em surt l'error de la captura de dalt.
La solució que proposa en **papapep** tampoc té cap resultat. Enganxo el que em surt del resultat de
```
sudo dpkg --configure --pending
```
```
gami@gami:~$ sudo dpkg --configure --pending
[sudo] password for gami: 
S'està configurant linux-image-2.6.24-19-generic (2.6.24-19.34) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.24-19.33 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.24-19.33 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
[: 25: ==: unexpected operator
exec: 25: -a: not found
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: s'ha produït un error en processar linux-image-2.6.24-19-generic (--configure):
 el subprocés post-installation script retornà el codi d'eixida d'error 2
dpkg: problemes de dependències impedeixen la configuració de linux-ubuntu-modules-2.6.24-19-generic:
 linux-ubuntu-modules-2.6.24-19-generic depèn de linux-image-2.6.24-19-generic; tot i així:
  El paquet linux-image-2.6.24-19-generic encara no està configurat.
dpkg: s'ha produït un error en processar linux-ubuntu-modules-2.6.24-19-generic (--configure):
 problemes de dependències - es deixa sense configurar
S'han trobat errors en processar:
 linux-image-2.6.24-19-generic
 linux-ubuntu-modules-2.6.24-19-generic

```

Bé, aviam si em podeu ajudar, i perdoneu per la immensa parrafada ;)

---

### Post by papapep on 2008-06-24
Primer mirem quin nucli tens funcionant:

```
uname -a
```

i quins paquets d'aquesta versió de kernel tens instal·lats:

```
sudo aptitude search 2.6.24-19|grep i\ 
```

(Assegura't de deixar un espai darrera la barra invertida "\")

---

### Post by Joan Marc on 2008-06-24
T'enganxo el que m'ha sortit de les dues ordres:
```
gami@gami:~$ uname -a
Linux gami 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux
gami@gami:~$ sudo aptitude search 2.6.24-19|grep i\ 
[sudo] password for gami: 
i   linux-headers-2.6.24-19         - Header files related to Linux kernel versi
i   linux-headers-2.6.24-19-generic - Linux kernel headers for version 2.6.24 on
i   linux-restricted-modules-2.6.24 - Non-free Linux 2.6.24 modules on x86/x86_6
gami@gami:~$
```

---

### Post by Joan Marc on 2008-06-24
Hola papapep. Em sembla que l'error ja s'ha arreglat. Com m'ha assenyalat en patrick a [l'altre fil]("http://ubuntuforums.org/showthread.php?t=837439"),he desinstal·lat el grub-gfxboot, i he tornat a instal·lar el grub. Durant l'instal·lació d'aquest m'he fixat que sortia que estava configurant i fent alguna cosa amb els paquets que abans tenia problemes, i aquest cop no ha donat cap problema. Després he provat això que m'has dit tu:
```
sudo dpkg --configure --pending
```
I no ha sortit res, per tant intueixo que ja no hi ha cap problema amb els paquets anteriors no?

Gràcies

---

### Post by patrickfromspain on 2008-06-24
merda, el que dius em sona. Em sona vagament que en algun moment de la meva curta vida ubuntera, vaig tenir alguna cosa semblant i era degut al sh o el bash. Buscare i si trobo res aviso i mirare si modifico el tutorial.

EDITO: m'ha costat, però he trobat alguna cosa al respecte:

[http://ubuntuforums.org/showthread.php?p=3523233&highlight=gfxboot+%2Fbin%2Fbash+%2Fbin%2Fsh+change#post3523233](http://ubuntuforums.org/showthread.php?p=3523233&highlight=gfxboot+%2Fbin%2Fbash+%2Fbin%2Fsh+change#post3523233) (última resposta)

[http://ubuntuforums.org/showthread.php?t=540188](http://ubuntuforums.org/showthread.php?t=540188) (3a i 4a resposta)

[http://ph.ubuntuforums.com/showthread.php?t=208855&page=57](http://ph.ubuntuforums.com/showthread.php?t=208855&page=57) (1a resposta de la pagina)

[http://www.ubuntu-es.org/index.php?q=node/78123](http://www.ubuntu-es.org/index.php?q=node/78123)

Bé, ja ni ha prou no? xD

suposo que canviaré el "joutu" i ho afegiré, que no farà mal a ningú.

salut!

---

