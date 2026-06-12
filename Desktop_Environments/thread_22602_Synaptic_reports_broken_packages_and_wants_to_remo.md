---
title: "Synaptic reports broken packages and wants to remove unbuntu"
date: 2005-03-28
forum: Desktop Environments
---

### Post by jnoreiko on 2005-03-28
I recently installed eciadsl and I've got my ADSL modem working :)

To get eciadsl to work, I had to install the pppoe package and its dependencies.

Now synaptic is telling me libc6-386 and libc6-dev are broken. Fixing these appears to involve removing ubuntu-base and ubuntu-desktop. 
Marking the broken packages for reinstallation has the same effect.

---

### Post by kassetra on 2005-03-28
> **jnoreiko]I recently installed eciadsl and I've got my ADSL modem working :)

To get eciadsl to work, I had to install the pppoe package and its dependencies.

Now synaptic is telling me libc6-386 and libc6-dev are broken. Fixing these appears to involve removing ubuntu-base and ubuntu-desktop. 
Marking the broken packages for reinstallation has the same effect.[/QUOTE]

ubuntu-desktop and ubuntu-base are just meta packages said:**
> WARNING: Some third-party binaries may not work well with these libraries.
Most notably, IBM's JDK. If you experience problems with such
applications, you will need to remove this package. 

So it *looks* like you'll be ok if you fix your broken packages...

---

### Post by jnoreiko on 2005-03-29
It also wants to remove locales and lsb.

I tried setting them all to reinstall instead and got this message:

> 
The version of the package that you want to install might be no longer available in the repository. Or there might be problems with the source of the package. Refresh the package list and check the source of the package (e.g. CD or network connection).

Unable to correct problems, you have held broken packages.Unable to correct problems, you have held broken packages.Unable to correct problems, you have held broken packages.Unable to correct problems, you have held broken packages.Unable to correct problems, you have held broken packages.Unable to lock the download directory


---

### Post by jnoreiko on 2005-03-29
I've let it remove everything it wanted to, and I seem to still be here...

---

### Post by trashbird1240 on 2006-09-26
> **jnoreiko said:**
> I've let it remove everything it wanted to, and I seem to still be here...

Is you open-office, etc., still there?

I got some broken packages and in the process of trying to install gcc, synaptic told me it would remove everything, including very recognizable stuff: ubuntu-base like you mentioned, plus open office and a bunch of other stuff that looks very essential.

Thanks,
Joel

---

