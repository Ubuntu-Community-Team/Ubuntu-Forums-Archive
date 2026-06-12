---
title: "subtitle editor"
date: 2006-05-01
forum: Desktop Environments
---

### Post by Smika on 2006-05-01
Hello,

I am a new user of Kubuntu and i love it very much, I install nothing yet, but I want install ksubtile_1.2-3_i386.deb. SO i do sudo -i dpkg ksubtile_1.2-3_i386.deb and then it says that i need newer files of some libs etc. SO i go to the debian webpage and download the newer version. But i cannot install it. Is there a automatic way so I can install all the lib etc by aptget or can I install it automaticly when i install ksubtile?

Thanks,

Smika

---

### Post by louis_nichols on 2006-05-01
ksubtile is in the repos, to my knowledge

so you should be able to ```
sudo apt-get install ksubtile
``` and it will solve all dependencies for you.

---

### Post by Smika on 2006-05-01
When I do what you say me, I get this error. It is in Dutch. But it says that it is not possible to install the kde;ib4, libqt3c102-mt and gcc-4.1-base. So what can I do now?

matthias@Laptop:~$ sudo apt-get install ksubtile
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
ksubtile is reeds de nieuwste versie.
U wilt waarschijnlijk 'apt-get -f install' uitvoeren om volgende op te lossen:
De volgende pakketten hebben niet-voldane vereisten:
  ksubtile: Vereisten: kdelibs4 (>= 4:3.3.1) maar het is niet installeerbaar
            Vereisten: libqt3c102-mt (>= 3:3.3.3) maar het is niet installeerbaar
  libgcc1: Vereisten: gcc-4.1-base (= 4.1.0-1+b1) maar het is niet installeerbaar
           Vereisten: libc6 (>= 2.3.6-6) maar 2.3.5-1ubuntu12.5.10.1 zal geïnstalleerd worden
E: Er zijn niet-voldane vereisten. U kunt best 'apt-get -f install' uitvoeren zonder pakketten op te geven, (of u kunt zelf een oplossing specificeren).

---

### Post by louis_nichols on 2006-05-01
Ok. i think I understand. By manually installing packages, you broke the links between the various versions of the packages and libraries. I use ubuntu, but I think Kubuntu should come with Synaptic, also (if it doesn't, I'll provide you with a command line solution, but this should be the easy way). So, what you should do is:

1. Open Synaptic package manager.
2. Select "Edit" from the menubar, then "Fix broken packages". Click ok to any confirmation dialog that comes up. Then click apply. So this should bring balance into your system again.
3. Install ksubtile from repos, either by using synaptic directly, or by using apt-get from terminal.

---

