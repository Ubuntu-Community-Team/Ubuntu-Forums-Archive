---
title: "Best way to install another DE?"
date: 2014-11-06
forum: Desktop Environments
---

### Post by Benjamin5th on 2014-11-06
I want to have multiple DE's onto Xubuntu just to try them out. I've heard that depending on the way you install them, you also get all the applications associated with that DE as well. Can I install just the DE, and not the applications that come with it?

---

### Post by Bucky Ball on 2014-11-06
Just the desktop environment. 

Lubuntu = install lxde, NOT lubuntu-desktop (that's when you'll drag in the WHOLE of Lubuntu);
Unity = Ubuntu;
etc. There are a heap. Just make sure you're installing the DE only and NOT *buntu-desktop anything. 

I quite liked RazorQT and Enlightenment myself.

When you install a DE, log out, choose it from the Sessions menu, log in. That's it. ;)

---

### Post by Benjamin5th on 2014-11-06
So how would I say that in the terminal? Sudo install ubuntu?

---

### Post by Bucky Ball on 2014-11-06
Nope. You don't want Ubuntu. You want its DE. So:

```
sudo apt-get install unity
```

That should do it. You can also install from the Software Centre, or with Xubuntu, Synaptics. Have a look around in there. 

Before you do install unity, or anything else, sticking to the terminal, run:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

This will bring everything up to date, then install Unity. The last command WON'T upgrade your release to another one. Just the packages you have installed in this release, if they need it. ;)

---

### Post by Benjamin5th on 2014-11-06
Will this make sure I only get the DE and not the applications associated with it?

---

### Post by vasa1 on 2014-11-07
Type ```
apt-get install -s unity
``` in your terminal to see what will be installed. Nothing will actually be installed: the -s indicates you're just doing a simulation.

You can use apt-get install -s for checking what will be installed for anything that's available via apt-get :)

Another tweak is to use ```
apt-get install --no-install-recommends -s unity
```

Yet another option is to use apt-cache. Run ```
apt-cache show unity
```

---

### Post by sammiev on 2014-11-07
> **vasa1 said:**
> Type ```
apt-get install -s unity
``` in your terminal to see what will be installed. Nothing will actually be installed: the -s indicates you're just doing a simulation.

You can use apt-get install -s for checking what will be installed for anything that's available via apt-get :)

Another way of getting information is to use apt-cache. Run ```
apt-cache show unity
```

+1 and if you have Synaptic Package Manager installed, it will also show you what is going to be installed before you install the packages.

---

### Post by vasa1 on 2014-11-07
> **sammiev said:**
>  ... if you have Synaptic Package Manager installed, it will also show you what is going to be installed before you install the packages.
Do you know whether Synaptic install "recommends" by default? If so, new users may not know that.

---

### Post by deadflowr on 2014-11-07
> **vasa1 said:**
> Do you know whether Synaptic install "recommends" by default? If so, new users may not know that.

For me, there is a line in preferences that says, consider recommendations as dependencies.
It is toggled on, but a simple uncheck, apply and reloading the packages stops that.
You can then mark which recommends you want to install from the right click menu option.

---

### Post by sammiev on 2014-11-07
> **deadflowr said:**
> For me, there is a line in preferences that says, consider recommendations as dependencies.
It is toggled on, but a simple uncheck, apply and reloading the packages stops that.
You can then mark which recommends you want to install from the right click menu option.

+1 and thanks.

---

### Post by Benjamin5th on 2014-11-08
> **Bucky Ball said:**
> Nope. You don't want Ubuntu. You want its DE. So:

```
sudo apt-get install unity
```

That should do it. You can also install from the Software Centre, or with Xubuntu, Synaptics. Have a look around in there. 

Before you do install unity, or anything else, sticking to the terminal, run:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

This will bring everything up to date, then install Unity. The last command WON'T upgrade your release to another one. Just the packages you have installed in this release, if they need it. ;)

I tried what you said, but unity still isn't an option when I start up my computer.

---

### Post by vasa1 on 2014-11-08
What do you have in /usr/share/xsessions ?

---

### Post by vasa1 on 2014-11-08
And what was the actual command you used to install "unity" or did you do it via the GUI?

If you have a few USB sticks and no download restrictions, it maybe cleaner to test various complete distros and then install the one you like.

---

### Post by deadflowr on 2014-11-08
When you installed unity you did indeed install unity.
However installing unity does not install the xsession packages to launch it via lightdm(the login screen).
You could at this point launch it from, let's say, a running session.
But who wants that.

Instead you need to session package
(It is at this point unclear which version of Ubuntu is being used so the package differs between Ubuntu 12.04 and Ubuntu 14.04.
In Ubuntu 12.04 it should *gnome-session*.
```
sudo apt-get install gnome-session
```
If memory serves correctly.
And in Ubuntu 14.04 it is *ubuntu-session.*
```
sudo apt-get install ubuntu-session
```
This/these will add unity/ubuntu to the login options.

---

### Post by vasa1 on 2014-11-08
> **deadflowr said:**
> When you installed unity you did indeed install unity.
However installing unity does not install the xsession packages to launch it via lightdm(the login screen).
You could at this point launch it from, let's say, a running session.
But who wants that.

Instead you need to session package
(It is at this point unclear which version of Ubuntu is being used so the package differs between Ubuntu 12.04 and Ubuntu 14.04.
In Ubuntu 12.04 it should *gnome-session*.
```
sudo apt-get install gnome-session
```
If memory serves correctly.
And in Ubuntu 14.04 it is *ubuntu-session.*
```
sudo apt-get install ubuntu-session
```
This/these will add unity/ubuntu to the login options.

It's ubuntu-session even in 14.10. See **apt-cache show ubuntu-session**.

---

### Post by Bucky Ball on 2014-11-08
Nicely. Thanks. ;)

---

### Post by Benjamin5th on 2014-11-09
Thanks guys :) that did it!

---

### Post by vasa1 on 2014-11-09
> **Benjamin5th said:**
> Thanks guys :) that did it!
But see [http://ubuntuforums.org/showthread.php?t=2252102](http://ubuntuforums.org/showthread.php?t=2252102)

---

