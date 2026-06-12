---
title: "how to download but not install ?"
date: 2010-10-01
forum: Gaming &amp; Leisure
---

### Post by m_zeid on 2010-10-01
Hi every one,
Every thing I found in Ubuntu is pretty good, except for one thing OFFLINE INSTALLING .
So I have an Ubuntu box and planning to install it for other PC's of my family and friends, but downloading the same programs and games for every single computer is absolutely not an option especially because in our country the Internet connection SUXXX

for now it's okay with programs, but games are much much bigger 1gb and above!!
so is there anyway to download the game with it's dependencies and then use a flash drive to install it on other computers ??

I've found somewhere on the Internet this "sudo aptitude &#150;download-only install   ??" but not sure about it and wont try it before asking other people experience with it 

So any ideas ??

---

### Post by Perfect Storm on 2010-10-01
You can download the packages here manually - just make sure tto get any dependencies as well; [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by sikander3786 on 2010-10-01
Downloading and installing from [http://packages.ubuntu.com](http://packages.ubuntu.com) is pretty useless, impossible I believe. You can never get past the dependency problems. How will one know which packages are installed on his PC. He needs dependencies of dependencies.....

You might be interested in Keryx.

[http://keryxproject.org/](http://keryxproject.org/)

---

### Post by m_zeid on 2010-10-02
> **Artificial Intelligence said:**
> You can download the packages here manually - just make sure tto get any dependencies as well; [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

thanks for the link I will take a look.

> **sikander3786 said:**
> Downloading and installing from [http://packages.ubuntu.com](http://packages.ubuntu.com) is pretty useless, impossible I believe. You can never get past the dependency problems. How will one know which packages are installed on his PC. He needs dependencies of dependencies.....

You might be interested in Keryx.

[http://keryxproject.org/](http://keryxproject.org/)

OK so what I've thought of was as I install software from terminal and how simple is for installing the dependencies, I do the same thing but but what the terminal will download make it download them not to temp but to another folder and those files (program+dependencies) can copy and install them on other pc, by installer, terminal, compiling... whatever. so can this be done??

I will take a look on Keryx, thank you for the advice

---

### Post by dfreer on 2010-10-02
I got this from a project at my school:

Getting Packages Offline

For Debian based distributions the following command can be used to generate a script that will download all needed packages for a given piece of software
```
apt-get -qq --print-uris install <package name> | awk '{print "wget -O " $2 " " $1}' >> wget.apt.sh
```
Take the wget.sh and use Cygwin's wget under windows to download the packages. Then move the packages back to the machine needing the packages and run
```
dpkg -i *.deb
```

For RedHat based distributions the following command can be used to generate a script that will download all neede packages fora given piece of software
```
yumdownloader -q --urls --resolve <package name> | awk '{print "wget " $1}' >> wget.yum.sh
```
Take the wget.sh and use Cygwin's wget under windows to download the packages. Then move the packages back to the machine needing the packages and run
```
rpm -ivh *.rpm
```

---

### Post by sikander3786 on 2010-10-03
> OK so what I've thought of was as I install software from terminal and how simple is for installing the dependencies, I do the same thing but but what the terminal will download make it download them not to temp but to another folder and those files (program+dependencies) can copy and install them on other pc, by installer, terminal, compiling... whatever. so can this be done??

Everytime the terminal downloads some packages, they are not stored in temp folder. Instead they are saved in apt-get cache directory for future installs/reinstalls. You can also specify a -d switch e.g,

```

sudo apt-get install -d vlc

```

It will download the packages only and will not install them. Later on you can use APTonCD to transfer them to another system.

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by R33D3M33R on 2010-10-03
I used [AptOnCD]("http://aptoncd.sourceforge.net/") (in the repositories) for this or you can also use [Remastersys]("http://www.geekconnection.org/remastersys/") to transfer the whole install.

---

### Post by m_zeid on 2010-10-15
> **dfreer said:**
> I got this from a project at my school:

Getting Packages Offline

For Debian based distributions the following command can be used to generate a script that will download all needed packages for a given piece of software
```
apt-get -qq --print-uris install <package name> | awk '{print "wget -O " $2 " " $1}' >> wget.apt.sh
```Take the wget.sh and use Cygwin's wget under windows to download the packages. Then move the packages back to the machine needing the packages and run
```
dpkg -i *.deb
```For RedHat based distributions the following command can be used to generate a script that will download all neede packages fora given piece of software
```
yumdownloader -q --urls --resolve <package name> | awk '{print "wget " $1}' >> wget.yum.sh
```Take the wget.sh and use Cygwin's wget under windows to download the packages. Then move the packages back to the machine needing the packages and run
```
rpm -ivh *.rpm
```

> **sikander3786 said:**
> Everytime the terminal downloads some packages, they are not stored in temp folder. Instead they are saved in apt-get cache directory for future installs/reinstalls. You can also specify a -d switch e.g,

```

sudo apt-get install -d vlc

```It will download the packages only and will not install them. Later on you can use APTonCD to transfer them to another system.

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

> **R33D3M33R said:**
> I used [AptOnCD]("http://aptoncd.sourceforge.net/") (in the repositories) for this or you can also use [Remastersys]("http://www.geekconnection.org/remastersys/") to transfer the whole install.


hi every one and thank you for you suggestions, and sorry for the late reply, because i will reinstall ubuntu coz now i have beta with alternate cd :mad: and now waiting a friend to give me another new one, until then( two days at most) nothing i will do
after then i will give a try for every idea you posted and give you a review

thanks again

---

