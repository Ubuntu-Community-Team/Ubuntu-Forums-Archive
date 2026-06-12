---
title: "KDE plasma update"
date: 2022-02-09
forum: Desktop Environments
---

### Post by jimninja on 2022-02-09
Hi, 

Ive just installed kde plasma from command line and my version is ; 5.18 (plasmashell)

I dont know why I can't have 5.23 and, I added kubuntu backports to try 5.24 but nothing happens


```
$ sudo apt upgrade kde-plasma-desktop 
Reading package lists... Done
Building dependency tree        
Reading state information... Done
kde-plasma-desktop is already the newest version (5:104ubuntu4).
Calculating upgrade... Done
```

---

### Post by #&amp;thj^% on 2022-02-09
Have a look here: [https://9to5linux.com/you-can-now-install-kde-plasma-5-23-on-kubuntu-21-10-heres-how](https://9to5linux.com/you-can-now-install-kde-plasma-5-23-on-kubuntu-21-10-heres-how)

---

### Post by jimninja on 2022-02-09
thanks but nothing happened. Check in bold

```
sudo apt update
[sudo] password for james:            
Hit:1 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal InRelease
Ign:2 [http://packages.linuxmint.com](http://packages.linuxmint.com) una InRelease                                        
Hit:3 [http://packages.linuxmint.com](http://packages.linuxmint.com) una Release                                          
Hit:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal InRelease                                   
Get:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease [114 kB]                
Hit:7 [http://deb.xanmod.org](http://deb.xanmod.org) releases InRelease                                           
Get:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates InRelease [114 kB]                  
Hit:9 [https://brave-browser-apt-nightly.s3.brave.com](https://brave-browser-apt-nightly.s3.brave.com) stable InRelease                    
Hit:10 [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu) focal InRelease    
Get:11 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-backports InRelease [108 kB]
Fetched 336 kB in 2s (182 kB/s)
Reading package lists... Done
Building dependency tree        
Reading state information... Done
All packages are up to date.
sudo apt full-upgrade
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by Bashing-om on 2022-02-09
jimninja; Hey :D

Plasma 5.24 available on Kubuntu 21.10

See: [https://kubuntu.org/news/plasma-5-24-available-on-kubuntu-21-10/](https://kubuntu.org/news/plasma-5-24-available-on-kubuntu-21-10/)

[INDENT]hope this helps
[/INDENT]

---

### Post by jimninja on 2022-02-09
> **Bashing-om said:**
> jimninja; Hey :D

Plasma 5.24 available on Kubuntu 21.10

See: [https://kubuntu.org/news/plasma-5-24-available-on-kubuntu-21-10/](https://kubuntu.org/news/plasma-5-24-available-on-kubuntu-21-10/)
[INDENT]hope this helps
[/INDENT]



thanks but nothing to upgrade, really don't know why.


```
sudo apt full-upgrade[/COLOR]
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by Bashing-om on 2022-02-09
jimninja; Hey -

You look to be running focal (20.04) - for plasma 5.24 ya need to be on release 21.10.

[INDENT]so it seems to me
[/INDENT]

---

### Post by SeijiSensei on 2022-02-09
I'm on the 22.04 development release and following the instructions at [https://kubuntu.org/news/plasma-5-24-available-on-kubuntu-21-10/](https://kubuntu.org/news/plasma-5-24-available-on-kubuntu-21-10/) works for me, too. My machine is now busily updating to 5.24.

---

### Post by QIII on 2022-02-09
@jimninja

Please use code tags around terminal commands and their results.

1. If you are using the "Reply to Thread" button, please type or paste your text, highlight the text and use the # button in the text box header. Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by guiverc on 2022-02-09
Firstly you're not using Ubuntu/Kubuntu, or an *official* Ubuntu *flavor*, but the Ubuntu based system called Linux Mint.

As I answered [elsewhere]("https://askubuntu.com/questions/1392058/kde-plasma-upgrade-to-5-23-or-5-34")

Ubuntu 20.04 LTS comes with the LTS release of Qt 5.12.8 LTS

That applies to all systems, including Kubuntu 20.04 LTS using KDE, and Lubuntu 20.04 LTS using LXQt.

- [https://kubuntu.org/news/kubuntu-20-04-lts-has-been-released/](https://kubuntu.org/news/kubuntu-20-04-lts-has-been-released/)
- [https://lubuntu.me/focal-3-released/](https://lubuntu.me/focal-3-released/)

To use later KDE Plasma versions, would require upgrading the Qt5 version off the LTS path (Qt 5.12.8 LTS was still the *latest* LTS offering of Qt5 at the time), which is offered via

- Kubuntu 20.10, Ubuntu Studio 20.10 or Lubuntu 20.10
- Kubuntu 21.04, Ubuntu Studio 21.04 or Lubuntu 21.04
- Kubuntu 21.10, Ubuntu Studio 21.10 or Lubuntu 21.10

Any change to Qt5 version would mandate all Qt5 apps be recompiled; and works against the *stable* release model used by Ubuntu (and *flavors*). It also mandates all teams do the change; as Qt5 is used by more than just Kubuntu, and would pull Qt5 from the LTS path mandating regular changes (*as fits a non-LTS release offered by 20.10, 21.04, 21.10 etc*).

---

### Post by jimninja on 2022-02-10
> **SeijiSensei said:**
> I'm on the 22.04 development release and following the instructions at [https://kubuntu.org/news/plasma-5-24-available-on-kubuntu-21-10/](https://kubuntu.org/news/plasma-5-24-available-on-kubuntu-21-10/) works for me, too. My machine is now busily updating to 5.24.

on ubuntu or kubuntu?

---

### Post by #&amp;thj^% on 2022-02-10
This is on Xubuntu 21.10
```
System:    Host: me-Standard-PC-i440FX-PIIX-1996 Kernel: 5.13.0-28-generic x86_64 bits: 64 
         **_  Desktop: KDE Plasma 5.24.0 Distro: Ubuntu 21.10 (Impish Indri) _**
Drives:    Local Storage: total: 23.25 GiB used: 9.28 GiB (39.9%) 
           ID-1: /dev/sda vendor: QEMU model: HARDDISK size: 23.25 GiB 
           Optical-1: /dev/sr0 vendor: QEMU model: QEMU DVD-ROM dev-links: cdrom,dvd 
           Features: speed: 4 multisession: yes audio: yes dvd: yes rw: none 

```
**B-om and guiverc pointed out:** Seems to be a mis-understanding on your end
>  Quote Originally Posted by Bashing-om View Post
jimninja; Hey

Plasma 5.24 available on Kubuntu**[COLOR="#FF0000"] 21.10 or just Impish :) (I added this)[/COLOR]**

See: [https://kubuntu.org/news/plasma-5-24...kubuntu-21-10/](https://kubuntu.org/news/plasma-5-24...kubuntu-21-10/)
hope this helps
EDIT: for impish the PPA needs to be added

---

### Post by SeijiSensei on 2022-02-11
> **jimninja said:**
> on ubuntu or kubuntu?

Well since I was following the instructions at kubuntu.org, you might infer I'm running Kubuntu. Also my profile reads "Kubuntu Development Release."

I wouldn't answer this question if it were about vanilla Ubuntu.

---

