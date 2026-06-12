---
title: "Oh dear god!"
date: 2009-03-13
forum: General Help
---

### Post by Clueless Chris on 2009-03-13
Hey guys!

I'm new to Unix/Linux.  I'm installing Ubuntu 8.10 on pc.  I have limited knowledge of Unix.

When I booted the OS for the first time it brought me to CLI.  I was expecting a GUI.  I think a GUI will help me aclimbatize.

Can anyone give some pointers, or point me to another thread that explains step-by-step on how to install a GUI?

Thanks everyone!  I know it's frustrating dealing with newbs like myself; but, it's greatly appreciated :)

Cheers,

Chris.

---

### Post by larrel on 2009-03-13
thats weird, should boot you to the login screen, and gnome display manager should be already set as the default session.. hmm

try: startx
or /etc/init.d/gdm start

---

### Post by Clueless Chris on 2009-03-13
It's Ubuntu Server - would that make a difference.  I also chose during install to be a file server.

Not sure if that is relative or not?

---

### Post by joeyknuccione on 2009-03-13
> **Clueless Chris said:**
> Hey guys!

I'm new to Unix/Linux.  I'm installing Ubuntu 8.10 on pc.  I have limited knowledge of Unix.

When I booted the OS for the first time it brought me to CLI.  I was expecting a GUI.  I think a GUI will help me aclimbatize.

Can anyone give some pointers, or point me to another thread that explains step-by-step on how to install a GUI?

Thanks everyone!  I know it's frustrating dealing with newbs like myself; but, it's greatly appreciated :)

Cheers,

Chris.

I use gnome, from command line do:

```

sudo apt-get install gnome-desktop

```

---

### Post by joeyknuccione on 2009-03-13
> **Clueless Chris said:**
> It's Ubuntu Server - would that make a difference.  I also chose during install to be a file server.

Not sure if that is relative or not?

Don't know about the server, previous reply may not work

---

### Post by Clueless Chris on 2009-03-13
It says "Couldn't find package gnome-desktop"

---

### Post by Clueless Chris on 2009-03-13
Would it be worth installing regular Ubuntu rather than the Server edition?

---

### Post by athaki on 2009-03-13
Ubuntu Server only has a CLI (command line interface)

---

### Post by Jameshardy88 on 2009-03-13
dumb question i know but, you are connected to the internet yes?

---

### Post by albinootje on 2009-03-13
> **Clueless Chris said:**
> It's Ubuntu Server - would that make a difference.

The ubuntu server installation doesn't come with a GUI.
You can run this :
```

sudo dhclient
sudo apt-get update
sudo apt-get install ubuntu-desktop

```
to install the default Ubuntu desktop.

---

### Post by issih on 2009-03-13
Ubuntu server has no gui by default, it is command line.

Assuming you have a working internet connection enter the following:

```
sudo apt-get install ubuntu-desktop
```
N.B. enter your login password and hit enter when prompted

and that will install a nice gnome gui for you..alternatively download the desktop edition and reinstall.

---

### Post by UbuntuNerd on 2009-03-13
> **joeyknuccione said:**
> Don't know about the server, previous reply may not work
you should be able to install the desktop onto the server with the code provided above and should work fine.

---

### Post by Clueless Chris on 2009-03-13
Perfect...Thanks!

I'll download Ubuntu minus the server part.

Sorry to have wasted anyones time.

Chris  :)

---

### Post by albinootje on 2009-03-13
> **joeyknuccione said:**
> 
```

sudo apt-get install gnome-desktop

```
Perhaps you meant gnome-desktop-environment, because gnome-desktop is not an existing package on my Ubuntu Hardy installation.
Recommended is to use the meta-package "ubuntu-desktop" or "xubuntu-desktop" or "kubuntu-desktop" depending on your taste and requirements.

---

### Post by arapa on 2009-03-13
From my understanding the Server and Desktop are pretty much the same - just a different set of applications that come on the install disk. (correct?)

For example, I do some web design so I took an old computer and installed Ubuntu Desktop (not the server version) and then installed some of the server apps like FTP (proFTP), PHP, Web Server (apache), MySql, etc, all available through the Synaptic Package Manager. If you were wanting to use Ubuntu Desktop to serve files on your home network, you could just share the folder by right clicking.

Is there a drawbacks to doing it the other way around? Server then the desktop?

---

### Post by albinootje on 2009-03-13
> **arapa said:**
> From my understanding the Server and Desktop are pretty much the same - just a different set of applications that come on the install disk. (correct?)

After installing the meta-package "ubuntu-desktop" on an already installed Ubuntu server installation, there's basically only one fundamental difference with an Ubuntu Desktop installation, and that is the kernel (linux-image-server versus linux-image-generic).
One extra feature in the server kernel (linux-image-server) is that it supports 4 Gb of RAM or more, which the generic kernel for 32 bit desktop installation doesn't have.

---

### Post by mb_webguy on 2009-03-13
> **arapa said:**
> From my understanding the Server and Desktop are pretty much the same - just a different set of applications that come on the install disk. (correct?)

For example, I do some web design so I took an old computer and installed Ubuntu Desktop (not the server version) and then installed some of the server apps like FTP (proFTP), PHP, Web Server (apache), MySql, etc, all available through the Synaptic Package Manager. If you were wanting to use Ubuntu Desktop to serve files on your home network, you could just share the folder by right clicking.

Is there a drawbacks to doing it the other way around? Server then the desktop?

As others have said, the server edition of Ubuntu has no desktop environment preinstalled, since users don't regularly interact with a server, and a desktop environment would needlessly consume system resources.  I think the kernel for the server version of Ubuntu might also have some optimizations for use on a server.  Otherwise, since they both use the same repositories, there's not much difference between installing server applications on the desktop version of Ubuntu and starting with the server version of Ubuntu.

---

