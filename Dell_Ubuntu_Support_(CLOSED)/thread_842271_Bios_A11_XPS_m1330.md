---
title: "Bios A11 XPS m1330"
date: 2008-06-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by atlas95 on 2008-06-27
Hello, 
I have try to extract the hdr bios from the windows package of the bios A11 but this fails, I have try firmwaretools --extract and other tools during 2h but nothing.

This bios isn't avalaible on the dell repo, could you help me please :(

---

### Post by sdennie on 2008-06-27
I actually just got notified about a BIOS update (A11) via the normal update-manager today (which was very, very cool).  I can't remember the exact directions I used to set that up but, it was similar to this: [http://direct2dell.com/one2one/archive/2007/12/05/37446.aspx](http://direct2dell.com/one2one/archive/2007/12/05/37446.aspx).  If it helps at all, the package that my machine wants to upgrade is called "system-bios-xps-m1330".  After adding the repos, maybe try:

```

sudo apt-get install system-bios-xps-m1330

```

And then continue with the firmware upgrade instructions if needed.

---

### Post by atlas95 on 2008-06-27
sudo apt-get install system-bios-xps-m1330

I can't find this packet !
:(

```

root@atlas-laptop:~#   aptitude install firmware-addon-dell
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Lecture de l'information d'état étendu      
Initialisation de l'état des paquets... Fait
Construction de la base de données des étiquettes... Fait
Aucun paquet ne va être installé, mis à jour ou enlevé.
0 paquets mis à jour, 0 nouvellement installés, 0 à enlever et 0 non mis à jour.
Il est nécessaire de télécharger 0o d'archives. Après dépaquetage, 0o seront utilisés.
Écriture de l'information d'état étendu... Fait
Running prelink, please wait...
Lecture des listes de paquets... Fait             
Construction de l'arbre des dépendances        
Lecture des informations d'état... Fait
Lecture de l'information d'état étendu      
Initialisation de l'état des paquets... Fait
Construction de la base de données des étiquettes... Fait
root@atlas-laptop:~#   aptitude install $(bootstrap_firmware -a)
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Lecture de l'information d'état étendu      
Initialisation de l'état des paquets... Fait
Construction de la base de données des étiquettes... Fait
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2850-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2850-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2815-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2815-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x283e-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x283e-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2829-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2829-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2849*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2849*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2448*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2448*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2845*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2845*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x283f*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x283f*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2841*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2841*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x10de-dev-0x0427-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x10de-dev-0x0427-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*system-bios-ven-0x1028-dev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*system-bios-ven-0x1028-dev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x4229-subven-0x8086-subdev-0x1121*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x4229-subven-0x8086-subdev-0x1121*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x14e4-dev-0x1713-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x14e4-dev-0x1713-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2832-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2832-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2831-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2831-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2830-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2830-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2836-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2836-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x284b-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x284b-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2a00-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2a00-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2834-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2834-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2835-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2835-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x283a-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x283a-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x1180-dev-0x0843-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x1180-dev-0x0843-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x1180-dev-0x0592-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x1180-dev-0x0592-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x1180-dev-0x0832-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x1180-dev-0x0832-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x1180-dev-0x0822-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x1180-dev-0x0822-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2a01*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2a01*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x1180-dev-0x0852-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x1180-dev-0x0852-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2850-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2850-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2815-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2815-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x283e-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x283e-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2829-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2829-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2849*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2849*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2448*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2448*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2845*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2845*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x283f*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x283f*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2841*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2841*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x10de-dev-0x0427-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x10de-dev-0x0427-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*system-bios-ven-0x1028-dev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*system-bios-ven-0x1028-dev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x4229-subven-0x8086-subdev-0x1121*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x4229-subven-0x8086-subdev-0x1121*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x14e4-dev-0x1713-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x14e4-dev-0x1713-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2832-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2832-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2831-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2831-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2830-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2830-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2836-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2836-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x284b-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x284b-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2a00-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2a00-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2834-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2834-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2835-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2835-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x283a-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x283a-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x1180-dev-0x0843-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x1180-dev-0x0843-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x1180-dev-0x0592-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x1180-dev-0x0592-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x1180-dev-0x0832-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x1180-dev-0x0832-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x1180-dev-0x0822-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x1180-dev-0x0822-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2a01*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x8086-dev-0x2a01*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x1180-dev-0x0852-subven-0x1028-subdev-0x0209*»
Impossible de trouver un paquet dont le nom ou la description correspond à «*pci-firmware-ven-0x1180-dev-0x0852-subven-0x1028-subdev-0x0209*»
Aucun paquet ne va être installé, mis à jour ou enlevé.
0 paquets mis à jour, 0 nouvellement installés, 0 à enlever et 0 non mis à jour.
Il est nécessaire de télécharger 0o d'archives. Après dépaquetage, 0o seront utilisés.
Running prelink, please wait...
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Lecture de l'information d'état étendu      
Initialisation de l'état des paquets... Fait
Construction de la base de données des étiquettes... Fait
root@atlas-laptop:~#   update_firmware

Running system inventory...

Searching storage directory for available BIOS updates...
Checking System BIOS for XPS M1330 - a10
	Did not find a newer package to install that meets all installation checks.

This system does not appear to have any updates available.
No action necessary.



```

I have this installed too...

```
i   dell-dup                                                            - A firmware-tools plugin for Dell DUP images                                   
i   dell-firmware-repository                                            - APT sources.list for Dell firmware images                                     
i   dell-repository-keys                                                - GPG keys for files in the Dell repositories                                   
i   dell-software-repository                                            - APT sources.list for Dell software packages
```

Help please :(

Maybe you can search this deb and give me it? Or the hdr A11 file?

---

### Post by sdennie on 2008-06-27
I'm not sure why it's not working for you.  Unfortunately, I didn't write down the way I got the BIOS updates to work but, if I'm not mistaken, I had to look in synaptic and install system-bios-xps-m1330 from there.  It now appears to be automatically updating (which, again, is incredibly cool).  I just installed the A11 BIOS via "apt-upgrade" and "update-firmware --yes" and it worked fine.

---

### Post by atlas95 on 2008-06-27
could you please so do a aptitude download system-bios-xps-m1330 and send me it?
i haven't this package.

Thanks :)

---

### Post by atlas95 on 2008-06-27
I have find it !
[http://linux.dell.com/repo/dists/cross-distro/dell-firmware/binary-i386/system-bios-xps-m1330_0.a11-1_all.deb](http://linux.dell.com/repo/dists/cross-distro/dell-firmware/binary-i386/system-bios-xps-m1330_0.a11-1_all.deb) 

I try it ! thanks

---

