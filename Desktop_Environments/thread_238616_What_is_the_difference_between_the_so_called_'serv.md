---
title: "What is the difference between the so called 'server' CD and alternate CD"
date: 2006-08-17
forum: Desktop Environments
---

### Post by harisund on 2006-08-17
So I downloaded both the 'server' CD and the alternate install CD. Here are my options. 

1. Boot with the server CD
--> 1.1 Install a server
--> 1.2 Install LAMP
2. Boot with the alternate CD
--> 2.1 Install in text mode
--> 2.2 Install in OEM mode
--> 2.3 Install a server

First, when Ubuntu mean server, what server are they having in mind? File server? Web server? At the very least a SSh server? Why does the name 'server' come into picture? 

What is the difference between 1.1 and 2.3? What server gets installed? 

Since option 1.2 is the webserver, I am guessing the other great 'server' option is either a file server, SSH server, samba server or something ...is it?

---

### Post by az on 2006-08-18
> **harisund said:**
> 
1. Boot with the server CD
--> 1.1 Install a server
--> 1.2 Install LAMP
2. Boot with the alternate CD
--> 2.1 Install in text mode
--> 2.2 Install in OEM mode
--> 2.3 Install a server

First, when Ubuntu mean server, what server are they having in mind? File server? Web server? At the very least a SSh server? Why does the name 'server' come into picture? 
Good question.

From a security point of view, it is best to not run anything you don't need.  A "server" install is a base system installation, on which you can install your server applications.

> **harisund said:**
> 

What is the difference between 1.1 and 2.3? What server gets installed? 

BOth are base systems.  Using the server CD, you get a server kernel.  Using the alternate cd, you get the 386 desktop kernel.  The server kernel does not run on a pentium 1 (It's 686 or better...)


> **harisund said:**
> 
Since option 1.2 is the webserver, I am guessing the other great 'server' option is either a file server, SSH server, samba server or something ...is it?

It's whatever you want.

---

### Post by Dr. Nick on 2006-08-18
Just to clarify at the start, No matter what cd you install from you can always end up at the same point. Everything that can be done on one can be done on the other, just may take a bit of work

The server cd install will only have a command line login by default, it will also install a special kernel for servers (web,ftp,etc....) This kernel will not have the best hardware support so If you plan to use it as a workstation it is not recommended, stuff like USB may not work aswell on the server kernel.

The alternate install cd is for those who cant/dont want to use the live cd. Before dapper the alternate cd was all that was used.

The server install off the alt cd will install the desktop kernel and boot into the command line, just a regular install from the alt cd will use the desktop kernel and boot a gui.

If you install off the alt cd you can still install web,ftp, or any server using apt-get/aptitude.

Their are different cds just to help speed up deployement, If you know you are going to use a web server and do not need a gui then the server cd is a good choice as a default install is closer to where you want to be then a regular install with a full gui.

The server install from the alt cd is nice if you do not to use gnome or kde as you gui, Some people like other interfaces better, and instead of installing a full interface you dont want you just install the base then install the ui you want

---

### Post by harisund on 2006-08-18
AWESOME! As usual the forums have refused to fail me :D

The fact that the server's server installation comes with a server kernel and the alternate's server installation comes with a regular kernel is indeed new to me. 

Thanks a bunch guys! That's all I needed to know :)

---

