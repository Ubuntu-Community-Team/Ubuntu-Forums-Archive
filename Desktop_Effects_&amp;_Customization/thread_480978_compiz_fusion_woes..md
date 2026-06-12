---
title: "compiz fusion woes."
date: 2007-06-22
forum: Desktop Effects &amp; Customization
---

### Post by BoneSaw on 2007-06-22
i read up about compiz fusion and was trying to install using this guide:

[http://forums.opencompositing.org/viewtopic.php?f=14&t=131](http://forums.opencompositing.org/viewtopic.php?f=14&t=131)

everything was going fine but on the second step i accidentally dropped my remote on my keyboard, which inserted some random characters and messed up my install. so now the packages compiz and compiz-gnome are broken when i run apt in terminal it tells me to run 

```
sudo apt-get -f install
```

which returns

```
bonesaw@monarch:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  compiz-gnome
The following packages will be upgraded:
  compiz-gnome
1 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
1 not fully installed or removed.
Need to get 0B/165kB of archives.
After unpacking 1286kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  compiz-gnome
Install these packages without verification [y/N]? Y
(Reading database ... 132254 files and directories currently installed.)
Preparing to replace compiz-gnome 1:0.3.6-1ubuntu13 (using .../compiz-gnome_1%3a0.5.0+git20070619~3v1ubuntu6_i386.deb) ...
Unpacking replacement compiz-gnome ...
dpkg: error processing /var/cache/apt/archives/compiz-gnome_1%3a0.5.0+git20070619~3v1ubuntu6_i386.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-gnome_1%3a0.5.0+git20070619~3v1ubuntu6_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

synaptic returns a similar error. what do i need to do?

---

### Post by crazyhunk on 2007-06-22
> **BoneSaw said:**
> i read up about compiz fusion and was trying to install using this guide:

[http://forums.opencompositing.org/viewtopic.php?f=14&t=131](http://forums.opencompositing.org/viewtopic.php?f=14&t=131)

everything was going fine but on the second step i accidentally dropped my remote on my keyboard, which inserted some random characters and messed up my install. so now the packages compiz and compiz-gnome are broken when i run apt in terminal it tells me to run 

```
sudo apt-get -f install
```

which returns

```
bonesaw@monarch:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  compiz-gnome
The following packages will be upgraded:
  compiz-gnome
1 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
1 not fully installed or removed.
Need to get 0B/165kB of archives.
After unpacking 1286kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  compiz-gnome
Install these packages without verification [y/N]? Y
(Reading database ... 132254 files and directories currently installed.)
Preparing to replace compiz-gnome 1:0.3.6-1ubuntu13 (using .../compiz-gnome_1%3a0.5.0+git20070619~3v1ubuntu6_i386.deb) ...
Unpacking replacement compiz-gnome ...
dpkg: error processing /var/cache/apt/archives/compiz-gnome_1%3a0.5.0+git20070619~3v1ubuntu6_i386.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-gnome_1%3a0.5.0+git20070619~3v1ubuntu6_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

synaptic returns a similar error. what do i need to do?

I had the same error.....it is not becoz of u dropping a remote... it happens when u directly try to install fusion on desktop effects....

I believe u are using trevinos repos...
so just indent it (add a '#' before the deb.....)

and then run 

sudo apt-get -f install

now this uninstalls desktop effects..... so u need to install it again from ubuntus repos....

but i am not too sure how to get fusion working from here....

hope it does help a little... :)

__________________________________________

EDIT: ok I hav managed to install fusion and it works now.....

first goto synaptic and do a complete removal of the already installed compiz in ur system.... and also the 'ubuntu-desktop'

next you can follow the trevinos reps to get fusion working......

if u need trevinos indtructions... go here..

```
http://forums.opencompositing.org/viewtopic.php?f=14&t=131
```

i u have any more problems come up here.... i will try to help u...

---

### Post by lolwhites on 2007-06-22
Hi

I followed the advice in the thread you link to. Now, when I type *compiz --replace*, the window borders disappear.

---

### Post by joeblow1102 on 2007-06-22
if you search the forums for compiz title bar, you'll see this is a pretty common error.

one fix located here: [http://ubuntuforums.org/showthread.php?t=452714&highlight=compiz+title+bar]("http://ubuntuforums.org/showthread.php?t=452714&highlight=compiz+title+bar")

---

### Post by lolwhites on 2007-06-22
Thanks. I actually managed to sort it out, but can't remmeber how I did it.

---

