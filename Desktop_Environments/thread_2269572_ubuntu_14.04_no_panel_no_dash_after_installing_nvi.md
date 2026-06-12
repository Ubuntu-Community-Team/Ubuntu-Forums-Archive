---
title: "ubuntu 14.04 no panel no dash after installing nvidia driver"
date: 2015-03-16
forum: Desktop Environments
---

### Post by daniii10 on 2015-03-16
After installing nvidia driver i don't have desktop only blank screen. 
[IMG]http://s24.postimg.org/axkwvk3th/20150316_160937.jpg[/IMG]

I tried several solutions [here]("http://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears") non of them worked.
when i try to go to tty terminal and type ccsm this is what i get. [http://s27.postimg.org/okm7g1qg3/20150316_162314.jpg](http://s27.postimg.org/okm7g1qg3/20150316_162314.jpg)
sorry for the pictures quality i don't know how to take screenshot on tty mod.

I'm running ubuntu 14.04 LTS with nvidia GeForce 630m 

If anyone can help me I'll be grateful.

---

### Post by grahammechanical on 2015-03-16
Please try the suggestions I offered in this thread that I just this minute replied to.

[http://ubuntuforums.org/showthread.php?t=2269582](http://ubuntuforums.org/showthread.php?t=2269582)

I am sorry, but right now I am unwilling to re-type what I have just written. How did you install this Nvidia driver? Through Additional Drivers?

Regards.

---

### Post by daniii10 on 2015-03-16
I tried to log on Gnome flashback but when i press the right click nothing appear.
I installed nvidia driver by following this guide [http://ubuntuhandbook.org/index.php/2015/01/install-nvidia-346-35-ubuntu-1404/](http://ubuntuhandbook.org/index.php/2015/01/install-nvidia-346-35-ubuntu-1404/)

---

### Post by daniii10 on 2015-03-16
Ok i found a way to restore my desktop this is what i did from this link [http://askubuntu.com/questions/450046/black-screen-with-nvidia-drivers-on-ubuntu](http://askubuntu.com/questions/450046/black-screen-with-nvidia-drivers-on-ubuntu)
This is what i did:

```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install build-essential
sudo apt-get install linux-source
sudo apt-get install linux-headers-generic
sudo apt-get dist-upgrade
sudo reboot

```
And after reboot

```
sudo apt-get install nvidia-current-updates
sudo nvidia-xconfig
sudo reboot
```

But now i don't have the full nvidia driver:
[IMG]http://s21.postimg.org/w0wpwboc7/Screenshot_from_2015_03_16_22_11_39.jpg[/IMG]

no prime and no resolution settings

there is any way i can install nvidia driver with all those settings?

---

### Post by jimmyh1972 on 2015-03-18
sudo apt-get install nvidia-current

---

### Post by jimmyh1972 on 2015-03-18
also

sudo ubuntu-drivers autoinstall

---

### Post by daniii10 on 2015-03-18
> **jimmyh1972 said:**
> also

sudo ubuntu-drivers autoinstall

thanks it works but now nvidia-settings can't detect the other screen when i press 'detect' it just crash

[IMG]http://s16.postimg.org/ryesk5tlh/Screenshot_from_2015_03_18_22_11_24.jpg[/IMG]

---

