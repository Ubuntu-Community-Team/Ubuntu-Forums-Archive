---
title: "&quot;apt-get install&quot; acutally deletes packages..."
date: 2009-05-16
forum: General Help
---

### Post by hob on 2009-05-16
I'm running an Ubuntu 8.10 virtual machine server on a Dell PowerEdge 2950 III. It works great, but I was having trouble installing a new JeOS virtual machine with python-vm-builder. It said package not found.

Curious on what happened to python-vm-builder (because I had used it earlier that week), I immediately became suspicious that I had been hacked. Going through the logs, another sysadmin tried to install the "python-" package by mistake, and apt-get deleted a bunch of stuff.

Here is a log of what I did, with the -s to Simulate the install:
```

user@server:~$ sudo apt-get install -s python-
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  debootstrap g++-4.3 libdate-manip-perl libgomp1 g++ gcc-4.3 kpartx gcc
  build-essential dpkg-dev libstdc++6-4.3-dev libc6-dev linux-libc-dev
  binutils make
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  command-not-found denyhosts kvm landscape-common logwatch lsb-release
  openssl-blacklist postfix python python-apt python-central python-cheetah
  python-dbus python-gdbm python-gnupginterface python-gobject python-libvirt
  python-libxml2 python-openssl python-pam python-pyopenssl python-serial
  python-support python-twisted-bin python-twisted-core python-urlgrabber
  python-virtinst python-vm-builder python-zopeinterface ssl-cert
  ubuntu-minimal ubuntu-virt-server ufw unattended-upgrades
  update-manager-core
0 upgraded, 0 newly installed, 35 to remove and 7 not upgraded.
Remv command-not-found [0.2.26ubuntu1.1]
Remv denyhosts [2.6-3]
Remv python-vm-builder [0.9-0ubuntu3.1]
Remv ubuntu-virt-server [1.2]
Remv kvm [1:72+dfsg-1ubuntu6.1]
Remv landscape-common [1.0.23-0ubuntu0.8.10.1]
Remv logwatch [7.3.6.cvs20080702-1ubuntu2]
Remv update-manager-core [1:0.93.34]
Remv ubuntu-minimal [1.124]
Remv unattended-upgrades [0.32ubuntu2]
Remv python-apt [0.7.7.1ubuntu4]
Remv lsb-release [3.2-14ubuntu2]
Remv postfix [2.5.5-1]
Remv ssl-cert [1.0.23]
Remv openssl-blacklist [0.4.2]
Remv ufw [0.23.3]
Remv python-virtinst [0.300.3-5ubuntu3]
Remv python-libxml2 [2.6.32.dfsg-4ubuntu1.1]
Remv python-libvirt [0.4.4-3ubuntu3.1]
Remv python-cheetah [2.0.1-2]
Remv python-twisted-core [8.1.0-4]
Remv python-zopeinterface [3.3.1-7build1]
Remv python-twisted-bin [8.1.0-4]
Remv python-urlgrabber [3.1.0-4]
Remv python-pyopenssl [0.7-2]
Remv python-openssl [0.7-2]
Remv python-gobject [2.15.3-0ubuntu5]
Remv python-gnupginterface [0.3.2-9ubuntu1]
Remv python-dbus [0.82.4-2]
Remv python-support [0.8.4]
Remv python-serial [2.3-1]
Remv python-pam [0.4.2-12ubuntu2]
Remv python-gdbm [2.5.2-1ubuntu1]
Remv python-central [0.6.7ubuntu1]
Remv python [2.5.2-1ubuntu1]
user@server:~$ 

```

What? Install actually removes packages? Is this a bug in apt-get, or feature that deletes packages if you add a - after? I also can confirm this in 9.04 Desktop edition, with at total of 222 packages to remove.

---

### Post by sgosnell on 2009-05-16
Depending on what you're installing, yes, it will remove packages.  Sometimes old packages have to be removed in order to install newer ones.

---

### Post by hob on 2009-05-16
Yes, I will agree with you that sometimes (very very rarely) packages need to be removed to upgrade or install new ones. Video card/sound drivers come to mind....

However, as you can see in the simulation **0 upgraded, 0 newly installed, 35 to remove and 7 not upgraded**, nothing was installed, or even planned to be installed.

Also, there is no package named "python-", so apt-get should have error-ed out immediately. Any other ideas?

---

### Post by lisati on 2009-05-16
> 
The following packages were automatically installed and are no longer required:

[COLOR="White"]......[/COLOR]

---

### Post by paradigm2 on 2009-05-16
I believe even though he used "apt-get install", a minus sign at the end of a package tells it to remove it!

[http://linux.die.net/man/8/apt-get](http://linux.die.net/man/8/apt-get)

> 
install
    install is followed by one or more packages desired for installation. Each package is a package name, not a fully qualified filename (for instance, in a Debian GNU/Linux system, libc6 would be the argument provided, not libc6_1.9.6-2.deb). All packages required by the package(s) specified for installation will also be retrieved and installed. The /etc/apt/sources.list file is used to locate the desired packages. **If a hyphen is appended to the package name (with no intervening space), the identified package will be removed if it is installed. Similarly a plus sign can be used to designate a package to install. These latter features may be used to override decisions made by apt-get's conflict resolution system.** 


---

### Post by albinootje on 2009-05-16
> **paradigm2 said:**
> I believe even though he used "apt-get install", a minus sign at the end of a package tells it to remove it!

[http://linux.die.net/man/8/apt-get](http://linux.die.net/man/8/apt-get)

Interesting, but where exactly did you read that in that manual page ? I searched for "minus" and "dash" but found nothing.

---

### Post by paradigm2 on 2009-05-16
> **albinootje said:**
> Interesting, but where exactly did you read that in that manual page ? I searched for "minus" and "dash" but found nothing.

They use the terminology "hyphen". :)

Under Description -> Install.  First paragraph.

It was new to me as well.... I was in doubt so I checked the man page.

---

### Post by albinootje on 2009-05-16
> **paradigm2 said:**
> They use the terminology "hyphen". :)

Under Description -> Install.  First paragraph.

It was new to me as well.... I was in doubt so I checked the man page.

Cool, thanks!

---

### Post by sgosnell on 2009-05-17
If you want to remove all packages with the pattern 'python-', then use 'sudo apt-get install python-*'.  The * is a wildcard, and that should get every package that starts with 'python-'.

---

