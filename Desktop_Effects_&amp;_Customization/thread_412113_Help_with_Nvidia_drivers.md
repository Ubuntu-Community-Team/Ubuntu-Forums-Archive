---
title: "Help with Nvidia drivers"
date: 2007-04-17
forum: Desktop Effects &amp; Customization
---

### Post by danylong on 2007-04-17
i am somewhat new to ubuntu and i have a nvidia riva tnt2 pro graphics card.
my problem is that i dont know which drivers to install, i have tried a legacy driver and it didnt work.
any suggestions on how to get a driver working with ubuntu 7.04 

thanks a lot in advance

---

### Post by loserboy on 2007-04-17
search the forums for a program called envy, I've only used it with edgy but im pretty sure theres a feisty version

---

### Post by loserboy on 2007-04-17
i just looked here [http://albertomilone.com/wordpress/](http://albertomilone.com/wordpress/) and it doesnt look like he has anything for feisty yet, but I see TNT2 drivers right off the nvidia page, did u try that?

---

### Post by danylong on 2007-04-17
i have tried to install off of the nvidia website but during the installation it tells me to shut down either xserver or xorg i cant remember which at the moment but when i did a kill all command it just kicked me off and made me restart.  this even happened when i booted into terminal mode also so i gave up on that idea.
any other suggestions?

---

### Post by eggdeng on 2007-04-17
I had a Riva TNT2 working with the legacy driver. The bad news is that it doesn't support 3D acceleration so no Beryl. :(

---

### Post by danylong on 2007-04-17
wait my card doesnt support 3d acceleration?
i read somewhere else on the internet that someone had beryl working with a riva tnt2
must have been fake...
well thanks to everyone for all their help

---

### Post by txhellkat138 on 2007-04-18
> **danylong said:**
> i have tried to install off of the nvidia website but during the installation it tells me to shut down either xserver or xorg i cant remem[ber which at the moment but when i did a kill all command it just kicked me off and made me restart.  this even happened when i booted into terminal mode also so i gave up on that idea.
any other suggestions?
before you start make sure you have your restricted modules and such installed.

```
sudo apt-get install linux-headers-$(uname -r) build-essential
```

You have to end your X session and stop gdm/kdm. Hit ctrl+alt+f2 and that will take you to a command prompt to log in. From there


```
sudo /etc/init.d/gdm stop
```

From this point you can 

```
sudo ./NVIDIA.whatever.the.file.is.called
```

it will run the installer. AT the end of the installer it will ask if you wanna run nvidia-xconfig say no.
then 
```
sudo nvidia-xconfig --add-argb-glx-visuals
```

Ie doen this quite a few times now for friends here is a helpful howto I got all this info from. It will even help you get beryl running and such if thats your bag.

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia)

---

