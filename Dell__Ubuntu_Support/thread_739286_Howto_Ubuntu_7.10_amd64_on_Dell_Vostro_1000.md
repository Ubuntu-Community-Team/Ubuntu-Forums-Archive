---
title: "Howto: Ubuntu 7.10 amd64 on Dell Vostro 1000"
date: 2008-03-29
forum: Dell  Ubuntu Support
---

### Post by cousinavi on 2008-03-29
**[SIZE="3"]Thanks[/SIZE]**
I have done very little work myself. Almost all of the information in this post comes from other sources. I hereby respectfully acknowledge the real work done by the following individuals/teams:
Ubuntu (what a great release of GNU/Linux), [http://linux.dell.com/wiki/index.php]("http://linux.dell.com/wiki/index.php") (Let no one say that Dell is in bed with MS),
mara9ato, james, klitz, Tyler H

**[SIZE="3"]Dream[/SIZE]**
I have been trying to get Ubuntu 7.10 amd64 working flawlessly on my Dell Vostro 1000. There are a few tricks that I have learned that should help people with similar laptops.
**I have stated commands usig the "nano" text editor, a novice user may prefer a WYSIWYG text editor, I recommend EMACS because I believe it to be THE text editor.**

**[SIZE="3"]Hardware[/SIZE]**
Firstly here is my (relevant) spec:
[LIST]
[*]AMD® Athlon 64 X2 Mobile Technology TK57
[*]ATI Radeon® Xpress 1150 HyperMemory
[*]Dell™ Wireless 1505 Wireless-N Mini-Card - Europe
[/LIST]

**[SIZE="3"]Prerequisites[/SIZE]**
I upgraded the BIOS to the latest version from the [Dell website]("http://support.dell.com"). This was done by running the appropriate executable under the preloaded MS windows XP.

**[SIZE="3"]Installation[/SIZE]**
I downloaded the Live CD version of Ubuntu 7.10 amd64 which I burnt to CD, then booted off this CD. _I loaded the safe graphical version of Ubuntu as the standard version would not load_. I installed Ubuntu using the standard installer which worked without a problem.

**[SIZE="3"]Updates[/SIZE]**
I strongly recommend that the first thing you do after Ubuntu boots for the first time is to install all the latest updates, and then restart without installing or running _anything_.

**[SIZE="3"]Graphics[/SIZE]**
I used the restricted drivers manager and enabled the graphics card driver listed. After a restart the screen resolution and refresh rate were automatically set correctly.

To get the startup and shutdown splash screens working I followed [mara9ato]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=687071")'s advice:
In a console type,
```
sudo nano /etc/usplash.conf
```
Change the line which says,
```
yres=1024
```
to,
```
yres=800
```
Then run the command,
```
sudo update-initramfs -u
```

**[SIZE="3"]Wireless[/SIZE]**
My wired network card worked fine, but my wireless didn't. This is the solution I got working which is based on [Dell]("http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper")'s advice, with a few tweaks due to package changes,

[LIST=1]
[*][SIZE="2"]_Remove clutter from any previous attempts_
If this is your first attempt to get the wireless working skip to step 2
[/SIZE]
Specifically you should get no entries if you type,
```
ndiswrapper -l
```
if there are any entries present remove them by using the command
```
sudo ndiswrapper -r <DRIVER_NAME>
```

[SIZE="2"][*]_Download packages_[/SIZE]
Install ndiswrapper and utilities by running,
```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
```
You will probably be prompted for your Ubuntu CD so make sure you have it handy.

Also you will need to get the windows drivers from [Dell's website]("http://support.dell.com").
Place the executable in a folder on your desktop called "tmp"
Then use the unzip command to unpack the drivers,
```
unzip ~/Desktop/tmp/R123456.EXE   (or whatever the name of the download is)
```

[SIZE="2"][*]_Install drivers_[/SIZE]
I don't know how important this, but there are 3 distinct geographic regions, US, Japan and the rest of the world (ROW). When I did this, I used the drivers located in "~/Desktop/tmp/DRIVERS_ROW", but obviously you should use the drivers for your own location. Also if you downloaded an executable for your specific location the name of the directory may be different. A little care and common sense should be all you need here.
The file you are interested in is called "bcmwl5.inf". Do NOT move this file. Use ndiswrapper to load in the drivers,
```
sudo ndiswrapper -i ~/Desktop/tmp/DRIVER_ROW/bcmwl5.inf
```
**Warning:**
If you use "bcmwl6.inf" you have installed the Windows Vista drivers. These do NOT work!
Make certain you install the Windows XP drivers.

Check this was successful by using the command,r
```
ndiswrapper -l
```
You should get something similar to,
```
bcmwl5 : driver installed
        device (14E4:4318) present
```

Next the ndiswrapper module must be loaded; type,
```
sudo depmod -a
sudo modprobe ndiswrapper
```

You may wish to check,
```
tail /var/log/messages
```
for any error messages. If the last line looks a little scary don't worry I got that too, but the rest of the lines should be fairly positive.  Look out for a line that states what encryption modes are available if you need a particular flavor of WPA then see if it is in the list. For example, I have been unable to get WPA-enterprise encryption working.  

My log read as,
```
ndiswrapper version 1.45 loaded (smp=yes)
ndiswrapper (link_pe_images:577): fixing KI_USER_SHARED_DATA address in the driver
ndiswrapper: driver bcmwl5 (Broadcom,09/20/2007, 4.170.25.12) loaded
ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 18
ndiswrapper: using IRQ 18
 wlan0: ethernet device xx:xx:xx:xx:xx:xx using NDIS driver: bcmwl5, version: 0x4aa190c, NDIS version: 0x501, vendor: '', 14E4:4318.5.conf
wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
 usbcore: registered new interface driver ndiswrapper
ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

[SIZE="2"][*]_Test the card_[/SIZE]
Now Ubuntu's default network manager should work and you should be able to find the wireless networks in range and you should be able to connect to them. If any keys, passwords are required a prompt should ask for the relevant information.
**Warning**
Check you "WIFI light" is on, if it is off then try Fn+F2. If the light is still off then your wireless probably wont work. 
 
[SIZE="2"][*]_Add ndiswrapper to startup routine_[/SIZE]
If you have connected to your wireless network then you have successfully got you card working. All that remains is to add ndiswrapper module to your startup routines.
Append the word "ndiswrapper" to the list in,
```
sudo nano /etc/modules
```
[/LIST]

[SIZE="3"]**Brightness Keys**[/SIZE]
This was solved by james and was first posted [here]("https://bugs.launchpad.net/ubuntu/+bug/159255")

Download the scripts he wrote and place them in a folder on your desktop called "tmp":
[video_brightnessdown.sh]("http://launchpadlibrarian.net/11081245/video_brightnessdown.sh")
[video_brightnessup.sh]("http://launchpadlibrarian.net/11085094/video_brightnessup.sh")
**Warning**
I do not maintain these scripts myself. It is YOUR responsibility to read the scripts to check for nasties, see [Ubuntu's FAQ]("http://ubuntuforums.org/announcement.php?f=48") for help.

Then run,
```
# Back up the original scripts
sudo cp /etc/acpi/video_brightnessup.sh /etc/acpi/video_brightnessup_old.sh
sudo cp /etc/acpi/video_brightnessdown.sh /etc/acpi/video_brightnessdown_old.sh
#
# Copy the scripts you just downloaded into position,
sudo cp ~/Desktop/tmp/video_brightnessdown.sh  /etc/acpi/video_brightnessdown.sh
sudo cp ~/Desktop/tmp/video_brightnessup.sh  /etc/acpi/video_brightnessup.sh
```

Your brightness keys should now work. Again thanks to james for solving that one.

[SIZE="3"]**DVD movie playback**[/SIZE]
Since DVDs require propriety codecs they can be a bit fiddley to get working. This method is based on Kilz's advice from [this thread]("http://ubuntuforums.org/showthread.php?t=470508").
I am a VLC kinda guy so that is what I have installed and found to be working. If you prefer another player change the appropriate lines below,
```
# Download your preferred player
sudo apt-get install vlc
#
# If you are a mozilla/firefox fan why not get the plugin
sudo apt-get install mozilla-plugin-vlc
#
# Download the DVD specific libraries
sudo apt-get install libdvdread3 libxine1-ffmpeg ffmpeg 
```
Now we need to run a script which will build the library, but make certain your C/C++ compilers are up-to-date.
```
# Install the necessary compilers
sudo apt-get install libc6-dev g++ gcc
#
# Run the script that will do the magic
sudo /usr/share/doc/libdvdread3/install-css.sh
```
Watch out for the classic "error 77" barf, as seen below:
```
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output... configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** [build-stamp] Error 77
```
This usually means that your gcc can't link against an important library.

But hopefully you will have no problems and you can now watch your favorite DVDs in your preferred video player.


[SIZE="3"]**TODO**[/SIZE]
Issues I have found which I have yet to fix:
[LIST]
[*]Suspend/resume
Suspend and hybernate will start, but they wont finish. This is a real toughy. Input welcome.
[*]Find a FREE driver for wireless card
[/LIST]



I hope this helps anyone who is having problems with their Vostro 1000.


[SIZE="2"]**-Avi**[/SIZE]

---

### Post by Tyler H on 2008-04-08
Thank you so much for centralizing all of this information. Two things that I did run into that other Vostro users should be aware of is:

1. Dell is shipping multiple wireless cards in their 'default' configurations. Make sure you recognise which one you are using and get the correct drivers. (Also the Vista drivers will NOT work).

2.Before you try to install the drivers, make  you sure Wi-Fi light is on by hitting Fn+F2. I spent hours trying to get the drivers to work before realising this.

---

### Post by cousinavi on 2008-04-08
Wireless on Dell laptops is a real issue. I hope Ubuntu 8.04 is better.

I have tried to keep this guide as concise as possible. The wireless card section is already over 50% of the document. I am reluctant to add too much more.
I have tried to keep the the wireless section card independent. I _hope_ this will work with any Broadcom based wireless card. I believe that the Intel based wireless cards apper in the Restricted Drivers Manager. Therefore they are not mentioned here. If you know this not to be true please PM me.

If anyone is having difficulties with there wireless card on an Dell laptop, PM me and I will offer all the help I can.

**-Avi**

---

### Post by shumifan50 on 2008-04-10
Register thanks for this usefull post.
Confirm works on Vostro 1000 with 1395 minicard and XP drivers.

Failed to apt-get vlc - not found and same for plugin.

Graphics card (ATI radeon exress 1150) sort of works. Couldnt enable "ATI accelerated graphics driver" as it reports xorg-driver-fglrx is not enabled. When I try to enable this diver it reports it is noot supported for amd64.

Thanks agan for the detailed post on wireless.

---

### Post by cousinavi on 2008-04-11
error

---

### Post by cousinavi on 2008-04-11
Hmmm,

I may have mispelt the package I will check. For now I would use your package management software (synaptic) if you want VLC.

Although you should be ablt to get DVD playback working on Totem, I just like to plug VLC :-)

NB
If you are new to VLC DVD playback can be a little troublesome:
when you "open the disc" you will probably have to specify a larger buffer, the default is a bit low and sometimes this can affect the quality of DVD playback.

**-Avi**

---

### Post by DoyleChris on 2008-04-14
I up to the part of the wireless working and i went to reboot into linux to make sure it would and it didnt came up with a error.  I am reinstalling and starting over and see when it happens.

---

### Post by Tyler H on 2008-04-17
How do I check to see if the onboard graphics is utilizing the full 256 mgs of dedicated memory?

---

### Post by Tyler H on 2008-05-08
IT WORKS!

I just made one heck of a discovery.

I did a clean install of Hardy 64 bit yesterday with no luck whatsoever with NDISwrapper and bcmwl5.inf driver. They log kept stating that the bcmwl564.sys file was missing. I had seen this in the Dell .exe download, but had no idea how to load it into NDISwrapper. So I wiped the drive, and did a clean install of Gusty 32bit for that fact that I had got it to work before. However even with following the instructions with this guide (which had worked before) NDISwrapper kept giving me an invalid driver message. In the log I had also noticed missing .sys files during installation. Then a bolt of intelligence hit me. I needed to compile all of the US folders files into a tmp file. PRESTO, it works! Somehow NDISwrapper is searching around in the same directory that the bcmwl5.inf file is located in.

Note that this is with a 1395 so your results may vary.

I've just completed the installation of Hardy64 andthe Dell drivers (which is the exact same the one for Gutsy) and it's working perfectly after blacklisting the bcm43xx and a reboot.

The mod posted above about the brightness control by Cousinavi which was not working for me in Gutsy is now working for me in Hardy!

---

