---
title: "LightDM for ubuntu mini"
date: 2013-02-26
forum: Desktop Environments
---

### Post by Elitenoname on 2013-02-26
I have my Ubuntu mini set up with X and everything but i would like to install a login manager and prefer to use LightDM and have it look at feel like the ubuntu login manager, i like it alot but i cant seem to find anything on it after googling around for a bit.

---

### Post by slickymaster on 2013-02-26
Did you already give [LXDE]("http://lxde.org/") a try?

It is extremely fast-performing and energy-saving. It's maintained by an international community of developers and it comes with a beautiful interface, multi-language support, standard keyboard short cuts and additional features like tabbed file browsing.
It uses less CPU and less RAM than other environments and can be installed on many Linux distributions including Debian, Fedora, OpenSUSE and Ubuntu. It is the standard for Knoppix and Lubuntu.

---

### Post by Elitenoname on 2013-02-26
not so much looking for a DE thats light weight more so looking to add a login manager to my ubuntu mini so i dont have to log in via console. mean i can just install lightdm but kinda want it to look like the ubuntu login that all :D

---

### Post by slickymaster on 2013-02-26
> **Elitenoname said:**
> not so much looking for a DE thats light weight more so looking to add a login manager to my ubuntu mini so i dont have to log in via console. mean i can just install lightdm but kinda want it to look like the ubuntu login that all :D

Sorry, completely misunderstood you.

From the [Official Ubuntu Documentation]("https://help.ubuntu.com/community/Installation/LowMemorySystems#Login_managers"):
> _Login managers_
Login managers will assist in choosing a graphical environment and will not require the user to start x.org to get into the window manager. 
It's important to note that it's not necessary to use a login manager. If you're willing to log in at the command line and start X manually, you can save yourself a lot of system resources -- and the time it takes to load them. That can be a more appealing option on older machines.
[B]GDM
[/B]
GDM is the Ubuntu default for a login manager. However, GDM has a reputation of being a heavyweight, and on a system that needs as little bulk as possible, you might find it to be a burden. If you've got a decent system, install it using:
```
sudo apt-get install gdm
```
**KDM**
KDM is another manager, but has the same heavy reputation as GDM.
```
sudo apt-get install kdm
```
**XDM**
XDM is the login manager for straight X, and while less beautiful than GDM or KDM, it can perform in the same role without fuss.
```
sudo apt-get install xdm
```
**SLiM**
SLiM is a simple login manager. It just works as expected.
```
sudo apt-get install slim
```
If the LANG environment variable is not correctly set, see bug #234474.
**LXDM**
LXDM is a light simple login manager designed to fit with LXDE, available in repos from Lucid (10.04) onwards.
```
sudo apt-get install lxdm
```

---

### Post by Elitenoname on 2013-02-26
it is completely fine and thanks for that i saw that but Ubuntu doesn't use the GDM anymore if i am reading it right it uses LightDM but they have their own "theme" if you want to call it that and just wondering how i go about configuring it, mean Slim is very nice and i do like that but was just wanting to try something new :)

---

### Post by Krytarik on 2013-02-26
> **Elitenoname said:**
> ...i would like to install a login manager and prefer to use LightDM and have it look at feel like the ubuntu login manager...
That would be "lightdm", obviously, plus "unity-greeter", but depending on your actual current setup, the latter might pull in too many dependencies. Alternatively, you could just install "lightdm-gtk-greeter", or any other of the "[*greeter]("http://packages.ubuntu.com/search?suite=all&section=all&arch=any&searchon=names&keywords=greeter")" packages, whatever fits best your current setup/taste.

Regards.

---

