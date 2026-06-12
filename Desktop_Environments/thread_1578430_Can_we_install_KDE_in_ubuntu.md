---
title: "Can we install KDE in ubuntu"
date: 2010-09-20
forum: Desktop Environments
---

### Post by c2tarun on 2010-09-20
hi friends
i m using UBUNTU 10.04 Lucid.
Can i install KDE in ubuntu. is it possible to switch among the two environments when necessary.
and please tell me how to create backup and restore in case if anything goes wrong.
thanx

---

### Post by perspectoff on 2010-09-20
> **c2tarun said:**
> hi friends
i m using UBUNTU 10.04 Lucid.
Can i install KDE in ubuntu. is it possible to switch among the two environments when necessary.
and please tell me how to create backup and restore in case if anything goes wrong.
thanx

Yes. Heck, you can install the entire kubuntu desktop (sudo apt-get install kubuntu-desktop)

At the login screen, there are options to choose which desktop you want to start. You can pick which one to make the default, as well.

---

### Post by lukeiamyourfather on 2010-09-20
Yes, you can install KDE in any existing Ubuntu install. There's an option to change the environment at the login screen (GNOME, KDE, Xfce, etc.). I don't remember the package name though, maybe kde-desktop? I'm on a Windows machine right now otherwise I'd check the package name for it.

---

### Post by bhavya juneja on 2010-09-20
or you can find it in ubuntu software centre with the name kubuntu desktop plama.

---

### Post by 3Miro on 2010-09-20
For Gnome (installed by default in Ubuntu):
```
 sudo apt-get install ubuntu-desktop 
```

For KDE (installed by default in Kubuntu):
```
 sudo apt-get install kubuntu-desktop 
```

For XFCE (installed by default in Xubuntu):
```
 sudo apt-get install xubuntu-desktop 
```

I am not sure about LXDE.

I recommend you give all of those a try to decide which one works best for you.

---

### Post by perspectoff on 2010-09-20
> **3Miro said:**
> For Gnome (installed by default in Ubuntu):
```
 sudo apt-get install ubuntu-desktop 
```

For KDE (installed by default in Kubuntu):
```
 sudo apt-get install kubuntu-desktop 
```

For XFCE (installed by default in Xubuntu):
```
 sudo apt-get install xubuntu-desktop 
```

I am not sure about LXDE.

I recommend you give all of those a try to decide which one works best for you.

Just be aware that Xubuntu-desktop is now primarily Gnome, so it is pretty similar to Ubuntu-desktop. I personally think it is a waste of time to try that one, these days.

---

### Post by slakkie on 2010-09-20
Just search for tu-desktop with aptitude/apt-get. This will give you all the -desktop packages.

And for KDE, just aptitude install kde :)

---

### Post by nothingspecial on 2010-09-20
Just so you know, you do not have to install the whole of kubuntu to try out kde.

The kde-minimal package would be enough to try it, kununtu-desktop is huge and comes with a huge amount of packages and their dependencies.

---

### Post by LinuxPhreak on 2010-09-20
KUbuntu is the KDE Desktop Envirnment with whole lot of extra packages added to it. You can install typing the following. 

```

sudo apt-get install kubuntu-desktop
```

Or you can install the bare KDE package which includes everything KDE needs in order for it to run. To do this you would type the following. 

```
sudo apt-get install kde-minimal
```

Depending on what login manager you choose to use you may want to type 

```
sudo apt-get install kdm
```

The above will replace the GDM with KDM. 

If your using an older version of Ubuntu then the KDE Desktop package would be different. To install kde-minimal on older machines you may want to type the following. 

```
sudo apt-get install kde-core
```

---

### Post by c2tarun on 2010-09-21
can i remove it whenever i want
how can i do that??

---

### Post by nothingspecial on 2010-09-21
Do the commands in the above post, but type remove instead of install.

To remove the full kubuntu-desktop package see here

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by c2tarun on 2010-09-21
thanx

---

