---
title: "Server X doesn't start in upgrading to hoary"
date: 2005-03-18
forum: Desktop Environments
---

### Post by lizardking on 2005-03-18
I was with warty 4.10 e I upgraded to hoary in this way:
change repository from warty to hoary
then **sudo apt-get update** 
and finally **sudo apt-get dist-upgrade** 

All goes weel but when I rebooted the machine the Server X doesn't start beacuse it says that the configuration file ws not property configured....

some help?

---

### Post by Yukonjack on 2005-03-18
You have to reconfigure xserver after such a big upgrade

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by lizardking on 2005-03-18
do U mean  **sudo dpkg --configure xserver-xorg ** ??

---

### Post by Yukonjack on 2005-03-18
[QUOTE=lizardking]do U mean  **sudo dpkg --configure xserver-xorg ** ??[/QUOTE]

No, I mean what I wrote. 
Reboot your box in the recovery mode once you login execute the command.

---

