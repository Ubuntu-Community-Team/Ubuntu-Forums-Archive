---
title: "Black screen!!"
date: 2006-01-02
forum: Desktop Environments
---

### Post by norm7446 on 2006-01-02
I have just intalled Kubuntu5.10 on my samsung laptop.
It seems to have installed Ok, but once it has loaded up to the login screen all I get is a blank black screen, if I type both my user name and password in the h/drive light starts flickering and after a minute or so I can here the Kde logging in sound so it does seem that Kde is loading up the desktop ok but I still dont see anything just a blank black screen. I have reinstalled Kubuntu5.10 again but still get the same blank black screen. Please help. I also have Kubuntu5.10 installed on my desktop with no problems and have done nothing differnt when installing on the laptop.

---

### Post by daller on 2006-01-02
[QUOTE=norm7446]I have just intalled Kubuntu5.10 on my samsung laptop.
It seems to have installed Ok, but once it has loaded up to the login screen all I get is a blank black screen, if I type both my user name and password in the h/drive light starts flickering and after a minute or so I can here the Kde logging in sound so it does seem that Kde is loading up the desktop ok but I still dont see anything just a blank black screen. I have reinstalled Kubuntu5.10 again but still get the same blank black screen. Please help. I also have Kubuntu5.10 installed on my desktop with no problems and have done nothing differnt when installing on the laptop.[/QUOTE]


Try to use this argument in the installation:

linux vga=771

...or if you don't want to install again, you can run:

```
dpkg-reconfigure xserver-xorg
```

...If you start in recovery mode! (press "esc" when GRUB loads, and choose revovery mode!)

Post again if you have any problems!

---

### Post by norm7446 on 2006-01-02
Probelm solved, well sort of, in a round about way, as im doing this post on my laptop while downloading ubuntu live on my main Pc with Kubuntu5.10, on the laptop I'm now using mandriva2006 which as set up my laptop screen ok with correct resolution and screen refresh.
thank you for your prompt reply. 
                                                            Norm7446.....

---

