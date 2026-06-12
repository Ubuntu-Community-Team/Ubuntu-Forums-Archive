---
title: "Did I break open office?"
date: 2009-04-14
forum: General Help
---

### Post by twinkletoes2007 on 2009-04-14
Hello!

I was attempting to install Open Office 3.0 on Ubuntu 8.10. 

I started following the instructions for this website-
[http://www.tectonic.co.za/?p=3363](http://www.tectonic.co.za/?p=3363)

and used 

sudo apt-get remove openoffice*.* 

in the terminal. I am now trying to install it again from the synaptic manager because I found an easier way to upgrade it. It gives me an error that looks like this-

openoffice.org-base:
 Depends: openoffice.org-core but it is not going to be installed
 Depends: openoffice.org-base-core but it is not going to be installed
 Depends: libstlport4.6ldbl  but it is not installable
 Depends: ure but it is not going to be installed

I reloaded the package manager before I had done that. I'm sure I'm just being a bit of a newbie, but I'd appreciate your help!

---

### Post by ajmctaggart on 2009-04-14
I'm not sure why that method is used, but it's not necessary to use a .deb or a tar, simply need to add some new repositories and you can install from the terminal or from Synaptic after that...

Taken from this thread
[http://ubuntuforums.org/archive/index.php/t-963786.html]("http://ubuntuforums.org/archive/index.php/t-963786.html")



> sayems
October 30th, 2008, 05:44 PM
$ sudo gedit /etc/apt/sources.list

## Openoffice.org
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

$ sudo apt-get update

It should solve all your SERIOUS problem.

---

### Post by twinkletoes2007 on 2009-04-14
Okay I tried adding-

## Openoffice.org
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

to the list that came up when I typed
sudo gedit /etc/apt/sources.list

and told it to update it. It appeared to update it. 
I'm still getting the error

"openoffice.org:
 Depends: openoffice.org-core but it is not going to be installed
 Depends: openoffice.org-writer but it is not going to be installed
 Depends: openoffice.org-calc but it is not going to be installed
...."


My problem is a little bit different from that past thread I think. I can't even get Open Office 2.4 back from the Synaptic Packager Manager because of these errors.

Thank you for looking at my problem though.

---

### Post by twinkletoes2007 on 2009-04-14
Oh wait I got it. 

I had to go back and change the things I had changed in the Software Sources back to the default.

---

### Post by ajmctaggart on 2009-04-14
That was my next comment... :)

It's best whenever possible to use repositories, because as updates come out, you'll get them...

A little different than other OS's that have you install stuff everywhere and each app has its own updates, Linux in general is *usually based on repositories, making it much smoother, and less invasive, I feel...

Hope it's working!

---

