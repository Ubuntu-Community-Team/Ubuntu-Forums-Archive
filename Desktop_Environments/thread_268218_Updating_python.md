---
title: "Updating python"
date: 2006-09-29
forum: Desktop Environments
---

### Post by elpuerco on 2006-09-29
I see that python 2.5 is now released and I was looking into updating my Kubuntu 6.06.1 installation.

I am currently downloading the tarball but before installing wanted to check whether I need to use adept to remove all previous python stuff?

Thnx

---

### Post by Anonii on 2006-09-29
Install the package  "python2.5" with APT.
Then you will use python2.5 with the command "python2.5". I dont know a way to use python2.5 with the command "python" except if you change it using the alias of ~/.bashrc.

Good luck.

---

### Post by elpuerco on 2006-09-29
dont suppose you can give me the command to do this?

is it something like...

sudo apt-get install python2.5 ?

---

### Post by Anonii on 2006-09-29
> **elpuerco said:**
> dont suppose you can give me the command to do this?

is it something like...

sudo apt-get install python2.5 ?
Yes, sudo apt-get install python2.5, would do the trick :]

---

### Post by elpuerco on 2006-09-29
nope?  it says it cannot find python2.5 I tried python-2.5 too but still the same?

I think I have all the repositories available...

---

### Post by Jukey on 2006-09-29
Check in synaptic or adept

---

### Post by Anonii on 2006-09-29
> **elpuerco said:**
> nope?  it says it cannot find python2.5 I tried python-2.5 too but still the same?

I think I have all the repositories available...
[I]sudo apt-get update
sudo apt-cache search python | grep 2.5
[/I]
Find the package using this. 
(If you dont have the apt-cache command, use "sudo apt-get install apt-cache")
and download it using apt-get like before.
It was python2.5 for me, dunno why it isnt for you.

---

### Post by elpuerco on 2006-09-29
OK did sudo apt-get update

did the grep line and got nothing back just the prompt.

did the install apt-cache and get cannot find package error?

I have loads of repositories enabled including the universe ones?

---

### Post by Anonii on 2006-09-29
Well, thats weird. What does:

[B]sudo apt-cache search python
[/B]
gives you?

---

### Post by elpuerco on 2006-09-29
screen full of entries scrolling down.....

---

### Post by Anonii on 2006-09-29
> **elpuerco said:**
> screen full of entries scrolling down.....
Great.

Copy paste this:

sudo apt-cache search python | grep 2.5

If it doesnt work again, check all that ouput from that previous command (sudo apt-cache search python) and find the 2.5 package.
If there is no 2.5 package, I give up. Couldnt find a .deb of it, either :/

(Also check /etc/apt/sources.list and see if every rep is uncommented. Dont start uncommenting everything, most of the commented lines are notes on how to use that config file.)

---

### Post by elpuerco on 2006-09-29
I ran sudo apt-cache search kate and it returned a load of guff so that works ok.

So there must be a problem me thinks with the repositories but I used the source generator from the ubuntu nl site to create mine?

---

### Post by elpuerco on 2006-09-29
the grep for python only returns up to 2.4.

I am on Kubuntu LTS 6.06.1 is that what you are on?

---

### Post by elpuerco on 2006-09-29
my sources list file:

# Automatically generated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#

# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper main restricted

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper-updates main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)

deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper main restricted

deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper-updates main restricted

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper universe multiverse

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)

deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper universe multiverse

deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)

deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main

# Cipherfunk multimedia packages (sources, GPG key: 33BAC1B3)

deb-src [ftp://cipherfunk.org/pub/packages/ubuntu](ftp://cipherfunk.org/pub/packages/ubuntu) dapper main

# kubuntu.org packages for the latest KDE version (packages, GPG key: DD4D5088)

deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) dapper main

# kubuntu.org packages for the latest KDE version (sources, GPG key: DD4D5088)

deb-src [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) dapper main

# kubuntu.org packages for the latest Koffice version (packages, GPG key: DD4D5088)

deb [http://kubuntu.org/packages/koffice-latest](http://kubuntu.org/packages/koffice-latest) dapper main

# kubuntu.org packages for the latest Koffice version (sources, GPG key: DD4D5088)

deb-src [http://kubuntu.org/packages/koffice-latest](http://kubuntu.org/packages/koffice-latest) dapper main

# kubuntu.org packages for the latest amaroK version (packages, GPG key: DD4D5088)

deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main

# kubuntu.org packages for the latest amaroK version (sources, GPG key: DD4D5088)

deb-src [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main

# Penguin Liberation Front (packages)

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) dapper free non-free

# Penguin Liberation Front (sources)

deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) dapper free non-free

# Bleeding edge wine packages (packages)

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

# Bleeding edge wine packages (sources)

deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

---

### Post by elpuerco on 2006-09-30
OK I could not get apt-get to find python2.5 at all!

So I downloaded the tarball to my home folder and did the following:

sudo ./configure

sudo make

the screen scrolledfor an age obviously building the application I guess and then returned to the prompt.

when I type python I still get the original 2.4 running and cannot locate where or how to fire up 2.5?

I knew there was a reason why it is better to use adept as now I have a gazillion pyhton2.5 files installed on my system, don't know where they are or how to run them!

Help anyone?

---

### Post by Anonii on 2006-09-30
> **elpuerco said:**
> OK I could not get apt-get to find python2.5 at all!

So I downloaded the tarball to my home folder and did the following:

sudo ./configure

sudo make

the screen scrolledfor an age obviously building the application I guess and then returned to the prompt.

when I type python I still get the original 2.4 running and cannot locate where or how to fire up 2.5?

I knew there was a reason why it is better to use adept as now I have a gazillion pyhton2.5 files installed on my system, don't know where they are or how to run them!

Help anyone?
Adept and Synaptic, is just a GUI for the apt-get commands I gave you, they are not gonna help you much, and GUI sucks anyway :P

Well, if ./configure, configured the tarball correctly and returned no errors, then make would compile the program all right. If that ended without errors too, then "make install" would finish that thing. And it would get installed.

Then you can use python, using the "python2.5" command, like I said before.


(There is "check install" too, that would build a Debian package from the tarball, but lets not complicate this further.)

---

### Post by elpuerco on 2006-09-30
Kool!!!!  Thnx that did it.

I had not completed the process by running make install!

Now why I type python I get the 2.5 version.

Cheers :D

---

### Post by Anonii on 2006-09-30
> **elpuerco said:**
> Kool!!!!  Thnx that did it.

I had not completed the process by running make install!

Now why I type python I get the 2.5 version.

Cheers :D
Also, just for the final "touch"

When you are instaling programs from tarballs, they dont get added to the dpkg list and they cant get removed using APT. To do that, you have to replace the  "make install" step with "check install" if you have the checkinstall package installed. When you do that, a .deb package will get generated which you can install using the "sudo dpkg -i <package_name>.deb" command!

---

