---
title: "Synaptic Smart Upgrade"
date: 2005-11-22
forum: Desktop Environments
---

### Post by chettyk on 2005-11-22
I need to know how safe it is to use the Synaptic Smart Upgrade option.

Today when I updated and upgraded my system, I got the following message:

> **It is not possible to upgrade all packages**
This means that beside the actual upgrade of the packages some further action (such as installing or removing packages) is required. Please use Synaptic 'Smart Upgrade' or 'apt-get dist-upgrade' to the fix the situation.


The two packages not upgraded were: linux-image-386 and linux-restricted-modules-386.

I don't want to upgrade from Hoary Hedgehog at present. Hence my question about whether it was safe to use Synaptic Smart Upgrade in these circumstances. Or is there something else that I ought to be doing?

---

### Post by Xian on 2005-11-22
There shouldn't be anything to worry over, since a "smart" upgrade simply gives the package manager the permission to install additional pkgs that are needed by the system update. It will not go outside your chosen (Hoary) repos if that is all that is in your sources list.

Post the output of the command if you want us to look at it for you.
It will ask for a confirmation. Just copy/paste up to that point.

```
$ sudo apt-get dist-uprade
```

---

### Post by chettyk on 2005-11-23
[QUOTE=Xian]There shouldn't be anything to worry over, since a "smart" upgrade simply gives the package manager the permission to install additional pkgs that are needed by the system update. It will not go outside your chosen (Hoary) repos if that is all that is in your sources list.

Post the output of the command if you want us to look at it for you.
It will ask for a confirmation. Just copy/paste up to that point.

```
$ sudo apt-get dist-uprade
```[/QUOTE]

I should have thought of this -- that the package manager would not go outside the Hoary repos. Thanks a bunch, Xian. I will take your suggestion and run the 'sudo apt-get dis-upgrade' command. 

Thanks again. Cheers.

---

### Post by chettyk on 2005-11-26
```
$ sudo apt-get dist-uprade
```

Worked smoothly. Thanks so much, Xian.

---

