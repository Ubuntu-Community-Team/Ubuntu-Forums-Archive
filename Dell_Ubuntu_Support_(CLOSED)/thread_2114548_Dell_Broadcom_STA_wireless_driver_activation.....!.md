---
title: "Dell Broadcom STA wireless driver activation.....!!!"
date: 2013-02-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by satyamM on 2013-02-10
Hello UFers,

Whenever I try to activate Broadcom STA wireless driver, I get error as depicted in the attached picture.

Can someone help me?

---

### Post by coldraven on 2013-02-10
That is strange! I don't have any problem with Kubuntu 12.04, see screenshot.
I hope that someone knows the answer.

---

### Post by kc1di on 2013-02-10
Hi,

I've found this often happens on a new install that has not been upgraded yet.  so try this in a terminal

```
sudo apt-get update && sudo apt-get upgrade
```
then try again.

---

### Post by satyamM on 2013-02-10
> **kc1di said:**
> Hi,

I've found this often happens on a new install that has not been upgraded yet.  so try this in a terminal

```
sudo apt-get update && sudo apt-get upgrade
```then try again.


Still the **same error.**

I upgraded to 12.04 from 10.04 last October and from then I have  _**updated and upgraded**_ many times. So this is not working.

---

### Post by ugm6hr on 2013-02-10
Try CLI - lots of people have issues with STA using GUI:
```

sudo apt-get install bcmwl-kernel-source
sudo modprobe -r b43 ssb wl
sudo modprobe wl

```

A suitable reference: [http://www.howopensource.com/2012/10/install-broadcom-sta-wireless-driver-in-ubuntu-12-10-12-04/](http://www.howopensource.com/2012/10/install-broadcom-sta-wireless-driver-in-ubuntu-12-10-12-04/)

---

### Post by satyamM on 2013-02-10
> **ugm6hr said:**
> 
```

sudo apt-get install bcmwl-kernel-source
sudo modprobe -r b43 ssb wl
sudo modprobe wl

```


See attached image which displays the output of your suggested commands. 
[B]First one is already in the newest version. 
Rest two give FATAL error[/B] about **wl module** not being found.

---

### Post by kc1di on 2013-02-10
try this :

With a temporary ethernet connection, please do:

```
sudo apt-get install --reinstall bcmwl-kernel-source
```
After it's done, do:

```
sudo modprobe wl
```
If there is no error or warning, your wireless should be working.

---

### Post by satyamM on 2013-02-10
> **kc1di said:**
> try this :
With a temporary ethernet connection, please do:
```
sudo apt-get install --reinstall bcmwl-kernel-source
```After it's done, do:
```
sudo modprobe wl
```If there is no error or warning, your wireless should be working.


See attached image. **No success**.


.

---

### Post by kc1di on 2013-02-10
It almost looks like your trying to install this without being connected to the net?
or your repository list is out of date. can you list your /etc/apt/sources.list?
when you do a apt-get update do you get any error messages?
let's try this install synaptic if not already install 
go to it refresh it the do a search for bcmwl see if it shows anything.

---

### Post by satyamM on 2013-02-11
> **kc1di said:**
> It almost looks like your trying to install this without being connected to the net?
No I am connected to net, it is clearly shown in the screenshot shown at top left bar "two arrows upside down" tell this.
> 
or your repository list is out of date. can you list your /etc/apt/sources.list?
 I don't know if its out of date.  Here it is:
```

# deb http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu precise main # disabled on upgrade to precise
# deb http://ppa.launchpad.net/lucid-bleed/ppa/ubuntu precise main # disabled on upgrade to precise
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb http://dl.google.com/linux/talkplugin/deb/ stable main # disabled on upgrade to precise
# deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu precise main # disabled on upgrade to precise
# deb http://archive.canonical.com/ubuntu precise partner #Added by software-center
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://in.archive.ubuntu.com/ubuntu/ precise main universe multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ precise main universe multiverse

###### Ubuntu Update Repos
deb http://in.archive.ubuntu.com/ubuntu/ precise-security main universe multiverse
deb http://in.archive.ubuntu.com/ubuntu/ precise-updates main universe multiverse
deb http://in.archive.ubuntu.com/ubuntu/ precise-proposed main universe multiverse
deb http://in.archive.ubuntu.com/ubuntu/ precise-backports main universe multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ precise-security main universe multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ precise-updates main universe multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ precise-proposed main universe multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ precise-backports main universe multiverse

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd Party Binary Repos

#### FBReader - http://www.fbreader.org/desktop/
## Run this command: http://www.fbreader.org/desktop/debian/geometer.fbreader.org.asc -O- | sudo apt-key add -
# deb http://www.fbreader.org/desktop/debian stable main # disabled on upgrade to precise

#### GetDeb - http://www.getdeb.net
## Run this command: wget -q -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
# deb http://archive.getdeb.net/ubuntu lucid-getdeb apps # disabled on upgrade to precise

#### Google Linux Software Repositories - http://www.google.com/linuxrepositories/
## Run this command: wget -q https://dl-ssl.google.com/linux/linux_signing_key.pub -O- | sudo apt-key add -
# deb http://dl.google.com/linux/deb/ stable non-free # disabled on upgrade to precise

#### HandBrake Releases - http://handbrake.fr/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 816950D8
# deb http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu precise main # disabled on upgrade to precise

#### KDE 3.5 - https://launchpad.net/~kde3-maintainers
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 44869960
# deb http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu precise main # disabled on upgrade to precise

#### LibreOffice 3.3 - http://www.documentfoundation.org/download/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444
# deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu precise main # disabled on upgrade to precise

#### Mozilla Daily Build Team - http://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys  247510BE
# deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu precise main # disabled on upgrade to precise

#### PlayOnLinux - http://www.playonlinux.com
## Run this command: wget -q "http://deb.playonlinux.com/public.gpg" -O- | sudo apt-key add - 
# deb http://deb.playonlinux.com/ precise main # disabled on upgrade to precise

#### PPA for Kiwi Linux Members - http://kiwilinux.org/kiwi/en/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 85C2A3C7
# deb http://ppa.launchpad.net/kiwilinux-members/ppa/ubuntu precise main # disabled on upgrade to precise

#### Terminator - http://www.tenshu.net/terminator/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1BD3A65C
# deb http://ppa.launchpad.net/gnome-terminator/ppa/ubuntu precise main # disabled on upgrade to precise

#### Themes for GNOME and Ubuntu - https://edge.launchpad.net/~bisigi/+archive/ppa
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 881574DE
# deb http://ppa.launchpad.net/bisigi/ppa/ubuntu precise main # disabled on upgrade to precise

#### Ubuntu Tweak - http://ubuntu-tweak.com/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
# deb http://ppa.launchpad.net/tualatrix/ubuntu precise main # disabled on upgrade to precise

#### VirtualBox - http://www.virtualbox.org
## Run this command: wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
# deb http://download.virtualbox.org/virtualbox/debian precise contrib # disabled on upgrade to precise

#### VLC Media Player  - http://www.videolan.org/vlc/
## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40130828
# deb http://ppa.launchpad.net/c-korn/ppa/ubuntu precise main # disabled on upgrade to precise

#### Webmin - http://www.webmin.com
## Run this command: wget http://www.webmin.com/jcameron-key.asc -O- | sudo apt-key add -
# deb http://download.webmin.com/download/repository sarge contrib # disabled on upgrade to precise

#### Wine - https://launchpad.net/~ubuntu-wine/+archive/ppa/
## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9CB8DB0
# deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main # disabled on upgrade to precise

#### X Updates - https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AF1CDFA9
# deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu precise main # disabled on upgrade to precise


####### 3rd Party Source Repos

#### Chromium Project (Source) - http://code.google.com/chromium/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4E5E17B5
# deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu precise main # disabled on upgrade to precise

#### FBReader (Source) - http://www.fbreader.org/desktop/
## Run this command: http://www.fbreader.org/desktop/debian/geometer.fbreader.org.asc -O- | sudo apt-key add -
# deb-src http://www.fbreader.org/desktop/debian stable main # disabled on upgrade to precise

#### HandBrake Releases (Source) - http://handbrake.fr/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 816950D8
# deb-src http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu precise main # disabled on upgrade to precise

#### KDE 3.5 (Source) - https://launchpad.net/~kde3-maintainers
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 44869960
# deb-src http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu precise main # disabled on upgrade to precise

#### Kubuntu Backports (Source) - https://edge.launchpad.net/~kubuntu-ppa/+archive/backports
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8AC93F7A
# deb-src http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu precise main # disabled on upgrade to precise

#### LibreOffice 3.3 (Source) - http://www.documentfoundation.org/download/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444
# deb-src http://ppa.launchpad.net/libreoffice/ppa/ubuntu precise main # disabled on upgrade to precise

#### Mozilla Daily Build Team (Source) - http://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys  247510BE
# deb-src http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu precise main # disabled on upgrade to precise

#### PPA for Kiwi Linux Members (Source) - http://kiwilinux.org/kiwi/en/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 85C2A3C7
# deb-src http://ppa.launchpad.net/kiwilinux-members/ppa/ubuntu precise main # disabled on upgrade to precise

#### Terminator (Source) - http://www.tenshu.net/terminator/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1BD3A65C
# deb-src http://ppa.launchpad.net/gnome-terminator/ppa/ubuntu precise main # disabled on upgrade to precise

#### Themes for GNOME and Ubuntu (Source) - https://edge.launchpad.net/~bisigi/+archive/ppa
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 881574DE
# deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu precise main # disabled on upgrade to precise

#### Ubuntu Tweak (Source) - http://ubuntu-tweak.com/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
# deb-src http://ppa.launchpad.net/tualatrix/ubuntu precise main # disabled on upgrade to precise

#### VLC Media Player  (Source) - http://www.videolan.org/vlc/
## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40130828
# deb-src http://ppa.launchpad.net/c-korn/ppa/ubuntu precise main # disabled on upgrade to precise

#### Wine (Source) - https://launchpad.net/~ubuntu-wine/+archive/ppa/
## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9CB8DB0
# deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main # disabled on upgrade to precise

#### X Updates (Source) - https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AF1CDFA9
# deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu precise main # disabled on upgrade to precise

```



> 
when you do a apt-get update do you get any error messages?No I don't get any. Believe me on this.

> 
let's try this install synaptic if not already install
I already have synaptic.
> 
go to it refresh it the do a search for bcmwl see if it shows anything.See attached image.


One thing I forgot to tell is my laptop **easily detects a wireless connection** whenever it catches one and easily connects to it. So I am not really having problem with wireless  connection.** But I do have problem with Bluetooth.** Bluetooth doesn't start, actually it hasn't worked since I switched to Ubuntu from Win7. Just a icon is there on top left bar, as shown in image. So I think activating this wireless driver might solve my Bluetooth problem.

---

### Post by satyamM on 2013-02-11
@kc1di and others:   I have edited my last post. Please do see it. :D

---

