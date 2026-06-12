---
title: "HOWTO: Upgrade to KDE 3.5.1"
date: 2006-02-02
forum: Desktop Environments
---

### Post by Howcomes on 2006-02-02
Add the following lines to your **/etc/apt/sources.list** file:
[b]
deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main
deb-src  [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main[/b]

now issue the following commands in a Konsole:

[b]
wget [http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg](http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg)
sudo apt-key add kubuntu-packages-jriddell-key.gpg
sudo apt-get update
sudo apt-get dist-upgrade[/b]

You may or may not get an error about key authentication (i did) i just accepted anyway.

Once this process finishes you can reboot or logoff and back on and you should be in KDE 3.5.1 (my log off/on hanged on Checking Battery Status so i just Alt + Ctrl + F2 and logged in and im in KDE 3.5.1 now :D)

Enjoy - Howcomes

---

### Post by magnusbb on 2006-02-02
Has anyone had problems with the kdeedu package? I have an x86 system, and there seems to be only amd64 packages for this part of KDE in the repository.

---

### Post by CyberAngel on 2006-02-02
[QUOTE=Howcomes]....
You may or may not get an error about key authentication (i did) i just accepted anyway.
[/QUOTE]

If you don`t want to get the error about key authentication before apt-get use the two following commands:
```
wget http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg
sudo apt-key add kubuntu-packages-jriddell-key.gpg
```

;)

---

