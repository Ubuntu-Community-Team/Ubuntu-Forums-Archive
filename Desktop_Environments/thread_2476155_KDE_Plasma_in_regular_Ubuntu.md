---
title: "KDE Plasma in regular Ubuntu"
date: 2022-06-17
forum: Desktop Environments
---

### Post by kalvaro on 2022-06-17
My employer is about to send me a new laptop (I work remotely) where I was planning to install Kubuntu LTS. Unfortunately, I was informed that the laptop would come with regular Ubuntu pre-installed (LTS, I presume, though I don't really know yet) and, due to a new company policy, that's the only distro allowed.

I know you can install Plasma in Ubuntu, but I wonder if you *should*. Do you know if it can cause stability or compatibility issues of any kind? Have you heard reports in that regard?

---

### Post by ActionParsnip on 2022-06-17
[https://computingforgeeks.com/install-kde-plasma-desktop-on-ubuntu-linux/](https://computingforgeeks.com/install-kde-plasma-desktop-on-ubuntu-linux/)

---

### Post by ActionParsnip on 2022-06-17
You don't need the PPA. The KDE / Plasma things are in the repos. On a work system I don't suggest using 3rd parties due to security concerns (Depends on your job etc) but the rest is fine.

---

### Post by guiverc on 2022-06-17
I'm a *lover* of having multiple desktops installed.  So if it was me, I'd keep the Ubuntu base & just add `kubuntu-desktop` to the system, so it was still Ubuntu, but you could choose to login & use KDE Plasma instead.

The box I'm writing this on, was originally a Ubuntu Desktop install (*artful or 17.10*).  I added onto that system Lubuntu (LXDE back then), Xubuntu (Xfce) & Ubuntu-MATE (MATE). It's now a *kinetic* system and I'm using Lubuntu (LXQt) currently.

I have a Lubuntu systems here, that co-exist with Kubuntu; those two desktops are good together as both are Qt5, and KDE has some configuration tools that really make easier some LXQt configuration..

I originally always installed Ubuntu desktops, as I could download those ISOs quota free, where as *flavors* counted in my bandwidth quota; thus I used to install Ubuntu; switch to a quota-free Ubuntu archive mirror, then install the desktop I really wanted, and if I felt I really needed to - remove the default `ubuntu-desktop` system (*which I rarely did*).  

Sure there are* costs* to have multiple Desktops installed, eg.

- more bandwidth used in upgrades, as more software gets upgraded
- menus are more complex; as this box has the following text editors:  `text editor` for Ubuntu (GNOME) desktop, `mousepad` for Xfce, `featherpad` for LXQt etc.
- more disk space is used due to additional packages installed

but to me the benefits are well worth it.  For some work flows, GNOME just works & I can decide to use it for a session when I login. On most days however GNOME just makes me want to pull my hair out; as a result it's not my usually chosen desktop; and I'm using my Lubuntu (LXQt) today.

If I was in your shoes, I'd leave Ubuntu (GNOME) desktop installed; and **add** the Kubuntu desktop you would prefer to it.  I have a number of machines here I use, and I really don't think I have a single desktop on any of them[I].

Note:  I didn't list the benefits intentionally... My intention is to offer the choice.
[/I]

---

### Post by Frogs Hair on 2022-06-17
Duplicate applications and bloat are the biggest problem with multiple desktop environments . KDE brings its own suite of applications which I like , but I'd check with your employer before proceeding.

---

### Post by mIk3_08 on 2022-06-18
> **kalvaro said:**
> My employer is about to send me a new laptop (I work remotely) where I was planning to install Kubuntu LTS. Unfortunately, I was informed that the laptop would come with regular Ubuntu pre-installed (LTS, I presume, though I don't really know yet) and, due to a new company policy, that's the only distro allowed.
I know you can install Plasma in Ubuntu, but I wonder if you *should*. Do you know if it can cause stability or compatibility issues of any kind? Have you heard reports in that regard?
If its pre installed, I'm pretty sure its already configured in the way to the maximum extent. For me, I prefer not to change the configurations because it has been already checked with the quality personnel but if you really want too, make it at your own risk. Anyway, KDE Plasma is also one of the best DE so, Good Luck Regards and cheers.

---

### Post by kalvaro on 2022-06-24
> **ActionParsnip said:**
> You don't need the PPA. The KDE / Plasma things are in the repos. On a work system I don't suggest using 3rd parties due to security concerns (Depends on your job etc) but the rest is fine.

You're right. All I had to do was [FONT=courier new]sudo apt install kubuntu-desktop[/FONT] and a I have a fully functional installation of KDE Plasma alongside with Gnome.

---

