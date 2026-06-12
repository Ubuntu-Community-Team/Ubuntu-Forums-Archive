---
title: "help a newbie"
date: 2006-01-25
forum: Desktop Environments
---

### Post by cody on 2006-01-25
hello, I just installed Ubuntu today.. besides winXP because i was tired of the unstability of windows. But i have a problem, im trying to install opera(a browser) and i downloaded the right version. But when i choose to open it in the packet handler or something it cant recognize it or its the wrong file type. So i tried to download the tar.gz format... but what do i do when i've downloaded it?? i unpacked it.. and i think there's some command to write but what is it??:confused: 

and anything basic things i need to know to get started with ubuntu?

---

### Post by Perfect Storm on 2006-01-25
```

sudo gedit /etc/apt/sources.list

```

add:

[b]# Opera web browser
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free
[/b]

```

sudo apt-get update
sudo apt-get install opera
opera

```

---

### Post by soulestream on 2006-01-25
> and anything basic things i need to know to get started with ubuntu?

[http://ubuntuguide.org/](http://ubuntuguide.org/) <- is for 5.04, but most of the stuff still applies
[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)
[http://tldp.org/](http://tldp.org/)
[http://www.google.com/linux]("http://www.google.com/linux")


oh, yeah, "help a newbie" is a bad(dumb) title. Asking questions in a forum usually gets a better response if you put "how to install opera" or something like that it the title. <- for future posts

soule

welcome to linux

---

### Post by tim15856 on 2006-01-25
When I installed Opera using one of the guides, I had a error when it would startup. It worked fine when I installed it using Automatix. Try it. [http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

---

### Post by rockstar on 2006-01-26
I don't know how to install any of the things i've downloaded off the internet

:confused:

---

### Post by Perfect Storm on 2006-01-26
Depends what you have install. The easist way to install something is to use apt-get or Synaptic Package Manager. Firstly you need to setup up your sourcelist which get you access to allmost 18000 programs/applications/libraries.

For ubuntu 5.10 (x86) with internet connection:
```
sudo gedit /etc/apt/sources.list
```

uncomment the lines you find there (The lines which says "#deb http://security.ubuntu.com/ubuntu" just remove the **#**).

and also add these line to the list:

[b]
## Multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

## Wine
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

## Backports
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main universe multiverse restricted
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-backports-staging main universe multiverse restricted

## backports-extras
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras-staging main universe multiverse restricted

## Open Office 2 final
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

## Opera web browser
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free
[/b]

then

```

sudo apt-get update

```

You can now install application with more through the terminal by writing **sudo apt-get install <name of the package>**, or you can go to synaptic package manager (System tab ---> Adminstration).

---

### Post by jrepan on 2006-01-26
[QUOTE=rockstar]I don't know how to install any of the things i've downloaded off the internet

:confused:[/QUOTE]

sudo dpkg -i package_name
These packages must be DEB-s. To install RPM-s you need "alien".

---

### Post by rockstar on 2006-01-26
I appreciate the advise, but I don't know where to put these codes.

---

### Post by kaamos on 2006-01-26
You should insert them to: Applications -> Accessories -> Terminal

---

### Post by aysiu on 2006-01-26
[QUOTE=rockstar]I appreciate the advise, but I don't know where to put these codes.[/QUOTE] Applications > Accessories > Terminal.

By the way, if you add non-Ubuntu repositories for Wine and Opera, be sure to take them out after you've installed Wine and Opera.

---

### Post by era86 on 2006-01-26
To make your life easy, just go and download Automatix. It is very easy to install because the instructions are very "noob" friendly. I think Automatix comes with the Opera browser. Just go to the Custominzation section and it should be a sticky thread.

-ERA

---

### Post by rockstar on 2006-01-26
what if I want to download applications off sourceforge.net, can I tell apt get to look there?  Is there any way I can manually download files.

---

### Post by Perfect Storm on 2006-01-26
If it's a .deb package sourceforge.net you can:

download it
```

cd /where/the/package/is
sudo dpkg -i XXXXXXXXX.deb
```

If it's a source file(s) it's get a bit more complicated, which require additional packages from the repo to be installed before you can compile it, and some more commands which depends how, where and what you'll compile it.

---

### Post by tim15856 on 2006-01-27
[QUOTE=rockstar]what if I want to download applications off sourceforge.net, can I tell apt get to look there?  Is there any way I can manually download files.[/QUOTE]
I gave you the link for Automatix. Install that first and see if it installs most of what you want. Otherwise, In the menu, there is an option to "install applications'. Use that and Synaptic to install practically anything else you'll want. To install other programs, you'll need to follow different procedures depending on if it is a deb, rpm, or source file.

To install via Synaptic or apt-get:
[http://help.ubuntu.com/starterguide/C/ch02.html](http://help.ubuntu.com/starterguide/C/ch02.html)

More on installing programs:
[https://wiki.ubuntu.com/InstallingSoftware](https://wiki.ubuntu.com/InstallingSoftware)

To compile a program from scratch
[https://wiki.ubuntu.com/CompilingSoftware?highlight=%28compile%29](https://wiki.ubuntu.com/CompilingSoftware?highlight=%28compile%29)

---

### Post by aysiu on 2006-01-27
[QUOTE=rockstar]what if I want to download applications off sourceforge.net, can I tell apt get to look there?  Is there any way I can manually download files.[/QUOTE] Read the second link of my signature. It explains everything. Chances are that most of the things you'll want to install will be available through apt-get or Synaptic, especially if you enable extra repositories (see the *first* link of my signature). For the occasional ones that aren't (Opera, for example), just ask.

---

