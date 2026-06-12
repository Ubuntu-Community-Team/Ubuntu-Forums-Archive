---
title: "Massive lag on boot"
date: 2009-03-08
forum: General Help
---

### Post by Imoen on 2009-03-08
When I first installed Ubuntu I could restart my pc in a minute or so. Recently I installed kde and upon restart I thought that something happened to my hard drive because it just sat at the intel screen (my motherboard's an intel, so it's that screen that comes on the board). If I try to enter my system bios it says entering setup but won't proceed. After restarting like 5 times, I just let it sit at the screen and after about 5 minutes grub started to load. I thought maybe this was just because it was the first time I ran it so I didn't think too much of it, but when I restarted my computer again the same thing occurs. 

Why would this be so slow with kde? If there's no way to correct it how can I go back to ubuntu?

---

### Post by taurus on 2009-03-08
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by Imoen on 2009-03-09
OK, I uninstalled and there's still a massive delay when starting my pc up. 

Also now I am getting an error when I use the package manager: E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by taurus on 2009-03-09
Close the package manager first.  Then run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Imoen on 2009-03-12
Even after running this code it takes a very long time to boot up and it says kubuntu when loading even though I have ubuntu. Then I get an error message about it not being able to find some file so it will revert to the default one instead. Is there no way to uninstall this and go back to ubuntu that loads in less then a minute?

The code did fix the error I was getting in package manager, thanks.

---

