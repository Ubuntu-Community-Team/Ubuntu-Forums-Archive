---
title: "Saying hello"
date: 2007-06-05
forum: Florida Team - US
---

### Post by bobsomebody on 2007-06-05
Name's not important, just call me Bob :)

Im in Vero Beach, FL (center state, east coast). New to *nix and Ubuntu. Currently banging on a Feisty (7.04) Server edition.


Got it working for the most part. It runs as a router that hosts my apache2 server (PHP+MySQL also) but I cannot seem to get it to mod_rewrite at all. Its pretty much at a default install. Im getting through most of the how-to's but it would be nice to know some people at least remotely near by.

---

### Post by SkyyBugg on 2007-06-05
Hello Bob, I am in Tampa, FL.  I just looked at the version of Ubuntu Server that I just installed.  The file says 6.06.  It sounds like you have a newer version.
I got it on the network, now my first step is to get my desktop working.

the install ran quickly and easy..
are you on desktop yet?
SkyyBugg:p

---

### Post by SkyyBugg on 2007-06-05
Bob that version number looks like a Desktop edition.  Are you sure you have Server?

SkyyBugg  :popcorn:

---

### Post by feravolo on 2007-06-05
Hello:

The only difference between "desktop" and "server" is the "server" doesn't by default install an X-Windows Desktop such as KDE, Xfce or GNOME. Everything else is the same and you will be able to install and run any type of service (or daemon) that you like.

You problems are most likely related to file protections, which is way you need to install software using the sudo command.

The command sudo -s will let you remain the super user for a series of commands or you can set a root password:

sudo su  

passwd

If you are running a server you will also want to setup Open SSL so you can logon securely over the internet:

sudo apt-get install openssh-server

Hope this helped a little

---

### Post by bobsomebody on 2007-06-16
> **SkyyBugg said:**
> Bob that version number looks like a Desktop edition.  Are you sure you have Server?

SkyyBugg  :popcorn:

I am positive that I have server. I might have the Ver number wrong, or the short-name they hand out each one, or both. I know I have the latest server, for sake of correction. All is running well actually and I am about to reconfigure my laptop and desktop to ubuntu with wine untill i can find suitable apps to replace the ones I used from windows, specifically:

Zend Studio 5
Photoshop 7
Trillian 3.1
Alibre Design (CAD sys)
BobCAD v20 + v21

---

### Post by bobsomebody on 2007-06-16
> **feravolo said:**
> Hello:

The only difference between "desktop" and "server" is the "server" doesn't by default install an X-Windows Desktop such as KDE, Xfce or GNOME. Everything else is the same and you will be able to install and run any type of service (or daemon) that you like.

You problems are most likely related to file protections, which is way you need to install software using the sudo command.

The command sudo -s will let you remain the super user for a series of commands or you can set a root password:

sudo su  

passwd

If you are running a server you will also want to setup Open SSL so you can logon securely over the internet:

sudo apt-get install openssh-server

Hope this helped a little

Actually I want to keep SSH and SSL off for now, I dont do much remote operation at the moment and I opted to just block (via DROP not REJECT) the port all together and not install the packets.

I do understand the differences between Server and Desktop and I was able to get it all up and running.

I did have to pick my way throught:
Samba
Apache
PHP
MySQL
iptables
and a couple others I played around with.

Makes me wonder why i used windows so long.

---

### Post by bobsomebody on 2007-06-16
> **SkyyBugg said:**
> Hello Bob, I am in Tampa, FL.  I just looked at the version of Ubuntu Server that I just installed.  The file says 6.06.  It sounds like you have a newer version.
I got it on the network, now my first step is to get my desktop working.

the install ran quickly and easy..
are you on desktop yet?
SkyyBugg:p

I am actually setting up desktop on my tower today.

---

### Post by feravolo on 2007-06-17
I think that Zend has a Linux version, I am sure you already know about GIMP and the others you are going to have to think about what your requirements are and go though the thousands of available applications and/or find a decent windows emulator to meet them

> **bobsomebody said:**
> 
Makes me wonder why i used windows so long.

It's nice to be able to do anything you want with your systems isn't it ? Without having to pay an extra "$2200" for each copy of "Server" Software. or for that matter the $300 each for the "desktop" software.

---

### Post by bobsomebody on 2007-06-19
> **feravolo said:**
> I think that Zend has a Linux version, I am sure you already know about GIMP and the others you are going to have to think about what your requirements are and go though the thousands of available applications and/or find a decent windows emulator to meet them



It's nice to be able to do anything you want with your systems isn't it ? Without having to pay an extra "$2200" for each copy of "Server" Software. or for that matter the $300 each for the "desktop" software.

actually I think im just going to use BlueFish, it seems to do what I need, and then some :P

I guess im actually getting this all figured out pretty well as I am already helping others with server and desktop problems.

---

