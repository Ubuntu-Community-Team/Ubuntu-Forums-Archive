---
title: "KDE without Kubuntu"
date: 2006-10-03
forum: Desktop Environments
---

### Post by krypto_wizard on 2006-10-03
I want to install KDE (minimal packages) without having to install kubuntu.

What I mean is when last time I installed Kubuntu desktop while booting the screee showed "Kubuntu" in blue color instead of Ubuntu  in yellow.

I want everything to have in ubuntu but an ability to switch to KDE someties.

How can we do this.

Thanks

---

### Post by someguyouknow on 2006-10-03
sudo aptitude install kde

you dont need kubuntu to have kde

---

### Post by aysiu on 2006-10-03
The *kde* package is a bit more.

I would start with *kde-core*.

```
sudo aptitude update
sudo aptitude install kde-core
```

---

### Post by krypto_wizard on 2006-10-03
I installed KDE and looged inside KDE.

It asked me which style to choose and by mistake I chose Apple MAC style.

How can I change it back to KDE .

Thanks

---

### Post by aysiu on 2006-10-03
> **krypto_wizard said:**
> I installed KDE and looged inside KDE.

It asked me which style to choose and by mistake I chose Apple MAC style.

How can I change it back to KDE .

Thanks
Alt-F2 ```
kpersonalizer
``` to run the wizard again or ```
kcontrol
``` to change the settings in general.

---

### Post by krypto_wizard on 2006-10-03
Thanks, I appreciate your help.

---

### Post by TristanMike on 2006-10-03
> **krypto_wizard said:**
> I want to install KDE (minimal packages) without having to install kubuntu.

What I mean is when last time I installed Kubuntu desktop while booting the screee showed "Kubuntu" in blue color instead of Ubuntu  in yellow.

I want everything to have in ubuntu but an ability to switch to KDE someties.

How can we do this.

ThanksHi, if all your looking for is to switch the usplash screen back to the Ubuntu from the Kubuntu one (which is what I did as well) after the kubuntu-desktop install, all you need to do is, in a terminal, ```
sudo update-alternatives --config usplash-artwork.so
```and select the usplash-default and you'll back to the nice yellow Ubuntu logo.

As well, make sure you select GDM instead of KDM to make sure Ubuntu gets default.

Hope this helps.

TM

---

### Post by krypto_wizard on 2006-10-04
Thanks it does help...

---

