---
title: "Removing Mate Desktop"
date: 2020-04-03
forum: Desktop Environments
---

### Post by rsteinmetz70112 on 2020-04-03
I'm working from home using Ubuntu something I don't normally do. 
A while ago I installed Mated Desktop to try it out and I have now decided I prefer the regular Gnome.
Can I remove Mate? If so what other things might it affect?

---

### Post by CelticWarrior on 2020-04-03
Installing additional DEs is usually very easy when such desktops are distributed with a meta-package that install all the required packages. OTOH, removing a DE is the opposite.

If you need it for work then, right now, do NOT touch it.

---

### Post by rsteinmetz70112 on 2020-04-03
I was afraid of that. 
I did find some comments that said simply apt remove mate-desktop.
but I was skeptical

---

### Post by CelticWarrior on 2020-04-03
> **rsteinmetz70112 said:**
> I did find some comments that said simply apt remove mate-desktop.


It removes the meta-package only, not the packages it installed. Those have to be manually removed one by one and even then some settings may remain.

---

### Post by ajgreeny on 2020-04-03
Run command ```
grep -i " remove " /var/log/dpkg.log.1 /var/log/dpkg.log | grep mate-desktop
``` which will show you the date and time that you installed the mate DE.

If you now run the command again but removing the final ```
 | grep mate-desktop
``` you may be able to figure out which other packages were installed at the same time, these probably being the packages for the full mate DE and remove them.

It is a slow process and will be very tedious to actually do but it does work; I did it a while ago simply to test the theory after installing KDE to a virtual install of Xubuntu.

---

### Post by Bashing-om on 2020-04-04
rsteinmetz70112 ; Hey -

One might also consider a script:
[https://github.com/aysiu/purebuntu](https://github.com/aysiu/purebuntu)

But, may require "some" adaptation to your particular use case. The author does provide some reasoning background for the existence of his script and the warning,

-my bit to try and help-

---

### Post by rsteinmetz70112 on 2020-04-14
Thanks everyone. I'm going to put this off until after things clear up.

---

### Post by rsteinmetz70112 on 2021-02-11
I finally got back to this. I was able to remove MATE pretty easily. 

```
sudo apt update
sudo apt upgrade
sudo apt remove mate-desktop
sudo apt autoremove
sudo apt install ubuntu-desktop
sudo update
sudo upgrade
```

I'm sure some stuff was left behind but it seems to be working just fine.

I thought about using 

```
sudo apt-get remove '*mate*'
```

But when I ran it with the --simulate option I wasn't sure it wouldn't pickup things I needed.

---

