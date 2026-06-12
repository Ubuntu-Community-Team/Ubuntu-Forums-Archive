---
title: "Hardware Wireless Problems"
date: 2005-05-11
forum: Desktop Environments
---

### Post by KriC on 2005-05-11
Hi
i installed kubuntu 5.04 hoary and i got some problems with my pcmcia.
it is a netgearWG511. i downloaded ndiswrapper and installed drivers for windows,
after i had loaded in the linux kernel the drivers with modprobe ndiswrapper, i tried to insert
the pcmcia in my laptop but it wasn't responding. It even didn't turn on by itself.
further i tried to modify /etc/network/interfaces but it was still turned off, even with ifup eth1
but nothing happens.
please, help me

thanks


KriC

---

### Post by spd106 on 2005-05-11
Hi, look at this thread [http://www.ubuntuforums.org/showthread.php?t=21505](http://www.ubuntuforums.org/showthread.php?t=21505)

also try the Ndiswrapper howto in the wiki
[http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto](http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto)

If your still having trouble please post more detailed information, such as the results of
```
$ndiswrapper -l 
```

or possibly

```
$dmesg | grep ndiswrapper
```
if there's something of note.

Hope this helps

---

### Post by KriC on 2005-05-11
the result for ndiswrapper -l is
Installed ndis drivers:
netwg511        driver present, hardware present
and for dmesg | grep ndiswrapper is
ndiswrapper version 1.1 loaded (preempt=yes,smp=no)
but i noticed that the shell produced that after i made modprobe ndiswrapper;
if i typed it before it showed nothing.
that make me think that when linux boot, the kernel don't load the modules for ndiswrapper
and i have to do it everytime i turn on my laptop.
but i don't know how to make my kernel load ndiswrapper modules at boot
 ](*,)  ](*,)  ](*,)  ](*,)  ](*,) 


KriC

---

### Post by poofyhairguy on 2005-05-11
[QUOTE=KriC]
but i don't know how to make my kernel load ndiswrapper modules at boot
 ](*,)  ](*,)  ](*,)  ](*,)  ](*,) 


KriC[/QUOTE]

modprobe ndiswrapper

---

### Post by KriC on 2005-05-11
i tried to do modprobe ndiswrapper and, after that, i typed lsmod and ndiswrapper there is
but when i reboot my laptop the modules for ndiswrapper there aren't.
that's why i don't know how to make my kernel load ndiswrapper modules at boot

---

### Post by spd106 on 2005-05-12
Hi, Have you tried
```
$sudo ndiswrapper -m
```

This adds ndiswrapper to the /etc/modules file, which contains the names of all the modules the kernel loads at boot.

---

### Post by KriC on 2005-05-13
ok, got it 'cause i haven't kernel sources.
after downloaded the sources everything's gone very well.
thank you so much for the help

bye


KriC

---

