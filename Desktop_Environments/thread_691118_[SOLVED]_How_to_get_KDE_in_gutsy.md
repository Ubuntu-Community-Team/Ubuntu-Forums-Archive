---
title: "[SOLVED] How to get KDE in gutsy ?"
date: 2008-02-08
forum: Desktop Environments
---

### Post by sourabhsharma149 on 2008-02-08
Hello,

Like in RedHat or Fedora or any other Linux won't I asked to select my session to a perticular environment ?

I am having default gutsy on gnome buit I also want to use KDE ...

So installing Kubuntu is must ?? or can I have KDE or Gnome both on Ubuntu ? Please help how I can get KDE also ?

Thanks.

---

### Post by jrib on 2008-02-08
Install the "kubuntu-desktop" package using your favorite package manager.  Then at the login screen you can select to log into GNOME or KDE by clicking on "options".

---

### Post by /home on 2008-02-08
> **_jason said:**
> Install the "kubuntu-desktop" package using your favorite package manager.  Then at the login screen you can select to log into GNOME or KDE by clicking on "options".
Or type in command line
> sudo apt-get install kubuntu-desktop

---

### Post by PmDematagoda on 2008-02-08
> **/home said:**
> Or type in command line
sudo apt-get install kubuntu-desktop 

Usually it is recommended that you use aptitude instead of apt-get since using aptitude ensures that if you want to completely remove KDE(i.e. with all the packages that were additionally installed) you can do so  simply by using:-
```
sudo aptitude remove kubuntu-desktop
```

---

### Post by sourabhsharma149 on 2008-02-09
Thank you all for your help

---

