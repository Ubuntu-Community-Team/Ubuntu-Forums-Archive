---
title: "installing Viewnior"
date: 2010-10-29
forum: Desktop Environments
---

### Post by pyrotechnician on 2010-10-29
hi

i'm trying to install Viewnior on my desktop and i can't get it done. i was using **[this page]("http://xsisqox.github.com/Viewnior/download.html")** and **[this one]("https://launchpad.net/%7Exsisqox/+archive/ppa")** as a reference, but something's not right, or i'm doing something wrong here..
can somebody pls explain to me how it should be done?
what command should i use? apt-get or aptitude?
```
sudo apt-get install viewnior
``` results with a message:
*Unable to locate package viewnior*

with this
```
sudo aptitude install viewnior
``` i get this message:
[I]aptitude: command not found

[/I]tia :)

---

### Post by cchhrriiss121212 on 2010-10-29
It is not in the Ubuntu repos, so you need to add the PPA that is described in the second link you posted.
Click on "Read about Installing" and follow the instructions.

---

### Post by pyrotechnician on 2010-10-29
i went through that before, this is what i get:
```
$ sudo apt-get install viewnior
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package viewnior
```i entered this:
*sudo add-apt-repository ppa:user/ppa-name*
and then this:
*sudo apt-get update*
and still receive message that it's unable to locate package viewnior.

i also tried entering PPA manually by copying this
```
deb [http://ppa.launchpad.net/xsisqox/ppa/ubuntu](http://ppa.launchpad.net/xsisqox/ppa/ubuntu) YOUR_UBUNTU_VERSION_HERE main 
deb-src [http://ppa.launchpad.net/xsisqox/ppa/ubuntu](http://ppa.launchpad.net/xsisqox/ppa/ubuntu) YOUR_UBUNTU_VERSION_HERE main 
```into sources.list. for ubuntu version i entered "maverick".

---

### Post by cchhrriiss121212 on 2010-10-29
> **pyrotechnician said:**
> i went through that before, this is what i get:
i entered this:
*sudo add-apt-repository ppa:user/ppa-name*
and then this:
*sudo apt-get update*
and still receive message that it's unable to locate package viewnior.


What you need to enter is this: 
sudo add-apt-repository** ppa:xsisqox/ppa**
then this:
sudo apt-get update

Now install using synaptic or with the command:
sudo apt-get install viewnior

The manual step you took failed as there is no PPA version for Maverick yet, you can see on the PPA page they go from Hardy to Lucid.

---

### Post by pyrotechnician on 2010-10-29
actually i did this before (only forgot to replace when c/p-ing) and it didn't work.
> What you need to enter is this: 
sudo add-apt-repository **ppa:xsisqox/ppa**
then this:
sudo apt-get update

i installed it successfully few minutes ago, by replacing this
```
deb http://ppa.launchpad.net/xsisqox/ppa/ubuntu maverick main 
deb-src http://ppa.launchpad.net/xsisqox/ppa/ubuntu maverick main 
```
with this:
```
deb http://ppa.launchpad.net/xsisqox/ppa/ubuntu lucid main 
deb-src http://ppa.launchpad.net/xsisqox/ppa/ubuntu lucid main 
```
in sources.list

ty for your help ):P

---

