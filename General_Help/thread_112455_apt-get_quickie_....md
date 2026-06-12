---
title: "apt-get quickie ..."
date: 2006-01-04
forum: General Help
---

### Post by wannabelinuxconvert on 2006-01-04
Hi,

I'm trying to configure my wireless USB dongle (*without much look so far* :( ) and following a guide I found
[http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=438&highlight=wusb54gv4]("http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=438&highlight=wusb54gv4")

I have to run the command 

**'sudo apt-get install build-essential linux-headers-$(uname -r)'**

But I don't have access to the internet (*hence me trying to get my wireless working*) and I read somewhere that if apt-get detects no internet connection it'll ask for the installation CD ... so I guess my question is, **will the above command work properly using the CD instead of the internet **!?

Cheers

Mic

---

### Post by Obituaryfreak on 2006-01-04
Hi
Before that you must let the APT know about the CD ROM existance ,
to make sure type the following:#vi etc/apt/sources.list
try not to delete any line
make sure that you have the lines starting with :deb cdrom:[Ubuntu ......
if they exist,just try to add a # in front of the other internet sources try not to remove them cause after getting internet connectivity they will be usefull for you,remember that there must about a couple of lines starting with the :deb cdrom:[ ..... , and non of them must be marked with #
but if they already exist(I mean deb cdrom is not marked ) just type 
#apt-cdrom add after inserting the cd 
and then you would have your cd rom added to your sourcelist and after enetering the #sudo apt-get install .....(the module of the usb driver) then it would be able to load the module into the kernel and make you wire less USB functioning.
After making the wireless USB working just unmark the internet sources within the etc/apt/sourcs.list to make your system able to check the packages from the web.
:twisted: 
Freak

---

