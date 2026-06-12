---
title: "Gnome 3 on ubuntu 10.10"
date: 2011-04-14
forum: Desktop Environments
---

### Post by velt on 2011-04-14
Maybe this is a newbie question, thats because im a newb. 
I was looking at some gnome 3 screens and looks pretty cool. Can it run on ubuntu 10.10? or to put it better, run over ubuntu 10.10?
Is still in beta or its safe to use?

---

### Post by velt on 2011-04-14
So i Have been doing a little bit of digging and they explained me that Kubuntu is KDE + ubuntu. That took me a while to understand. 
Now I think for what I have seen that I like GNOME 3 more than KDE, so the question is: can I install GNOME 3 on 10.10 or I have to go to the beta 11?

---

### Post by Frogs Hair on 2011-04-14
Here is an instruction for a PPA . There is always a risk of breakage  when using a PPA  . If in doubt make backups just in case.
```
sudo add-apt-repository ppa:ubuntu-desktop/gnome3-builds
``````
sudo apt-get update
``````
sudo apt-get install gnome3-session
```

When log in before you press enter choose Gnome 3 session on the panel  below the the greeter . Good Luck !

---

### Post by velt on 2011-04-15
> **Frogs Hair said:**
> Here is an instruction for a PPA . There is always a risk of breakage  when using a PPA  . If in doubt make backups just in case.
```
sudo add-apt-repository ppa:ubuntu-desktop/gnome3-builds
``````
sudo apt-get update
``````
sudo apt-get install gnome3-session
```When log in before you press enter choose Gnome 3 session on the panel  below the the greeter . Good Luck !

what will happen when ubuntu 11 is released with gnome 3? will I have compatibility issues on update?

---

### Post by nerdy_kid on 2011-04-15
Ubuntu is not going to (ever) use GNOME3, it uses Unity.  See: [http://en.wikipedia.org/wiki/Unity_(desktop_environment](http://en.wikipedia.org/wiki/Unity_(desktop_environment))

---

### Post by velt on 2011-04-15
well I tried the first part of the code, i will paste the details here:

velt@velt-Precision-M2400:~$ sudo add-apt-repository ppa:ubuntu-desktop/gnome3-builds
[sudo] password for velt: 
Error: can't find signing_key_fingerprint at [https://launchpad.net/api/1.0/~ubuntu-desktop/+archive/gnome3-builds](https://launchpad.net/api/1.0/~ubuntu-desktop/+archive/gnome3-builds)

So is that a no go for that repository for gnome 3?

---

### Post by velt on 2011-04-15
so i tried the command again and:

velt@velt-Precision-M2400:~$ sudo add-apt-repository ppa:ubuntu-desktop/gnome3-builds
Error reading [https://launchpad.net/api/1.0/~ubuntu-desktop/+archive/gnome3-builds:](https://launchpad.net/api/1.0/~ubuntu-desktop/+archive/gnome3-builds:) <urlopen error [Errno 8] _ssl.c:490: EOF occurred in violation of protocol>

---

### Post by clobercow on 2011-04-15
Error: can't find signing_key_fingerprint at [https://launchpad.net/api/1.0/~ubuntu-desktop/+archive/gnome3-builds](https://launchpad.net/api/1.0/~ubuntu-desktop/+archive/gnome3-builds)

---

### Post by Frogs Hair on 2011-04-15
Sorry I took that from another thread and it may be dated. try the link below.
[http://www.ubuntugeek.com/how-to-install-gnome3-on-ubuntu-11-04-nattyubuntu-10-10-maverick.html](http://www.ubuntugeek.com/how-to-install-gnome3-on-ubuntu-11-04-nattyubuntu-10-10-maverick.html)

---

### Post by velt on 2011-04-15
> **Frogs Hair said:**
> Sorry I took that from another thread and it may be dated. try the link below.
[http://www.ubuntugeek.com/how-to-install-gnome3-on-ubuntu-11-04-nattyubuntu-10-10-maverick.html](http://www.ubuntugeek.com/how-to-install-gnome3-on-ubuntu-11-04-nattyubuntu-10-10-maverick.html)

on that link it said: 
**For ubuntu 10.10 users**
 Open the terminal and run the following commands
 Note:- This PPA works but it  is outdated
 [INDENT]sudo add-apt-repository ppa:ubuntu-desktop/gnome3-builds
sudo apt-get update
sudo apt-get install gnome3-session
[/INDENT]

I tried it and:
velt@velt-Precision-M2400:~$ sudo add-apt-repository ppa:ubuntu-desktop/gnome3-builds
[sudo] password for velt: 
Error: can't find signing_key_fingerprint at [https://launchpad.net/api/1.0/~ubuntu-desktop/+archive/gnome3-builds](https://launchpad.net/api/1.0/~ubuntu-desktop/+archive/gnome3-builds)
velt@velt-Precision-M2400:~$

---

### Post by Frogs Hair on 2011-04-15
I can't find anything newer ,  the post was dated 4-11 and it the same thing I posted from the thread . It may be worth waiting two  weeks and attempt install it on 11.04  or wait for a new PPA for 10.10.

---

### Post by velt on 2011-04-16
> **Frogs Hair said:**
> I can't find anything newer ,  the post was dated 4-11 and it the same thing I posted from the thread . It may be worth waiting two  weeks and attempt install it on 11.04  or wait for a new PPA for 10.10.

Yeah I get it, I have been reading a lot about how gnome 3 is supposed to work with ubuntu 11.04, And even then, both 11 and gnome 3 are still in infancy, 
So I think I will wait for the official ubuntu 11 upgrade and then move to gnome 3.

---

### Post by clobercow on 2011-04-16
This key problem with a ppa is extremely annoying :mad::mad::mad:


How can I resolve this error?

---

### Post by velt on 2011-04-16
> **clobercow said:**
> This key problem with a ppa is extremely annoying :mad::mad::mad:


How can I resolve this error?

i dont know but for what i have read i think is best to wait until ubuntu 11. 
When is it going to be released?

---

### Post by nickdbliss on 2011-05-21
ppa:gnome3-team/gnome3 

Worked for me.

---

### Post by marcoftheknight on 2011-05-31
Hey ,

I'm getting the same thing was trying to load te GNome because im getting seriously frustrated with the Unity guesse ill just have to sweat it out lol. Im not joking 

tried the most recent post code got this message:

The following packages have unmet dependencies:
 gnome3-session : Depends: gnome-shell but it is not installable
E: Broken packages
marc@marc-GA-890GPA-UD3H:~$ sudo add-apt-repository ppa:gnome3-team/gnome3 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 9D542E3D52C801D9F8E31682F1773AF13B1510FD
gpg: requesting key 3B1510FD from hkp server keyserver.ubuntu.com
gpg: key 3B1510FD: public key "Launchpad PPA for GNOME3 Team" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)

---

### Post by kroq-gar78 on 2011-06-18
> **marcoftheknight said:**
> Hey ,

I'm getting the same thing was trying to load te GNome because im getting seriously frustrated with the Unity guesse ill just have to sweat it out lol. Im not joking 

tried the most recent post code got this message:

The following packages have unmet dependencies:
 gnome3-session : Depends: gnome-shell but it is not installable
E: Broken packages
marc@marc-GA-890GPA-UD3H:~$ sudo add-apt-repository ppa:gnome3-team/gnome3 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 9D542E3D52C801D9F8E31682F1773AF13B1510FD
gpg: requesting key 3B1510FD from hkp server keyserver.ubuntu.com
gpg: key 3B1510FD: public key "Launchpad PPA for GNOME3 Team" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
now what you do is 
```
sudo apt-get update
sudo apt-get install gnome-shell
```
and then it SHOULD work....

---

