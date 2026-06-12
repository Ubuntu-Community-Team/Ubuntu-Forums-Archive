---
title: "supertux install"
date: 2005-12-09
forum: Gaming &amp; Leisure
---

### Post by emerick7 on 2005-12-09
I've been trying to install supertux and have tried a few different ways.  In a terminal, I get the following code when I do 'apt-get install supertux':

> 
root@ubuntu:~# apt-get install supertux
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  supertux: Depends: libsdl-image1.2 (>= 1.2.3) but it is not installable
            Depends: libsdl-mixer1.2 (>= 1.2.6) but it is not installable
E: Broken packages
root@ubuntu:~#
 

In Synaptic, I search 'supertux' and get 'supertux' and 'supertux-data.'  I am able to click 'mark for installation' for 'supertux-data.'  When I click 'mark for installation' for supertux, I get the following:

> 
Could not mark all packages for installation or upgrade

The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences.

supertux:
 Depends: libsdl-image1.2 (>=1.2.3) but it is not installable
 Depends: libsdl-mixer1.2 (>=1.2.6) but it is not installable


I'd appreciate any help... thanks!

---

### Post by kagashe on 2005-12-10
[QUOTE=emerick7]I've been trying to install supertux and have tried a few different ways.  In a terminal, I get the following code when I do 'apt-get install supertux':

 

In Synaptic, I search 'supertux' and get 'supertux' and 'supertux-data.'  I am able to click 'mark for installation' for 'supertux-data.'  When I click 'mark for installation' for supertux, I get the following:



I'd appreciate any help... thanks![/QUOTE]Hi,
Please check whether you have following repositories enabled:
[http://archive.ubuntu.com.breezy/main](http://archive.ubuntu.com.breezy/main)
[http://archive.ubuntu.com.breezy/universe](http://archive.ubuntu.com.breezy/universe)

kagashe

---

### Post by emerick7 on 2005-12-10
I've looked around and haven't found a simple answer (but I'm sure it is), but how do I enable those repositories?  Thanks!

---

### Post by SickTwist on 2005-12-10
[QUOTE=emerick7]I've been trying to install supertux and have tried a few different ways.  In a terminal, I get the following code when I do 'apt-get install supertux':

 

In Synaptic, I search 'supertux' and get 'supertux' and 'supertux-data.'  I am able to click 'mark for installation' for 'supertux-data.'  When I click 'mark for installation' for supertux, I get the following:



I'd appreciate any help... thanks![/QUOTE]

We need to figure out why these packages cannot be installed:
libsdl-image1.2
libsdl-mixer1.2

Try running this command and post the output here:

sudo apt-get update ; sudo apt-get install libsdl-image1.2 libsdl-mixer1.2

---

### Post by emerick7 on 2005-12-10
I installed automatix a little bit ago, and then tried the supertux installation again, and it worked!  Not sure how it got working, but I'm assuming something got changed during automatix install.

---

### Post by SickTwist on 2005-12-10
Glad to hear it; Supertux is a great game.

Ah, the good old days of the original NES. Memories.. :)

---

