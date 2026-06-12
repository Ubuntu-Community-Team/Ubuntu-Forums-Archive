---
title: "vpnclient"
date: 2006-06-08
forum: Desktop Environments
---

### Post by Smika on 2006-06-08
Hello there,

I try to install vpncleint for 2 days, but nothing works. I install the correct headers but when I type ./vpn_install they give me some errors:

Making module
make -C /lib/modules/2.6.15-23-386/build SUBDIRS=/home/vis/Desktop/vpnclient/vpnclient modules
/usr/src/linux-headers-2.6.15-23-386/scripts/gcc-version.sh: line 11: gcc: command not found
/usr/src/linux-headers-2.6.15-23-386/scripts/gcc-version.sh: line 12: gcc: command not found
make[1]: gcc: Opdracht niet gevonden
make[1]: Map '/usr/src/linux-headers-2.6.15-23-386' wordt binnengegaan
  CC [M]  /home/vis/Desktop/vpnclient/vpnclient/linuxcniapi.o
/bin/sh: gcc: command not found
make[2]: *** [/home/vis/Desktop/vpnclient/vpnclient/linuxcniapi.o] Fout 127
make[1]: *** [_module_/home/vis/Desktop/vpnclient/vpnclient] Fout 2
make[1]: Map '/usr/src/linux-headers-2.6.15-23-386' wordt verlaten
make: *** [default] Fout 2
Failed to make module "cisco_ipsec.ko".
 
Is there someoe who can help me?

Thanks a lot..

Smika

---

### Post by Smika on 2006-06-08
P.S. I have installed gcc 3.4 too and I have gcc 4.0

---

### Post by Raezel on 2006-06-08
EDIT: removed, just figured, it was vpn, not vnc

---

### Post by meng on 2006-06-08
You may have an older version of the cisco client, it is notorious for restricted kernel compatibility. Have you tried vpnc instead? It is compatible with Cisco concentrators.

---

### Post by Smika on 2006-06-08
I need this for havind internet on the university. The only manual I have is about the cisco vnc client 4.8. So that it is the reason that I want use this one. But is there someone that understand the errors?

Smika

---

### Post by meng on 2006-06-08
Well I understand that 4.8 should be the correct version for your kernel, so that refutes my theory of incompatibility. However, I use vpnc to connect to a Cisco concentrator - i.e. it ought to work for you - so that is an alternative if you cannot get the official Cisco client up and running.

As for your problem, it may be solved by:
sudo apt-get install build-essential

---

### Post by str8rekt on 2006-06-08
I use vpnc also instead of the cisco client, because you don't have to mess with the kernel at all. Also, there is a nice looking front end for vpnc called Kvpnc, although I've never gotten it to work correctly =)

---

