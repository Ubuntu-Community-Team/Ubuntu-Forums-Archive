---
title: "how install mint in ubuntu?"
date: 2013-02-15
forum: Desktop Environments
---

### Post by omid2s on 2013-02-15
how install mint desktop in ubuntu?

---

### Post by brent1975 on 2013-02-15
This is for the latest version of cinnamon desktop that mint uses.

```

sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable
sudo apt-get update
sudo apt-get install cinnamon
```



a google search came up with many different articles. But I got this from this article [here]("http://http://www.noobslab.com/2012/12/cinnamon-167-has-been-released-for.html")

---

### Post by Ravi5kumar on 2013-02-16
Mint comes with two desktop environments. Cinnamon (fork of gnome shell) and Mate (fork of Gnome 2).

If you want cinnamon the proceed as brent1975 said above.

To install Mate type this commands in terminal:

```
sudo add-apt-repository "deb http://packages.mate-desktop.org/repo/ubuntu [code-name] main"
```

where [distro-name] is the code-name of the Ubuntu version - oneiric, precise, quantal etc.

For example for Precise (Ubuntu 12.04) type:

```
sudo add-apt-repository "deb http://packages.mate-desktop.org/repo/ubuntu precise main"
```

Then Install Mate:

```
sudo apt-get update
sudo apt-get install mate-archive-keyring
sudo apt-get update
```

This installs base packages:

```
sudo apt-get install mate-core
```

The last command above installs only the packages required to run MATE. To install some extra packages like Mozo (Alacarte fork), MATE Netspeed, MATE Sensors Applet, MATE System Tools and others, use the following command:

```
sudo apt-get install mate-desktop-environment
```

Source : [http://askubuntu.com/questions/87040/how-to-install-mate](http://askubuntu.com/questions/87040/how-to-install-mate)

---

