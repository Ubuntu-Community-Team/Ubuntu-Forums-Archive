---
title: "Kubuntu package not found - help!"
date: 2005-08-18
forum: Desktop Environments
---

### Post by Vinze on 2005-08-18
I've been told to install Kubuntu next to Ubuntu I could just apt-get the kubuntu-desktop, so I did. The result:

[[IMG]http://imgnow.net/imgs/Kubuntu.png[/IMG]](http://imgnow.net?r=54)

Do I have to do it in another way?

---

### Post by Locomorto on 2005-08-18
[QUOTE=Vinze]I've been told to install Kubuntu next to Ubuntu I could just apt-get the kubuntu-desktop, so I did. The result:

[[IMG]http://imgnow.net/imgs/Kubuntu.png[/IMG]](http://imgnow.net?r=54)

Do I have to do it in another way?[/QUOTE]
 Can you please post the contents of your /etc/apt/sources.list file?

---

### Post by Vinze on 2005-08-18
Sure:

> deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe multiverse

 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

#deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/ 
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/ 
deb [http://ubuntu.tower-net.de/ubuntu/](http://ubuntu.tower-net.de/ubuntu/) hoary java
deb [http://www.vollstreckernet.de/debian/](http://www.vollstreckernet.de/debian/) testing amule
deb [http://www.vollstreckernet.de/debian/](http://www.vollstreckernet.de/debian/) testing wx


---

### Post by Takis on 2005-08-18
[QUOTE=Vinze]deb [http://www.vollstreckernet.de/debian/](http://www.vollstreckernet.de/debian/) testing amule
deb [http://www.vollstreckernet.de/debian/](http://www.vollstreckernet.de/debian/) testing wx[/QUOTE]
Spot of advice: it's a really bad idea to have debian-specific repositories in your sources.list - potentially they can break your entire system. Unless the program provider has specifically marked a .deb package as being for Ubuntu, install the program from its source code.

Back on topic:
> ## Uncomment the following two lines to fetch updated software from the network
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restrictedchange to:> ## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

---

### Post by Vinze on 2005-08-18
Thanks for the advise on both points, I'm going to try it now.

***EDIT*** When I had edited it, it said I couldn't save it. I can't remember how I did it last time I edited it! I'm the owner, so I don't know what could be wrong!

---

### Post by SGC on 2005-08-18
[QUOTE=Vinze] When I had edited it, it said I couldn't save it. I can't remember how I did it last time I edited it! I'm the owner, so I don't know what could be wrong![/QUOTE]
 You need to open it with sudo so you can edit it:
sudo gedit /etc/apt/sources.list

Don't forget to do apt-get update after saving the file

---

### Post by Vinze on 2005-08-18
[QUOTE=SGC]You need to open it with sudo so you can edit it:
sudo gedit /etc/apt/sources.list

Don't forget to do apt-get update after saving the file[/QUOTE]

That worked, now going to try kubuntu! Thanks everybody!

---

### Post by Takis on 2005-08-18
[QUOTE=Vinze]I'm the owner, so I don't know what could be wrong![/QUOTE]
As a security measure, just because you own the computer doesn't necessarily you can do anything you want - not straight away. Using the sudo command and entering your password ensures that:
a) You're aware that you're about to make a system change; and
b) that someone who comes across your computer when it's logged in as you can't do too much damage.

---

