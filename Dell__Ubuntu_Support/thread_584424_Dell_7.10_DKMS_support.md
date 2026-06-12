---
title: "Dell 7.10 DKMS support?"
date: 2007-10-21
forum: Dell  Ubuntu Support
---

### Post by carnagex420x on 2007-10-21
i just saw the newest post on the ubuntu Fridge, Dell is shipping Gutsy on there computers and have hardware driver kernel support (a.k.a. DKMS) HOWEVER, when and what support is still a question i have. there are GREAT advances in 7.10 over 7.04. but sadly like always theres still hadware problems. Is there some sort of Dell Gutsy Release Date?

---

### Post by ebozzz on 2007-10-23
> **carnagex420x said:**
> i just saw the newest post on the ubuntu Fridge, Dell is shipping Gutsy on there computers and have hardware driver kernel support (a.k.a. DKMS) HOWEVER, when and what support is still a question i have. there are GREAT advances in 7.10 over 7.04. but sadly like always theres still hadware problems. Is there some sort of Dell Gutsy Release Date?

If you search for DKMS in the Synaptic package manager, you will find that it is available for install......

---

### Post by carnagex420x on 2007-10-29
i have the dkms package installed, but dont i need to configure modules for it or sumthing? i read and re-read pages but idk what to do.:(

---

### Post by john_hull-DELL on 2007-10-29
DKMS by itself doesn't do anything. It's a framework for installing/managing out-of-kernel drivers and driver updates, and thus driver update packages would use it. For example, if you want to install a newer tg3 driver on your system, someone could take the newer driver source code and use DKMS to build and package the driver, and then load it on your system.

---

### Post by carnagex420x on 2007-10-30
so its just a waiting game on Dell? I assume, because if the drivers were free i wouldnt be having this problem.

---

### Post by john_hull-DELL on 2007-10-30
What problems are you having with your hardware? The only additional driver we have to release for 7.10 is a Conexant modem driver, since it's closed-source. Everything else should already be in the OS

---

### Post by carnagex420x on 2007-10-30
I was having a problem with my sound card and having multiple applications using it at once. I accualy found help on a Dell 1520 Feisty Thread, so thats fine, except i only get 1 audio out , not 2. I cant get my multimedia keys  to work eigther, but that wasnt as important. I also am unsure if my Card reader is functional in Gutsy because i havent had a chance 2find out.

---

### Post by Tensho on 2007-11-07
> **john_hull-DELL said:**
> The only additional driver we have to release for 7.10 is a Conexant modem driver, since it's closed-source.

Indeed. I'm eagerly (impatiently :P) waiting for this one! Have you got any idea when it might be out? Just out of curiosity, why aren't these Conexant drivers open-source? If it's not possible to have it out for everyone to see... I'm quite certain it would be more beneficial for Dell to have a modem with out of the box support for Linux. I know there are business agreements and contracts keeping ties between the two companies, but I'm sure it wouldn't be too much a hassle to include another brand of (Linux-supported) modems available for selection when one customises their computer online as I did? :)

Great job on supporting Linux, by the way. It's the main reason why I got myself an Inspiron 1520. :)

---

### Post by ebozzz on 2007-11-07
> **Tensho said:**
> Indeed. I'm eagerly (impatiently :P) waiting for this one! Have you got any idea when it might be out? Just out of curiosity, why aren't these Conexant drivers open-source? If it's not possible to have it out for everyone to see... I'm quite certain it would be more beneficial for Dell to have a modem with out of the box support for Linux. I know there are business agreements and contracts keeping ties between the two companies, but I'm sure it wouldn't be too much a hassle to include another brand of (Linux-supported) modems available for selection when one customises their computer online as I did? :)

Great job on supporting Linux, by the way. It's the main reason why I got myself an Inspiron 1520. :)


+1 

I didn't go with an Inspiron but the fact that Dell supported Linux was a **huge** factor with my decision to go with a Vostro 1500.

---

