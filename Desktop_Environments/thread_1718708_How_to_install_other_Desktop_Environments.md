---
title: "How to install other Desktop Environments?"
date: 2011-03-31
forum: Desktop Environments
---

### Post by galacticaboy on 2011-03-31
I would like to try out LXDE and E17 on my Xubuntu 10.04. What would I type in the terminal to install them? I want to try them out without installing Distros that have them? And if I want to remove them what do I type in the terminal? Thanks!
David

---

### Post by ankspo71 on 2011-03-31
Hi,
You don't necessarily need to use commands to install other desktop environments, because they can be found in your package manager (Synaptic Package Manager, Software Center, etc), but you can install them with commands if you want to. 

To install using apt-get commands:
```
sudo apt-get install lxde
sudo apt-get install e17
```

To uninstall :
```
sudo apt-get remove lxde
sudo apt-get remove e17
```

Note: Some larger desktop environment packages (or rather the distribution packages like kubuntu-desktop and ubuntu-desktop, etc) can't get removed as easily because they use meta-packages for installation, so you will need to refer to this link for special removal commands: [http://www.psychocats.net/ubuntu/purexfcelucid](http://www.psychocats.net/ubuntu/purexfcelucid) <- I edited the link for Xubuntu 10.04.

To log into your newly installed desktop, you will need to log out of your current desktop, then select your name in the log in window, then go to the bottom of the screen to choose the desktop you want to log into, then go back up to enter your password and login.

Hope this helps.

---

### Post by 3Miro on 2011-03-31
+1 for psycho cat

---

### Post by oldrocker99 on 2011-04-02
> **ankspo71 said:**
> 

To install using apt-get commands:
```
sudo apt-get install lxde
sudo apt-get install e17
```

To uninstall :
```
sudo apt-get remove lxde
sudo apt-get remove e17
```

---------

Hope this helps.

I had no idea that you simply used the name of the environment. THANK YOU!!!\\:D/

---

