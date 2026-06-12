---
title: "Steam error today"
date: 2013-02-23
forum: Gaming &amp; Leisure
---

### Post by send2 on 2013-02-23
I have Ubuntu 12.04 LTS with steam running ok untill just a minute ago now i have a loop going with the terminal. When i tried to open a game just a minute ago, the steam app wanted to update itself i said ok and now i get this from the terminal: 

 a) Steam needs to install these additional packages: 
    steam-launcher
[sudo] password for warrior: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package steam-launcher
Press return to continue: 

when i hit return their installer downloads their app but then i got this:
Steam needs to install these additional packages: 
    steam-launcher
[sudo] password for warrior: 

then when i enter my password i get the above a) ad infinitum

how can i install the package steam-launcher so i can get out of this loop from  the terminal?

thanks for any help coming my way

Here is also a pic depicting a conflict with installed steam package. The strange thing is that everything was working fine from my end.

And now i am getting this error
Steam needs to install these additional packages: 
    steam-launcher, curl
[sudo] password for warrior: 
Sorry, try again.
[sudo] password for warrior:

---

### Post by siekier on 2013-02-23
I solved that problem by uninstalling steam from ubuntu:
```
sudo aptitude purge steam64
```
And then installing steam-launcher:
```
sudo aptitude install steam-launcher
```
I also clean all steam folders in my home dir, before installing launcher, but im not sure if its necessary.
I hope this will help.

---

### Post by send2 on 2013-02-23
> **siekier said:**
> I solved that problem by uninstalling steam from ubuntu:
```
sudo aptitude purge steam64
```And then installing steam-launcher:
```
sudo aptitude install steam-launcher
```I also clean all steam folders in my home dir, before installing launcher, but im not sure if its necessary.
I hope this will help.

Hi siekier,

i got the following from my terminal:

warrior@warrior-Satellite-A505:~$ sudo aptitude purge steam64
[sudo] password for warrior: 
sudo: aptitude: command not found
warrior@warrior-Satellite-A505:~$ 

thanks for your reply

---

### Post by siekier on 2013-02-23
Use apt-get insted aptitude :
```
sudo apt-get purge steam64
sudo apt-get install steam-launcher
```
Aptitude its kind of apt-get replacemnt which I am using, sorry for confusion.

---

### Post by UnrefinedIron on 2013-02-23
Similarly, updating and installing worked for me.

sudo apt-get update
sudo apt-get install steam-launcher

---

### Post by send2 on 2013-02-24
> **siekier said:**
> Use apt-get insted aptitude :
```
sudo apt-get purge steam64
sudo apt-get install steam-launcher
```Aptitude its kind of apt-get replacemnt which I am using, sorry for confusion.

No problem :)

> **UnrefinedIron said:**
> Similarly, updating and installing worked for me.

sudo apt-get update
sudo apt-get install steam-launcher

Hi siekier, UnrefinedIron, 

when i ran the commands suggested above I got the following:
```
       warrior@warrior-Satellite-A505:~$ sudo apt-get purge steam64
[sudo] password for warrior: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ttf-umefont liboce-ocaf1 libgl2ps0 liboce-visualization1
  libdrm-nouveau1a:i386 liboce-foundation1 ttf-unfonts-core liboce-modeling1
  liboce-ocaf-lite1 libcurl3-gnutls:i386 ttf-droid libllvm3.0:i386
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  steam64*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 27.6 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 408734 files and directories currently installed.)
Removing steam64 ...
warrior@warrior-Satellite-A505:~$ sudo apt-get install steam-launcher
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package steam-launcher
warrior@warrior-Satellite-A505:~$
  
```What to do next? How can I install the missing package steam-launcher?  thanks for the help given so far.....

---

### Post by thnewguy on 2013-02-24
Make sure you update your package information. The following worked for me on my 64-bit install:

```

sudo apt-get remove steam
sudo apt-get update
sudo apt-get install steam

```

With the updated repository information, installing Steam should automatically pull in the launcher dependency.

---

### Post by send2 on 2013-02-24
> **thnewguy said:**
> Make sure you update your package information. The following worked for me on my 64-bit install:

```

sudo apt-get remove steam
sudo apt-get update
sudo apt-get install steam

```With the updated repository information, installing Steam should automatically pull in the launcher dependency.

Hi thnewguy,

thanks for your help, I will check your code out. Thanks for the dependency tip.


I am marking this thread solved, I am not sure yet if my problem cleared up but it seems to be working ok. If I have more problems I will open it back up, thanks to all of you who helped :)

---

