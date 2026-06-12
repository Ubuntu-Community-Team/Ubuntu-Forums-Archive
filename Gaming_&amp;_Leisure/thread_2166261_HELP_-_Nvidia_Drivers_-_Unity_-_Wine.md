---
title: "HELP - Nvidia Drivers - Unity - Wine"
date: 2013-08-08
forum: Gaming &amp; Leisure
---

### Post by phosphorus2 on 2013-08-08
[COLOR=#333333][FONT=lucida grande]Hi

I need to run wine. 

On ubuntu 13.04, when I install the nvidia drivers [/FONT][/COLOR][COLOR=#333333][FONT=lucida grande]unity disappears[/FONT][/COLOR][COLOR=#333333][FONT=lucida grande]. After I run some compiz command on the terminal I got -> "glxqueryextensionsstring is null for screen 0", " error plugin opengl not loaded", etc. 
On 64 bit version that problem doesn't seem to happen but it looks like wine only works on 32 bit versions? 
[/FONT][/COLOR]
I formatted the HDD several times for clean install, used also 13.10, 64 bits versions... I tried several commands to fix this, install headers-generic, remove nvidia-current, purge "something", etc. Also if I install the OS with download 3rd party updates I get an internal error.

[COLOR=#333333][FONT=lucida grande]Anyone knows how to solve the issue? Or maybe tell me a distro I can use that doesn't give me this problems...[/FONT][/COLOR]

---

### Post by phosphorus2 on 2013-08-09
Been doing this-> [http://ubuntuforums.org/showthread.php?t=1743535&page=28&p=10909540#post10909540](http://ubuntuforums.org/showthread.php?t=1743535&page=28&p=10909540#post10909540) 

It works to remove and unity loads, but when I installed the drivers it got into black screen again.

The commands of Step 2 don't work too neither did most of those here -> [http://ubuntuforums.org/showthread.php?t=1743535&page=80&p=11467050#post11467050](http://ubuntuforums.org/showthread.php?t=1743535&page=80&p=11467050#post11467050)

---

### Post by phosphorus2 on 2013-08-09
[http://www.linlap.com/asus_k53sc](http://www.linlap.com/asus_k53sc) -> my laptop...

---

### Post by mirearts KING SUNNY on 2013-08-10
You need to purge nouveau drivers first, and make sure you have your kernel generic binaries to compile the nvidia drivers (Search in forum or google how to do)...I suggest you proceeding to a MANUAL installtion as follows which worked for me.

Go to nvidia.com and download .run package drivers for Linux and paste in /home and select properties and tick 'allow run...'

Open software center and remove all nouveau drivers. After removal, open terminal and type '**sudo update-initramfs -u**' and **sudo reboot**.

Now choose ubuntu recovery from GRUB and select failsafe session...when your screen seems to load your login screen, press Alt+F1 or F2 then type:
cd dir and note the nvidia-Linux-x86..... file which is the driver 
now type : **sudo sh NVIDIA-Linux-x86...**(exactly as you see it on your screen) and hit enter
now follow instructions, choose yes and no appropriately!
after it is over, type: **sudo nvidia-xconfig** and **sudo update-initramfs -u**
now reboot by **sudo reboot**

---

### Post by mirearts KING SUNNY on 2013-08-10
[B]USE THIS ONE INSTEAD,,VERY SIMPLE!!!
[/B]
Another much simple way is to press Alt+F2 as soon as your monitor turns black. Login and type:

**sudo add-apt-repository ppa:xorg-edgers/ppa**
[B]
sudo apt-get update[/B]

**sudo apt-get install nvidia-current**

That's all, and reboot after download and setup finishes...

---

### Post by MikeCyber on 2013-08-12
Personally I only install kernel sources. Than on vt2 stop x and run the nvidia installer.

---

### Post by Yellow Pasque on 2013-08-12
The k53sc looks like an Optimus/hybrid graphics laptop. If the following command shows an Intel and nvidia GPU, remove the nvidia driver, reboot, make sure Unity is working properly, and then you can install bumblebee: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

```
lspci | grep VGA
```

---

### Post by DarkAmbient on 2013-08-12
Bought a dual-gpu laptop the other day, took a while before I realised that and that I needed bumblebee to use the dedicated GPU. You never stop to learn. :-)

First, In terminal, remove nvidia completely:
```
sudo apt-get remove --purge nvidia-*
```
Then reboot.

_In case Unity won't show up:_
```
sudo apt-get install compizconfig-settings-manager && ccsm
```
[U]Click on Ubuntu Unity Plugin, then activate it and everything it requires. You also need to enable Desktop Wall, Move Window, Place Window, Scale Window, Animations, Windows Frame to get the normal Unity behaviour back.
You may need to reboot, or you could try type unity the the terminal afterwards.[/U]


Once you got Unity back. Run this to add 2 req. repos and install bumblebee, primus and latest nvidia-drivers.
```
sudo add-apt-repository ppa:bumblebee/stable && sudo apt-add-repository ppa:xorg-edgers/ppa && sudo apt-get update && sudo apt-get install bumblebee bumblebee-nvidia primus primus-libs-ia32:i386 nvidia-325 nvidia-settings-325 
```

Then open up bumblebee.conf in gedit
```
sudo gedit /etc/bumblebee/bumblebee.conf
```

and change "**Driver**" to "**Driver=nvidia**"
"**KernelDriver**" to "**KernelDriver=nvidia-325**"
"**LibraryPath**" to "**LibraryPath=/usr/lib/nvidia-325:/usr/lib32/nvidia-325**"
"**XorgModulePath**" to "**XorgModulePath=/usr/lib/nvidia-VERSION/xorg,/usr/lib/xorg/modules**"

Reboot, then try if it worked with
```
optirun nvidia-settings -c :8

```
'
You can also compare:
```
glxgears
``` with ```
optirun glxgears
```


If you wanna play steam-games using your dedicated GPU, then in Steam click properties on the installed game then "set launch options" and add **primusrun %command%**


Oh, and if the card still doesn't work, check that the cards BusID match the one in xorg.conf.nvidia.

```
lspci | grep 3D | awk '{ print $1 }'
```

should match the value of BusID "PCI:xx:xx:x in xorg.conf.nvidia.
```
sudo gedit /etc/bumblebee/xorg.conf.nvidia 
```


sources:
[http://www.webupd8.org/2013/04/bumblebee-321-released-with-ubuntu-1304.html](http://www.webupd8.org/2013/04/bumblebee-321-released-with-ubuntu-1304.html)
[https://support.steampowered.com/kb_article.php?ref=6316-GJKC-7437](https://support.steampowered.com/kb_article.php?ref=6316-GJKC-7437)



Please correct me if you see something inaccurate.

---

