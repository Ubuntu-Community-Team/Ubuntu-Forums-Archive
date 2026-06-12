---
title: "simple GUI?"
date: 2009-12-01
forum: Desktop Environments
---

### Post by jwarburton3 on 2009-12-01
I just installed 9.10. Is there a basic GUI available?
ubuntu-desktop installs a lot of programs (such as open-org) that I do not need.

Is there a package that will install just the desktop, and then I can go thru the packages and install what I want?

Thanks for any ideas.

Joe

---

### Post by leandromartinez98 on 2009-12-01
If you want to "go though packages" you mean that you want
synaptic installed. Then, you probably can install the synaptic
package, which will install as a dependency the basic gnome
desktop.

---

### Post by maxsideburn on 2009-12-01
WHICH desktop are you wanting? There's XFCE, Gnome, KDE, LXDE, and several others...

As a side note, if anyone knows how to install XFCE WITHOUT installing the entire Xubuntu-Desktop package please let me know, thanks.

---

### Post by maxsideburn on 2009-12-01
For simple GUI I would try install XFCE or WindowMaker

sudo apt-get install xubuntu-desktop

or

sudo apt-get install wmaker

---

### Post by jwarburton3 on 2009-12-01
Thanks for the replies.

I didn't really want to install 500+ packages such as "ubuntu-desktop".

I was looking for something that installed just the necessary packages for the GUI, not alot of extra programs.

Joe

---

### Post by oldos2er on 2009-12-01
There isn't one GUI, there are several. The smallest in terms of hard disk space used is probably LXDE, which you can install by running **sudo apt-get update && sudo apt-get install lubuntu-desktop**.

---

### Post by XubuRoxMySox on 2009-12-02
> **maxsideburn said:**
> 

As a side note, if anyone knows how to install XFCE WITHOUT installing the entire Xubuntu-Desktop package please let me know, thanks.

Yup! Use Synaptic and **install "Xfce" instead of "Xubuntu-desktop."** You just get the Xfce environment without all the extra stuff. You can (and should, IMO) add Xfce-Goodies" as well.

The same applies to LXDE (super-lightweight, but still immature and buggy as hell): If you install "Lubuntu-desktop" you get abuncha extra stuff (and right now it frankly sucks), but install just "LXDE" and you get the way-kewl uber-lightweight newbie-friendly (but immature and buggy) desktop and it's apps.

-Robin

---

### Post by nothingspecial on 2009-12-02
Install Ubuntu minimal or server then

```
sudo apt-get install gnome-core gdm network-manager-gnome  human-theme x11-xserver-utils tangerine-icon-theme gnome-themes-ubuntu ubuntu-artwork jockey-gtk gnome-screensaver gnome-utils
```

Then reboot

---

### Post by sakisds on 2009-12-02
Also you could install xubuntu-desktop without recommends, you will get basic gnome, but without a tone of applications with this:
```
sudo apt-get install --no-install-recommends xubuntu-desktop
```

Also you could use IceWM, its really lightweight, but not really newbie-friendly. To install it use:
```
sudo apt-get install icewm icewm-*
```
(You can also don't include "icewm-*" but i recommend it)

---

### Post by ugm6hr on 2009-12-02
> **sakisds said:**
> Also you could install xubuntu-desktop without recommends, you will get basic gnome, but without a tone of applications with this:
```
sudo apt-get install --no-install-recommends xubuntu-desktop
```


Not true. **x**ubuntu-desktop install xfce.

For a basic xfce:
```
sudo apt-get install xfce4
```

Although, I'd recommend adding the following to make it slightly less basic:
```
sudo apt-get install catfish xfce4-mixer
```
The former is a simple file search GUI, and the latter is an audio volume GUI.

For a basic Gnome, this might help explain what all the various packages add:
[http://distrowatch.com/weekly.php?issue=20081215#feature](http://distrowatch.com/weekly.php?issue=20081215#feature)
However, it is easier to start minimal and add than work in the reverse direction.

Although, it *is* possible to work backwards...
Use both the commands here: [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce) but just remove the *&& sudo apt-get install xubuntu-desktop* at the end of each line.

Hope that helps.

---

