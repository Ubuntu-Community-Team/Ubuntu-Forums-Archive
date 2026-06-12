---
title: "Using xfce, but want to install Gnome"
date: 2009-11-16
forum: Desktop Environments
---

### Post by chris_andrew on 2009-11-16
Hi,

I'm currently running with an Xubuntu set-up (xfce), but I'd like to be able to use Gnome.

In the old days using Debian, I would have done

```
apt-get install gnome
```

Can anyone confirm whether this is the best way to add  the default Ubuntu Gnome desktop?

Cheers,

Chris.

---

### Post by m_duck on 2009-11-16
Hey,

The way to get the default Ubuntu desktop would be to install the [ubuntu-desktop](http://packages.ubuntu.com/karmic/ubuntu-desktop) package.```
sudo apt-get install ubuntu-desktop
```That will install Gnome as it is on Ubuntu with all the applications that come with Gnome and that Ubuntu include. A slimmer choice would be installing [gnome-core](http://packages.ubuntu.com/karmic/gnome-core) which installs the basic Gnome desktop, leaving you free to add the rest of the apps that you want.

---

### Post by wilee-nilee on 2009-11-16
If you want the Ubuntu desk top go to synaptic and tick it to install. Here is a link so you can add or remove Xubuntu and Ubuntu. Since you don't list which distro your running now just look at the list on the left to find the playing around and have a good time.
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

You can also just install in the terminal 
sudo aptitude install ubuntu-desktop
I would use aptitude as it makes it easier to remove the whole package set if needed, On the psychocats site you will see, gives you a complete package list for installation and removal for Xubuntu and Ubuntu. You can have both desktops installed you just have to chooses which one is the default or change to in the login Gui. Just also make sure you are adding or removing the list for whatever OS your using.

The only thing you want to be careful about is that if you have thunderbird install it will get removed if you remove a complete desktop, this probably applies to some other 3rd party programs so be careful to have any email saved.

---

### Post by chris_andrew on 2009-11-16
> **wilee-nilee said:**
> If you want the Ubuntu desk top go to synaptic and tick it to install. Here is a link so you can add or remove Xubuntu and Ubuntu. Since you don't list which distro your running now just look at the list on the left to find the playing around and have a good time.
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

You can also just install in the terminal 
sudo aptitude install ubuntu-desktop
I would use aptitude as it makes it easier to remove the whole package set if needed, On the psychocats site you will see, gives you a complete package list for installation and removal for Xubuntu and Ubuntu. You can have both desktops installed you just have to chooses which one is the default or change to in the login Gui. Just also make sure you are adding or removing the list for whatever OS your using.

The only thing you want to be careful about is that if you have thunderbird install it will get removed if you remove a complete desktop, this probably applies to some other 3rd party programs so be careful to have any email saved.

Running Xubuntu Karmic.  I'm going to go for Gnome-Core and see how it's looking these days.

Cheers,

Chris.

---

### Post by wilee-nilee on 2009-11-17
I like Xubuntu I usually have it and the Ubuntu desktops installed just for the variety. Both are easy to manipulate or customize and are already user friendly.

---

### Post by Dullstar on 2009-11-17
> **chris_andrew said:**
> Hi,

I'm currently running with an Xubuntu set-up (xfce), but I'd like to be able to use Gnome.

In the old days using Debian, I would have done

```
apt-get install gnome
```Can anyone confirm whether this is the best way to add  the default Ubuntu Gnome desktop?

Cheers,

Chris.

If you mean sudo apt-get install gnome, you're right that that's a way to do it.  Basically think of it this way.

```
sudo apt-get install [insert desktop environment name here (lowercase)]
```

But that's if you want Gnome.  If you want the Gnome used by Ubuntu, then it's ubuntu-desktop instead of gnome in the terminal.

---

