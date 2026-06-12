---
title: "Fix broked dependencies in KDE"
date: 2013-03-05
forum: Desktop Environments
---

### Post by mikael.springer on 2013-03-05
Hi.

I'm new to Ubuntu but not to Linux in general (I'm an openSUSE user used to zypper and rpm, not apt-get and deb).

At work I've been given a machine that has been upgraded from the previous LTS release to 12.04 LTS. It had only the Ubuntu desktop installed. I started with installing KDE with the following command:

```

sudo apt-get install kde-full

```

I then proceeded with upgrading KDE to the latest 4.10 with the following commands

```

sudo add-apt-repository ppa:kubuntu-ppa/backports
sudo apt-get update
sudo apt-get upgrade

```

I wasn't satisfied with the result however and wanted to downgrade to the default KDE version in 12.04 LTS so I did the following:

```

sudo apt-get install ppa-purge
sudo ppa-purge ppa:kubuntu-ppa/backports
sudo apt-get autoremove

```

I think I also removed the ppa source list in directory /etc/apt/sources.list.d when the above commands had finished but I'm not shure, it's not there now anyhow.

But now I'm stuck with an unusable KDE. If I try to reinstall the package kde-full to get a full default KDE environment I get the following error:

```

mikspr@rhino:/etc/apt/sources.list.d$ sudo apt-get install kde-full
[sudo] password for mikspr: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 kde-full : Depends: kde-plasma-desktop (>= 5:71~pre15ubuntu12.4) but it is not going to be installed
            Depends: kde-plasma-netbook (>= 5:71~pre15ubuntu12.4) but it is not going to be installed
            Depends: kdeartwork (>= 4:4.8.2) but it is not going to be installed
            Depends: kdeplasma-addons (>= 4:4.8.2) but it is not going to be installed
            Recommends: kde-standard (>= 5:71~pre15ubuntu12.4) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
mikspr@rhino:/etc/apt/sources.list.d$ 

```

I've tried a number of different things but nothing works. I need some help to move forward.

Regards, Micke.

---

### Post by speartip on 2013-03-07
I know this isn't helpful, but I did the same thing on my 12.04 Kubuntu desktop.
Once I had 4.10 installed, I had a number of plasma crashes, so decided to do a "ppa purge".
This screwed up my desktop big time.
Ended up doing a complete re-install.
That might be your best option.

---

### Post by ibjsb4 on 2013-03-07
Maybe try to remove KDE

[http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu)

---

### Post by Zteam on 2013-03-07
try sudo apt-get install -f

That will tell APT to try to repair any packages error it can find.

---

