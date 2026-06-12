---
title: "Few Problems after install 64bit"
date: 2009-03-22
forum: General Help
---

### Post by Socoj2 on 2009-03-22
Downloaded and installed 64bit on a dell m1530.

Video drivers working everything else working.

The 2 things i am having a problem with are. Flash and Wine.

> ocoj2@socoj2-laptop:~$ sudo apt-get install ia32-libs lib32asound2 libc6-i386 lib32nss-mdns
[sudo] password for socoj2:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
ia32-libs: Depends: lib32gcc1 but it is not going to be installed

So then i did:
root@socoj2-laptop:/home/socoj2# apt-get install lib32gcc1
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
lib32gcc1: Depends: gcc-4.3-base (= 4.3.2-1ubuntu11) but 4.3.2-1ubuntu12 is to be installed
Depends: libc6-i386 (>= 2.5) but it is not going to be installed
E: Broken packages

and:

apt-get install libc6-i386

libc6-i386: Depends: libc6 (= 2.8~ 20080505-0ubuntu7) but 2.8~20080505-0ubuntu9 is to be installed


Depends: lib32stdc++6 but it is not going to be installed
libc6-i386: Depends: libc6 (= 2.8~20080505-0ubuntu7) but 2.8~20080505-0ubuntu9 is to be installed
E: Broken packages

Flash i ran a script i found on these forums to install the ndiswrapper version of the 32 bit. It said successfull but flash didnt install. I also tried downloading the 64bit plugin from adove and putting it in mozzilla/plugins directory and it still doesnt show.

I used synaptics to fix broken packages and it says sucessfull but still no joy.

Thanks for your help.

---

### Post by Therion on 2009-03-22
For Flash just install the Restricted Extras package, thusly:```
sudo apt-get install ubuntu-restricted-extras
```

Wine should be installable from "Add/Remove".

---

### Post by Socoj2 on 2009-03-22
Restricted Extras was installed. and still no flash.

I tried wine from the Add/Remove and still no luck.

When trying to install wine with add/remove it says "wine can not be installed on your computer type (AMD64) Either it requires special hardware or the vendor has decided not to support your computer type.

---

### Post by men28 on 2009-03-22
Download Flash player from there:
[http://get.adobe.com/flashplayer/]("http://get.adobe.com/flashplayer/")
and then for Firefox extract and copy an .so file to ~/.mozilla/plugins

This worked for me very fine.

---

### Post by oldos2er on 2009-03-22
Check System, Administration, Software Sources to make sure all repositories are enabled. You can run "sudo apt-get install -f" to fix your broken packages.

---

### Post by hp owner on 2009-03-22
i too am also having problems with flash, im running 64 bit ubuntu, and when i go to youtube, i get just a Grey box were the video should play


> Download Flash player from there:
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
and then for Firefox extract and copy an .so file to ~/.mozilla/plugins

This worked for me very fine. 

that is for 32bit not 64 bit

---

### Post by oldos2er on 2009-03-22
64-bit flash is here: [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz)

---

### Post by Socoj2 on 2009-03-22
> **oldos2er said:**
> Check System, Administration, Software Sources to make sure all repositories are enabled. You can run "sudo apt-get install -f" to fix your broken packages.

all repositories are enabled...


> socoj2@socoj2-laptop:~$ sudo apt-get install -f
[sudo] password for socoj2: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsm-dev libice-dev libpthread-stubs0 x11proto-kb-dev xtrans-dev
  libxcb-xlib0-dev libxau-dev libxcb1-dev x11proto-core-dev libxdmcp-dev
  libpthread-stubs0-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
socoj2@socoj2-laptop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate


---

### Post by oldos2er on 2009-03-22
Have you updated sources.list recently?
```
sudo apt-get update && sudo apt-get install wine
```

---

### Post by Socoj2 on 2009-03-22
> **oldos2er said:**
> Have you updated sources.list recently?
```
sudo apt-get update && sudo apt-get install wine
```

Well this gave me a different error message...

> socoj2@socoj2-laptop:~$ sudo apt-get update
[sudo] password for socoj2: 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Translation-en_US                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release.gpg
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Sources
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Sources
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages
Reading package lists... Done
socoj2@socoj2-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsm-dev libice-dev libpthread-stubs0 x11proto-kb-dev xtrans-dev
  libxcb-xlib0-dev libxau-dev libxcb1-dev x11proto-core-dev libxdmcp-dev
  libpthread-stubs0-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
socoj2@socoj2-laptop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate


---

### Post by oldos2er on 2009-03-22
You need to remove those Feisty repositories. Run
```
gksu gedit /etc/apt/sources.list
```
and add a comment mark # at the beginning of each Feisty repo.

 Wine is in the universe repository, so after you're done editing sources.list, double-check Software Sources and rerun
```
sudo apt-get update && sudo apt-get install wine
```

---

### Post by Socoj2 on 2009-03-23
> **oldos2er said:**
> You need to remove those Feisty repositories. Run
```
gksu gedit /etc/apt/sources.list
```
and add a comment mark # at the beginning of each Feisty repo.

 Wine is in the universe repository, so after you're done editing sources.list, double-check Software Sources and rerun
```
sudo apt-get update && sudo apt-get install wine
```


> socoj2@socoj2-laptop:~$ sudo apt-get update
[sudo] password for socoj2: 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Sources
Reading package lists... Done
socoj2@socoj2-laptop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate


still no joy.

---

### Post by hyper_ch on 2009-03-23
use my generator in the sig to recreate your sources list. You might also want to add the repos for Wine HQ directly.

---

### Post by Socoj2 on 2009-03-23
> **hyper_ch said:**
> use my generator in the sig to recreate your sources list. You might also want to add the repos for Wine HQ directly.

done and it still says "package wine has no installation candidate.

---

### Post by hyper_ch on 2009-03-23
post the full output.

---

