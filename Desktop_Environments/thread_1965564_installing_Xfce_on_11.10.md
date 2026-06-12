---
title: "installing Xfce on 11.10"
date: 2012-04-26
forum: Desktop Environments
---

### Post by nashtrik on 2012-04-26
I want to install Xfce desktop environment on my ubuntu 11.10. Is it possible to install it alongside Unity..? Will I get the option to boot/login with either of the two during bootup...? If i want to uninstall Xfce sometime later,would it be a clean uninstal without messing up the whole setup ? Above all,is it worth giving Xfce a shot?

---

### Post by Lemuriano on 2012-04-26
It just take a few clicks in the software center under Xfce4 and also from the CLI if you choose to.

```
sudo apt-get install xfce4
```Or if you prefer to install the Xubuntu desktop 

```
sudo apt-get install xubuntu-desktop
```The option would appear when you login and if you decide to unistall go to the software center or:

```
sudo apt-get purge xfce4 
```

Related to your last question, your hardware could influence your decision and the other factor is how well you can perform on both environments (preference).  

Regards.

---

### Post by 3Miro on 2012-04-26
Here is a good tutorial on how to switch between different DE:

[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

I prefer to just install xfce4. Xubuntu desktop comes with a lot of other stuff that I don't necessarily need and it changes some settings (like the boot splash screen).

---

