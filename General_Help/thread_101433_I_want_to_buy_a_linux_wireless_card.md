---
title: "I want to buy a linux wireless card"
date: 2005-12-09
forum: General Help
---

### Post by gatorbrit on 2005-12-09
I have a dell 1450 wireless card - did the whole ndiswrapper routine and got it to work.  BUT now ubuntu crashes all the time.  ALL THE TIME.   What I want to do is buy a wireless card that comes with linux drivers, straight out of the box.  No more ndiswrapper.  Just full linux support.  Plug it in and ubuntu recognizes it. 

Any recommendations?

Many thanks
Rich

---

### Post by aclaunch on 2005-12-09
Any Atheros based card works well OOB. I don't have a specific brand (sorry).

Alan

---

### Post by matthewstory on 2005-12-09
[https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?action=show&redirect=WirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?action=show&redirect=WirelessNetworkCards)

regards,
matt

---

### Post by samir85 on 2005-12-09
Well, it depends what kind of Wlan Card you want to afford (PCI, USB, Cardbus ...).

For the PCI Wlan Cards I recommend the MSI PC54G2 Card, which you buy at the German Amazon for 25 Euros (so American Amazon probably offers this product too). This WLan Card is based on the Ralink RT2500 chipset. Ralink released some open source linux drivers for this chipset and an open source community is optimizing the drivers.
The Wlan Card works out of the box in Ubuntu Breezy (except WPA), if you need  
WPA, you must install a GUI (you can find installation instructions for this on Ubuntu Wiki).


regards Samir ;)

---

### Post by jdong on 2005-12-09
D-Link Wireless G PCI and USB cards work well under Linux, **WITH THE EXCEPTION OF** the 108M **USB** card.

---

### Post by gatorbrit on 2005-12-09
Thanks sooo much for the very quick feedback.   I'm a linux noobie and ubuntu was recommended to me because of the great user forums!  

You mention D Link products- Are you refering to these: (for example)
D-Link AirPlus G DWL-G510 PCI Adapter
see : [http://www.dlink.com/products/?sec=0&pid=308]("http://www.dlink.com/products/?sec=0&pid=308")

Thanks.

Rich

---

### Post by jdong on 2005-12-09
Yes:

D-link DWL-G510 and DWL-G520: Atheros

D-link DWL-G122 (usb 54M): Ralink rt2570 (aka 2500usb)

---

### Post by gatorbrit on 2005-12-09
Thanks so much.:D 

Rich

---

### Post by gatorbrit on 2005-12-09
Found this link - seems to be helpful.  And confirms comments on the D-Link products.

[http://linux-wless.passys.nl/]("http://linux-wless.passys.nl/")

Rich

---

### Post by az on 2005-12-09
[QUOTE=gatorbrit] BUT now ubuntu crashes all the time.  ALL THE TIME.   [/QUOTE]

That usually happens when you are using an older INF file.  The newer ndiswrapper version are built with newer INF files.   Using an older windows driver (like the one provided in the box the card came in) can cause crashing like this.  Is there a more recent version available from the manufacturer?

---

### Post by jdong on 2005-12-09
[QUOTE=gatorbrit]I have a dell 1450 wireless card - did the whole ndiswrapper routine and got it to work. [/QUOTE]

Wait... is that a Broadcom 43xx?

Within the past week, a **native Linux driver has been made for it!**

[http://bcm43xx.berlios.de/](http://bcm43xx.berlios.de/)

---

### Post by MichaelM on 2005-12-09
[QUOTE=jdong]Wait... is that a Broadcom 43xx?

Within the past week, a **native Linux driver has been made for it!**

[http://bcm43xx.berlios.de/](http://bcm43xx.berlios.de/)[/QUOTE]
*WOW*
No more messing with ndiswrapper?? I can't believe it! :D :D :KS

---

### Post by gatorbrit on 2005-12-09
Thats pretty cool if a driver has been written.  So next question: 
1. how do I figure out if this is the driver for it?
2. how do I install the native linux driver?


Thanks again!!!

Rich

---

### Post by MichaelM on 2005-12-09
[QUOTE=gatorbrit]1. how do I figure out if this is the driver for it?[/QUOTE]
Do```
lspci | grep Wireless
```and look for something like BCM4306. (I guess BCM4301 is the one the driver is aiming at, but it shouldn't be too big of a difference.)> 2. how do I install the native linux driver?Good question. I'd like to know the answer to this. I downloaded and extracted a snapshot and, seeing a makefile, tried to make it. But no luck. Anyone?

EDIT: Does it have to be compiled with the kernel, maybe? :confused:
EDIT2: Just found this in one of the source files:```

#if LINUX_VERSION_CODE < KERNEL_VERSION(2, 6, 15)
# error "The bcm43xx driver does not support kernels < 2.6.15"
# error "The driver will _NOT_ compile on your kernel. Please upgrade to the latest 2.6 kernel."
# error "DO NOT COMPLAIN ABOUT BUGS. UPDATE FIRST AND TRY AGAIN."
```Also:```

# error "The bcm43xx driver requires the SoftMAC subsystem."
# error "SEE >>>>>>    http://softmac.sipsolutions.net/    <<<<<<"
```I hadn't noticed, in all the output.

---

### Post by jdong on 2005-12-10
hmm, it may need the new wireless stack....

Unfortunately, that may mean you'll have to compile your own kernel :-/

In that case, why not spend $30 on a better card? ;)

---

### Post by SickTwist on 2005-12-10
The D-Link DWL-G630 (H/W Ver.:C2 F/W Ver.:3.01) has an Atheros chipset and is supported in Breezy. It is part of the linux-restricted-modules package (install the one that matches the kernel you are running).

The Broadcom driver will most likely be included in Dapper but that release is still about 4 months away. You could try compiling the Broadcom driver yourself but you would need to compile a new kernel as well and that could get messy (there may be incompatibilities between the newest kernel and packages in Breezy).

---

### Post by gatorbrit on 2005-12-10
What is a  "linux-restricted-modules package"?

---

### Post by jdong on 2005-12-10
It's installed by default.

Atheros cards have a "closed source" firmware image requirement, so that means the Atheros Linux driver cannot be 100% open source (closed firmware image). Nothing important :)

---

### Post by SickTwist on 2005-12-10
[QUOTE=gatorbrit]What is a  "linux-restricted-modules package"?[/QUOTE]

All the pieces that make up Ubuntu (programs, documentation, artwork, sounds, themes, etc) are part of modules called "packages" that can be installed for removed. Sometimes one package requires others to be present in order for it to work correclty. The additional required packages are called "dependencies". Ubuntu's package manager knows whether dependencies are needed and will suggest them automatically.

There are databases (called "repositories") available on the Internet containing all of the packages that can be installed in Ubuntu. The Ubuntu install CD also functions as a repository. Only some of the packages in the repositories are installed by default but any packages in the repositories can be added or removed after installation.

There are a few ways to install and remove packages in Ubuntu. From the terminal (command line) there is the apt-get command. There are also graphical programs such as Synaptic (System-->Administration-->Synaptic Package Manager) and Gnome-app-install (Applications-->Add Applications).

There are literally thousands of packages available in the repositories that can be installed. Almost none of these even require a reboot after installing!

The linux-restricted-modules packages are packages that contain some of the modules (kind of like plug-ins) for the Linux kernel. Modules allow the kernel to have features (like hardware drivers) added or removed without having to restart the kernel. This is a good thing because restarting the kernel requires the computer to be rebooted. The Atheros driver (called Madwifi) is included in each of the restricted modules packages. 

There are several restricted modules packages but only one needs to be installed. The reason for this is that kernel modules must be used only with the kernel with which they were compiled. In order to prevent users from having to compile their own modules, there are a few different restricted module packages in the repositories (one for each of the kernels provided).

This command installs the restricted modules package for the kernel that is currently running:

sudo apt-get install linux-restricted-modules-$(uname -r)

Well, that wraps up Ubuntu Packages 101. Hopefully I provided more help than confusion. ;)

---

### Post by gatorbrit on 2005-12-10
That helps a whole lot.  I'm learning a lot here - thanks

---

### Post by MichaelM on 2005-12-10
[QUOTE=jdong]hmm, it may need the new wireless stack....

Unfortunately, that may mean you'll have to compile your own kernel :-/

In that case, why not spend $30 on a better card? ;)[/QUOTE]
Actually, compiling my own kernel wouldn't bother me (I'm currently running 2.6.14.3 vanilla :)). But if you (or someone else) could point me to some detailed instructions... Oh, wait. :idea: I would extract to /usr/src/modules and compile it with the kernel, of course. :oops: 

Of course, I still need to have 2.6.15, so I might wait a little for the official release.

---

### Post by jdong on 2005-12-10
You should be able to untar it into any directory, then "sudo make; sudo make install". This is somewhat "standard procedure" for installing modules.

---

### Post by MichaelM on 2005-12-11
[QUOTE=jdong]You should be able to untar it into any directory, then "sudo make; sudo make install". This is somewhat "standard procedure" for installing modules.[/QUOTE]
Oh.
Well, I'll try again. Maybe I forgot the "sudo". :)
Of course, there's still the issue of kernel version. 2.6.15 should be released within a week or two, I think.

Actually, ndiswrapper works pretty well for me. The only bothers are having to compile it again if I want a vanilla kernel, and having to wait ~1 minute during bootup for it to load. :( Would a native driver load faster?

---

### Post by jdong on 2005-12-12
Native drivers should be significantly more stable / cooperative than ndiswrapper emulated ones.

---

### Post by gatorbrit on 2005-12-12
OK, I'm back and I got a D-Link DwL 122 wireless adapter.  But it is not being recognised by ubuntu.  So I even tried ndiswrapper (I had hoped to avoid this) but the terminal hangs when I type "modprobe ndiswrapper".

I am able to install the windows drivers and they and the hardware are found in 
ndiswrapper -l



I thought that the DWL 122 was supported in linux - how do I go about getting Ubuntu to work with it.

Thanks
Rich

---

### Post by jdong on 2005-12-12
Go to rt2x00.serialmonkey.com, download the rt2570 USB nightly snapshot, untar, make, make install.


Dapper will include this driver by default.

---

### Post by gatorbrit on 2005-12-12
I hate to be sort of dumb, but are these the steps I am gonna do?

untar rt2570*****.tar.gz
make rt2570*****
make instal rt2570******

and then reboot?

---

### Post by jdong on 2005-12-12
tar xzvf rt2570*.tar
cd rt2570-*
make
sudo make install

---

### Post by gatorbrit on 2005-12-12
Here is what I did
unpack into the /rt2570****/
cd Modules 
Make

and I get the following error...
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4 command not found
make[1]: Entering directory '/usr/src/linux-headers-2.6.12-9-386'
  CC [M] /home/richard/drivers/rt2570****/Module/rtusb_main.o
/bin/sh: gcc-3.4 command not found
and then much of the same...

I think I am almost there...



rt2570.ko failed to build.

---

### Post by jdong on 2005-12-12
One more step:

```

sudo apt-get install gcc-3.4

```

The kernel is compiled with GCC version 3.4 while the rest of the system is done by GCC 4.0.

---

### Post by gatorbrit on 2005-12-12
I get..

E: Couldn't find package gcc-3.4

In synaptic i have installed gcc 3.3 and gcc 4, but there is no sign of 3.4.

---

### Post by jdong on 2005-12-12
Hmm, please post your /etc/apt/sources.list

---

### Post by gatorbrit on 2005-12-12
[QUOTE=jdong]Hmm, please post your /etc/apt/sources.list[/QUOTE]
I am trying to post the list - but remember that I have no internet access so any sources that are on the web are not accessible to my pc.  I am able to post messages because I have a second (winxp) box in my office.  My linux box has no network connection

---

### Post by gatorbrit on 2005-12-12
Here is the contents od the sources.list file.  I had to copy it a floppy to bring  it to my other machine to post.



deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

---

### Post by gatorbrit on 2005-12-12
Hang on.. I think this tells me what to do...

[http://www.ubuntuforums.org/showthread.php?t=79896&highlight=%22gcc-3.4%3A+command](http://www.ubuntuforums.org/showthread.php?t=79896&highlight=%22gcc-3.4%3A+command)

---

### Post by jdong on 2005-12-12
Your Internet based sources.list is all disabled. We need to turn it on. Replace the file with the following content:

```

#Ubuntu PLF -- Restricted Formats (i.e. w32codecs, opera, etc)
#Remove if you don't have multimedia needs.
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free

#Base repository
deb http://archive.ubuntu.com/ubuntu breezy main restricted universe multiverse

#Bugfix Updates
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse

#Security Updates
deb http://archive.ubuntu.com/ubuntu breezy-security main restricted universe multiverse

#Backports (newer software; officially sanctioned)
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

```

Run a **sudo apt-get update** and you'll be ready to continue...

Else if you currently don't have network access, follow the instructions you dug up.

---

### Post by gatorbrit on 2005-12-12
Thanks that works!!!!!   jdong - your help has been fantastic - I really appreciate it.  Now I can start to explore all the features of linux.  I really felt that internet access was a must have before I invested any more time in the OS.  
Incidently, I am typing this from my ubuntu box now, not my windows machine!!

One last thing, to get the card drivers loaded i typed
sudo insmod rt2570.ko
then I activated the interface in the network settings gui.

is there a way to automate this on start up?

Anyhow, thanks again.

---

### Post by jdong on 2005-12-12
On subsequent reboots, the "hotplug" service should be able to auto-detect it.  If not, go into /etc/modules and add rt2570 to the end of the list.

---

### Post by ldavey on 2005-12-12
hi, i have the same usb card dwl-g122 ... i have followed this instructions and my pc reports gcc 3.4 is already installed ...

when i type the make command all i get is .... 

ldavey@ubuntu:~/Desktop/DOWNLOADS/usb_card_driver/rt2570-1.1.0-b1/Module$ make
bash: make: command not found

why is this :(

i havent used my laptop for a couple months now due to no net and would love to start using it again

thanks

---

### Post by jdong on 2005-12-12
You need to install build-essential also. In addition, I recommend using a nightly snapshot rather than the BETA 1 release; the nightlies are actually more stable.

---

### Post by ldavey on 2005-12-12
thanks alot your a :KS  much appreciated :)

i got a error saying no build directory in /lib/modules/2.6.12-10-386 so i logged in as root and created one .... now im getting this, so i have made a little progress but somthing must be still missing which i need to install ?

ldavey@ubuntu:~/Desktop/DOWNLOADS/usb_card_driver/rt2570-cvs-2005121213/Module$ make
make[1]: Entering directory `/lib/modules/2.6.12-10-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.12-10-386/build'
rt2570.ko failed to build!
make: *** [module] Error 1

sorry to trouble u, i do enjoy learning linux, it brings the fun back into pcs, thanks

---

### Post by jdong on 2005-12-12
You need to install kernel headers:

```

sudo apt-get install linux-headers-`uname -r`

```

Those are backticks, the things to the left of the number 1, same key as ~.

---

### Post by ldavey on 2005-12-12
THANK YOU VERY MUCH :D 

Couldnt have done this without your help... i reinstalled the necessary linux headers using synaptic and it did the trick, posting this using the usb card right now :)

have the same problem as the other guy tho, with the card not being active on boot up, ill try what u told him and see if that works...

Thanks again, hope i can contribute help to this forum sometime !

---

### Post by ldavey on 2005-12-12
i added rt2570 at the end of /etc/modules, didn't work tho.

But i have managed to get it to configure at boot altho it is VERY slow at booting now...

I copied all the files i created with the make command  (ending with .o) into a folder i also made, called rt2570, and pasted that folder into my /lib/modules/2.6.12-10-386/kernel/drivers/net/wireless directory...

All i could think of, as a temp fix ... When i get some more time tomoz ill mess around more, just happy its working :) do u have anymore ideas ?

Anyway time for me to goto bed. 1 25 am here in UK..... u been a great help tonight, respect for u, thanks !

---

### Post by gatorbrit on 2005-12-12
Hey ldavey, the other guy here (actually UK expat) anyhow, I couldn't get the wireless driver to load either - even when I played around with putting it in the modules file.  Its no biggie really as I don't shut the linux box down that often.    Strange thing tho, when I rebooted to windows I sometimes got a keyboard error - i.e. no keyboard found.  Wierd.  I guess my PC was telling me to stick with ubuntu!

The help on this forum is fantastic.

Rich




[QUOTE=ldavey]i added rt2570 at the end of /etc/modules, didn't work tho.

But i have managed to get it to configure at boot altho it is VERY slow at booting now...

I copied all the files i created with the make command  (ending with .o) into a folder i also made, called rt2570, and pasted that folder into my /lib/modules/2.6.12-10-386/kernel/drivers/net/wireless directory...

All i could think of, as a temp fix ... When i get some more time tomoz ill mess around more, just happy its working :) do u have anymore ideas ?

Anyway time for me to goto bed. 1 25 am here in UK..... u been a great help tonight, respect for u, thanks ![/QUOTE]

---

### Post by ldavey on 2005-12-13
i really want to be a expact... lol

i will be going to washington, vancouver for 2 weeks in march, my best mate lives there, be my first steps on american soil, i dream on one day making it for permenant ! (sorry to admin for drifting thread from topic)

---

### Post by jdong on 2005-12-13
You need to make sure rt2570.ko lands inside the right folder. I'm not sure you guys installed it properly. If **modprobe rt2570** gives you an error, the module was not installed.

You should run:
```

cp rt2570.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/

```

After the **make** command.

---

### Post by gatorbrit on 2005-12-13
That makes sense - I tried to put in the "path" to the ko file in the modules file, but that didn't work.  

Thanks again

---

### Post by gatorbrit on 2005-12-13
[QUOTE=ldavey]i really want to be a expact... lol

i will be going to washington, vancouver for 2 weeks in march, my best mate lives there, be my first steps on american soil, i dream on one day making it for permenant ! (sorry to admin for drifting thread from topic)[/QUOTE]
Technically Vancouver is not American soil!!  Of course to us brits they all talk sort of funny over here.  
Have a good trip.  Pack warm clothes!
Rich

---

