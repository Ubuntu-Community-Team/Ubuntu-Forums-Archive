---
title: "Can't install beryl"
date: 2007-11-05
forum: Desktop Effects &amp; Customization
---

### Post by qbox on 2007-11-05
I try to install beryl with following commands

sudo sed -i '$adeb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main' /etc/apt/sources.list
wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -
sudo apt-get update

qbox@qboxcom:~$ sudo apt-get -y install beryl emerald-themes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  beryl: Depends: beryl-settings but it is not going to be installed
E: Broken packages

and Im stuck to here.
help? :confused:

---

### Post by ddrichardson on 2007-11-05
Are you running 7.10?

---

### Post by qbox on 2007-11-06
Yes
Ubuntu 7.10
On dell inspiron 1520

---

### Post by ddrichardson on 2007-11-06
I don't think that repository is yet been updated for Gutsy. Beryl is no more any way - have you tried compiz fusion? Its installed in Gutsy provided you have the restricted drivers running.

---

### Post by Forlong on 2007-11-06
> deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) **edgy** main
This can not work for obvious reasons.

There's no repository for Beryl on Gutsy available. If you really want to use Beryl (did you know it's a discontinued project?) you would have to compile from source.

---

