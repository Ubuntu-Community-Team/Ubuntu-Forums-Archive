---
title: "libplasma2 is broken in KDE 4.2"
date: 2009-02-01
forum: Desktop Environments
---

### Post by yangcheng on 2009-02-01
Hi, I am using kubuntu 8.10.
I upgraded to kde4.2 recently , however, I have some problems while install plasmoid-* .

The following packages have unmet dependencies:
  plasmoid-kepas: Depends: libplasma2 but it is not going to be installed
E: Broken packages


and for libplasma2 , I got the following error:

 sudo apt-get install libplasma2
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libplasma2: Depends: kdebase-workspace-libs4+5 but it is not going to be installed
              Depends: kdebase-workspace-data (= 4:4.1.3-0ubuntu1~intrepid1) but 4:4.2.0-0ubuntu1~intrepid1~ppa5 is to be installed
E: Broken packages

how can I solve this problem? thanks

---

### Post by pritamps on 2009-02-01
Hey,

I think with KDE 4.2, libplasma3 comes installed and they asked to uninstall all old plasmoids before you upgraded. But I'm not sure if you can install the old plasmoids again...

---

### Post by yangcheng on 2009-02-02
> **pritamps said:**
> Hey,

I think with KDE 4.2, libplasma3 comes installed and they asked to uninstall all old plasmoids before you upgraded. But I'm not sure if you can install the old plasmoids again...

libplasma3 Replaces: kdebase-workspace-data (<< 4:4.1.73-0ubuntu1), libplasma1, libplasma2

However, all plasmoid-* but plasmoid-quickaccess depends on libpasma2.

It seems I should wait a while until they rebuild all the packages?

---

### Post by gearangelus on 2009-02-07
-in bad english-

I've exactly the same throuble... the thing is.. that i've installed ubuntu 8.10 server.

I put the line on my sources.list, get the pgp key.


Then i made an aptitude install kubuntu-desktop, update and upgrade everithing

Later i've been install my envy, theres no throuble anyway. 3d full.

Just traying to install compiz-kde, the dependency with libplasma2, it's there. I don't know what to do.

-it is a pretty bad english-

Thanks if 'u drop me the answer.

---

### Post by Tiftof on 2009-02-11
I wanted to try kde 4.2 on my ubuntu intrepid setup but I'm getting the same problem. The ppa isn't fixed yet then?

---

