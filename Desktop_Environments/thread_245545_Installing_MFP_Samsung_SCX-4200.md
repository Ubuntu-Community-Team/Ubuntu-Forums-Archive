---
title: "Installing MFP Samsung SCX-4200"
date: 2006-08-28
forum: Desktop Environments
---

### Post by shyster. on 2006-08-28
Hey all,

I just recently acquired a Samsung SCX-4200 and currently in the process of installing it in Ubuntu. 

I have followed these instructions but for SCX-4200 instead and with updated Linux drivers provided by Samsung.
[http://www.elijahlofgren.com/linux/ubuntu/#scx-4100]("http:///www.elijahlofgren.com/linux/ubuntu/#scx-4100")

The big problem is when I try running the install script:
```
sudo ./cdroot/Linux/install.sh
```
And I get this message:
```
./cdroot/Linux/install.sh: 1230: source: not found
ERROR: HARDWARE_PLATFORM undefined, execution aborted
```
Can anyone point me in the right direction? Thanks! :D

---

### Post by orb9220 on 2006-08-28
is the cdrom disc mounted when you issue the command? Might try replacing  the ./cdroot/ with./hdc/

He might mean whatever your cdrom root drive is.

Just a thought

---

### Post by mulvila on 2006-09-12
I am thinking about bying the same piece, but would not do it before I learn about a succesfull installation experience. Any progress with yours?

Marko

---

### Post by mixandgo on 2006-10-03
I am having problems installing this printer ! does anyone have it working ?

---

### Post by shyster. on 2006-10-14
Hello to all,

I *finally* got this bloody thing to work. Samsung really messed up the drivers for this one. Finding out how to fix it involved a lot of this ](*,) 

On your original cd install, run all the install scripts including:
[LIST=1]
[*]Linux/models/scx4200/drivers.sh
[*]Linux/models/scx4200/scx4200install.sh
[*]Linux/install.sh
[*]Linux/rd/mfpcommon.sh
[/LIST]
Make sure it is done in this order or the Samsung application will not install. 

Next, follow the instructions given here (edited for scx-4200, and copy the files from your installation cd, or the new driver package to the given locations. This part was copied from [URL="http://blog.clustrix.com/?p=5"]http://blog.clustrix.com/?p=5
[/URL]

___________________________

First, go to the Samsung website and download the latest driver pack. The filename should resemble 20051130084614343_DriversPack-1.0.165.tar.gz. Do not run any of the installers. If you use KDE or GNOME, it will try to execute autorun for you. Do not give in. Exit anything that might pop up.

From this monstrous driver pack, weighing in at 16MB, you only need 7 small files. First, extract the following two files from cdroot/Linux/models/scx4200/scx4200.ss. Despite the unfortunate name, it’s really a plain tar file.

    * /usr/share/cups/model/samsung/scx4200.ppd.gz (gzip this yourself)
    * /usr/lib/sane/libsane-samsung_scx4200.so.1.0.1

Next, you want to grab the following files from cdroot/rd/mfpcommon.ss:

    * /usr/lib/cups/backend/mfp
    * /usr/lib/cups/filter/rastertosamsungspl
    * /usr/lib/libmfp.so.1.0.1
    * /usr/lib/libmfpdetect.so.1.0.1
    * /usr/lib/libqt-mt.samsung-mfp.so.3.0.4 (appears as libqt-mt.so.3.0.4 in the tarball)
    * /usr/lib/libGDI.so.1.0.0

Don’t forget to run ldconfig to rebuild the cache. Now you should be able to configure your printer in CUPS. You probably want the scanner to work as well. So add the following entry to /etc/sane.d/dll.conf:samsung_scx4100. You will get an error message from sane telling you that it cannot load some mfp kernel module. Ignore it. You do not actually need that kernel module. Oh, and one more thing, you will need to tweak your SELinux settings (or, if you’re like me, disable it altogether).

___________________________

Now to configure the scanner. The following was shamefully stolen from [http://www.elijahlofgren.com/ubuntu/ ]("http://www.elijahlofgren.com/ubuntu/")

___________________________

First, add the following 2 lines near end of /etc/udev/rules.d/45-libsane.rules (use sudo with your favourite text editor)
```

# Samsung|SCX-4100
SYSFS{idVendor}=="04e8", SYSFS{idProduct}=="3413", MODE="664", GROUP="scanner"
```

Be sure to put it before 
```
LABEL="libsane_rules_end"
```

All this does is make sure that the permissions for the device file is correct and setting its group to scanner. The device is identified by the vendor id and product id. So all users in group scanner will now have access to the scanning functions.

Add the following 2 lines to the end of /etc/udev/rules.d/60-symlinks.rules (use sudo with your favourite text editor)

```
# Create symlink for usb printer to /dev/usb/lp*
BUS=="usb", KERNEL=="lp[0-9]*",         SYMLINK+="usb/%k"
```

You don't have to restart just execute:
```
sudo /etc/init.d/udev restart
```

This will restart udev.
___________________________

Scanning should work now, but printing still has to be configured at this point.

Extract the PPD from /usr/share/cups/model/samsung/scx4100.ppd.gz to your Desktop. Then, go to[ http://localhost:631/]("http://localhost:631/") (cups) and install the printer under Administraion (it should have detected your printer by now), and for drivers, browse to the ppd you just extracted to your desktop.

You can then find your SCX-4200 under System->Administration->Printing, and set it to your default.

Hope this helps! And hopefully Samsung fixes their drivers soon.I'm sure there's an easier method but for now, this is what I did, and I have full scanning and printing functionality to this otherwise great all-in-one.

---

### Post by krolyk on 2006-11-28
> **shyster. said:**
> 
On your original cd install, run all the install scripts including:
[LIST=1]
[*]Linux/models/scx4200/drivers.sh
[*]Linux/models/scx4200/scx4200install.sh
[*]Linux/install.sh
[*]Linux/rd/mfpcommon.sh
[/LIST]
Make sure it is done in this order or the Samsung application will not install. 


Hello 2 all,
i'm an beginner ubuntu user, and also have problems with installing this mfp, tell me please how could i run those scripts from the original CD. ](*,) 
Thanks

---

### Post by MarcoPau on 2007-02-04
Shyster I did the whole thing, just not sure about the output of install.sh (install.sh: 11: source: not found -- [: 670: ==: unexpected operator). Anyway I went on and the printer eventually showed up in the cups page (as local raw printer).
The only thing is that the device URL is set to file:/dev/null, and obviously it will complain that the printer is not connected, as soon as I try printing a page.
I also tried to set some /dev/usb/lp0-1 or /dev/ulpt0-1, or putting usb: instead of file: (it says that raw printers can't use file: devices...). No changes.
If I try adding a new printer, then, I won't get any matching device in the devices list: there's no usb entry or something similar that later will ask for the ppd file.
What am I supposed to do?
Thanks for helping.

---

### Post by MarcoPau on 2007-02-04
I launched usbview and it apparently correctly sees the printer (it's written in red, means anything?).
Under the details it says "device: usblp", "alternate number: 0". So I tried to use /dev/usblp0 as a device both in cups and in the kde printing utility, still obtaining absolutely nothing.

---

### Post by MarcoPau on 2007-02-04
Latest news: I did this

sudo apt-get install libstdc++2.10-glibc2.2
sudo apt-get install libsane-dev sane sane-utils

according to an Italian page I found with google and now the printer is correctly seen in cups, with all its device and ppd.
But I get this error now: "/usr/lib/cups/filter/rastertosamsungspl failed", which I copied from the drivers to the wanted directory. Still error.
Any hint?

---

### Post by MarcoPau on 2007-02-04
Tried launching that raster, output error says it can't find libGDI.so.1.
I did strace and it seems to seek it in many directories, among which there's actually that libGDI.so.1. Can't understand...

---

### Post by MarcoPau on 2007-02-04
Done!!! Incredible...
I did ldd ./rastertosamsungspl and that told me what libs it couldn't find, so I copied the missing ones from the drivers tree to /usr/lib (no symlinks accepted).
Restarted cupsys and here is the test page!
Can't believe the mess.
Hope these posts can help someone else.
Ciao!

PS: we'll see with the scanner... :-D

---

### Post by MarcoPau on 2007-02-04
sane-find-scanner finds it, but if I start xsane it won't be detected...

---

### Post by bronson on 2007-02-06
I posted an updated procedure here: 

[http://news.u32.net/articles/2007/02/05/the-samsung-unified-linux-driver-installer-on-ubuntu](http://news.u32.net/articles/2007/02/05/the-samsung-unified-linux-driver-installer-on-ubuntu)

Alas, it's still somewhat painful...

---

### Post by Marcelo Fernández on 2007-02-20
I've installed this Samsung MFP in Ubuntu 6.10 for AMD64, on an Nvidia nForce 4 Ultra Chipset (Asus A8N-E) Motherboard and it seems the Samsung's 2.2.90 "Unified Driver" installer works ok once you change the simbolic link /bin/sh from "/bin/dash" to "/bin/bash".

After that, printing works ok. But I have a LOT of troubles to make the scanner working. After some hours trying everything I could make it work... The problem was the error message "I/O Error when scanning" when trying to scan something from xsane, even as root user. Besides, "scanimage -L" worked fine, and "sane-find-scanner" too. 

But when I tried to (even preview) something... I got that "I/O error". Looking at the syslog (/var/log/syslog) when running xsane, I was getting something like this:

Feb 21 00:00:43 localhost rmmod: ERROR: Module mfpportprobe does not exist in /proc/modules 
Feb 21 00:00:43 localhost rmmod: ERROR: Module mfpport does not exist in /proc/modules 
Feb 21 00:00:43 localhost rmmod: ERROR: Module ppdev does not exist in /proc/modules 
Feb 21 00:00:43 localhost kernel: [  226.781867] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRIST
ATE,COMPAT,ECP,DMA]
Feb 21 00:00:43 localhost kernel: [  226.849499] lp0: using parport0 (interrupt-driven).
Feb 21 00:00:43 localhost rmmod: ERROR: Module ppdev does not exist in /proc/modules 
Feb 21 00:00:43 localhost kernel: [  226.930894] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRIST
ATE,COMPAT,ECP,DMA]
Feb 21 00:00:44 localhost kernel: [  227.019155] lp0: using parport0 (interrupt-driven).
Feb 21 00:00:57 localhost kernel: [  234.294029] drivers/usb/class/usblp.c: usblp0: nonzero read/write bulk status received: -71
Feb 21 00:00:57 localhost kernel: [  234.325509] drivers/usb/class/usblp.c: usblp0: error -71 reading from printer
Feb 21 00:00:57 localhost kernel: [  234.325796] drivers/usb/class/usblp.c: usblp0: nonzero read/write bulk status received: -71
Feb 21 00:00:57 localhost kernel: [  234.385447] drivers/usb/class/usblp.c: usblp0: error -71 reading from printer
Feb 21 00:00:57 localhost kernel: [  234.385518] drivers/usb/class/usblp.c: usblp0: nonzero read/write bulk status received: -71
Feb 21 00:00:57 localhost kernel: [  234.443150] drivers/usb/class/usblp.c: usblp0: error -71 reading from printer

The rmmod's are "fine", it seems like the mfp library is doing it's (dirty?) work. But the "nonzero read/write bulk status received: -71" and the "error -71 reading from printer" were important... I did a Google search... and in a lost post[1] said "try to talk to the device with USB 1.1, disabling USB 2.0".

I did a 'sudo rmmod ehci_hcd' and now the scanner works perfectly. It seems the USB 2.0 kernel module (2.6.17-11-generic from Edgy) can't communicate with the device very well when scanning. To print, unloading the ehci_hcd module isn't needed.

I hope this help the next one. :) 

(Anyway the device works beautifully)
Regards
Marcelo
[1]: [http://www.ussg.iu.edu/hypermail/linux/kernel/0402.3/1488.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0402.3/1488.html)

---

### Post by zvezdafolk on 2007-03-09
> **MarcoPau said:**
> sane-find-scanner finds it, but if I start xsane it won't be detected...

Did you finaly manage to make it work ?

I got the printer working but not the scanner:

> $ scanimage -L
insmod: can't read '/lib/modules/2.6.17-11-386/kernel/drivers/mfpportctrl/mfpport.ko': No such file or directory
Erreur de segmentation (core dumped)

> $ sane-find-scanner
(...)
found USB scanner (vendor=0x04e8 [Samsung], product=0x341b [SCX-4200 Series]) at libusb:002:002
(...)

any idea ?

---

### Post by zvezdafolk on 2007-03-13
I finaly succed to make it work.

I got this error :
> # scanimage -L

insmod: can't read '/lib/modules/2.6.17-11-386/kernel/drivers/mfpportctrl/mfpport.ko': No such file or directory

*** glibc detected *** scanimage: double free or corruption (!prev): 0x080546b8 ***

So I get in synaptic an uninstall something looking like glibc! I tried again and became in the same case as [http://jacobo.tarrio.org/Samsung_SCX-4200_on_Debian]("http://jacobo.tarrio.org/Samsung_SCX-4200_on_Debian")
... and then the problem was solved!

---

### Post by minghai on 2007-04-19
Hi,

    Following the instructions in [http://jacobo.tarrio.org/Samsung_SCX-4200_on_Debian](http://jacobo.tarrio.org/Samsung_SCX-4200_on_Debian), I got the scanner to work.  When I type ¨xsane" on a command prompt, xsane comes up and I can scan fine.  However, when I try to run Applications -> Graphics -> Xsane Image Scanner, it says ¨no devices available¨.  I tried re-installing xsane but still no luck.  Any ideas?  Thank you.

Ming Hai

---

### Post by shyster. on 2007-04-20
Hey all,

Sorry for not replying to the other posts- I've been very busy over the past few months. However, I have found a much better method in getting the printer AND scanner working. Using this method is not very confusing and should be easy for Ubuntu newbies. Let's get on shall we? :D

1. Download the Samsung Unified Driver File [here ]("http://org.downloadcenter.samsung.com/downloadfile/ContentsFile.aspx?CDSite=SS&CttFileID=828690&CDCttType=DR&ModelType=N&ModelName=SCX-4200&VPath=DR/200704/20070406190711687_UnifiedLinuxDriver.tar.gz") and extract it to your home folder. 

2. Using terminal, navigate to the Linux folder within the extracted folder and right-click on the "install.sh" file to change the permissions so that the file may be writable. At the top it should state 
```
#! /bin/sh
# {

### Common procedures
```

Change this to:
```
#! /bin/bash
# {

### Common procedures
```

Then, navigate to the folder and run it in a terminal with root privileges. ```
sudo bash cdroot/Linux/install.sh
```

3. The installer should start. Let it run until you get to the point where it tells you to add a new printer. For some reason the required driver is not installed during the process, and therefore not eligible for selection, so just cancel/quit the installation. A Samsung Unified Driver Configurator icon should appear on your desktop by now.

4. To install the driver for the printer, we go to the CUPS server at [URL="http://localhost:631/"]localhost:631
[/URL]. Next we click Administration at the top row of tabs. Under "New Printers Found", you should have two entries mentioning the Samsung printer. I chose to add the printer for USB_1, so do so. It should now ask you for the driver, which is located at /home/ed/Desktop/cdroot/Linux/noarch/at_opt/share/ppd/scx4200.ppd . After this, it should work and you can print out a test page.

5. As for the scanner, I have no idea how or why it worked, but when I first entered the XSane Image Scanner Program, there was no devices found. The second time I opened XSane the scanner was detected. Because I have no idea why this occurred, this may not work, however hopefully it does. 

Well, hope this works far better than my first set of confusing instructions. 

Cheers!

---

### Post by minghai on 2007-04-23
Hi all,

     Just thought I share with everyone how I got the 4200 working in my office.

To get the printer working, I used the instructions from this website:
[http://news.u32.net/articles/2007/02/05/the-samsung-unified-linux-driver-installer-on-ubuntu](http://news.u32.net/articles/2007/02/05/the-samsung-unified-linux-driver-installer-on-ubuntu)
====================================================================

Download the latest driver from Samsung's site. Use the latest driver for the SCX-4200 (20070406190711687_UnifiedLinuxDriver.tar.gz version 2.00.93) 

Problem 1: Non-Posix Installer Scripts
If you try to run the installer now, you immediately get errors:

$ ./cdroot/autorun 
./Linux/install.sh: 1232: source: not found
ERROR: HARDWARE_PLATFORM undefined, execution aborted

This is because Samsung uses non-Posix extensions in their shell scripts yet they specify /bin/sh, the Posix interpreter, to run them.

Most distributions use Gnu Bash to provide /bin/sh. This way everything just works, extensions and all. The problem is, Bash has become quite large and slow. It's good for interactive use, bad for fully automated use. Ubuntu still uses Bash for interactive use but, as of Edgy's release, has started using Dash for automated scripts. Dash is a big part of the reason why Edgy boots so much faster than Dapper, but it's also why any script executed by /bin/sh must be careful follow the Posix standard.

The fix is easy: just change every /bin/sh to explicitly use /bin/bash instead (see the patch). Here's how to do this:

   $ tar zxf 20070406190711687_UnifiedLinuxDriver.tar.gz
   $ cd cdroot
   $ sudo apt-get install patch
   $ wget -O- [http://news.u32.net/files/samsung.patch](http://news.u32.net/files/samsung.patch) | patch -p1
   $ sudo ./autorun

And now the install should complete without a hitch.

Problem 2: PPD Location
OK, the drivers are installed. When you go to configure your new printer, however, find Samsung's drivers will be missing. That's because their PPDs were installed into /usr/share/cups/model/samsung but Cups now looks for PPDs in /usr/share/ppd. This is easy enough to fix. Just run:

    $ sudo ln -s /usr/share/cups/model/samsung /usr/share/ppd/samsung
    $ sudo /etc/init.d/cupsys restart

Now the "SCX-4200 Series" driver should show up and you'll be able to finish configuring your printer.

Problem 3: Flawed mfp Utility
OK, the printer is configured but, when you try to print, Samsung's mfp executable will bail out with "E [05/Feb/2007:20:45:57 -0800] PID 12485 (/usr/lib/cups/backend/mfp) stopped with status 2!" (in /var/log/cups/error_log).

A convenient solution, however, is to just change the printer's port to be explicitly USB. That way MFP won't error out when it fails to install its kernel module.

So, when setting up this printer, don't use the default "Samsung SCX-4200 Series" device. Instead, click on "Use another printer," then select "Samsung SCX-4200 Series USB #1". 

To get the scanner working, I used instructions from this site:
[http://jacobo.tarrio.org/Samsung_SCX-4200_on_Debian](http://jacobo.tarrio.org/Samsung_SCX-4200_on_Debian)
====================================================

Download these files for the driver:

    * [http://jacobo.tarrio.org/files/soft/scx/fix-nopar-scx4200-2.00.92-2007011301.tar.gz](http://jacobo.tarrio.org/files/soft/scx/fix-nopar-scx4200-2.00.92-2007011301.tar.gz)

# md5sum fix-nopar-scx4200-2.00.92-2007011301.tar.gz
2007072b63c987722dcb8afb580e7521  fix-nopar-scx4200-2.00.92-2007011301.tar.gz

Then, run this:

# tar xvfz fix-nopar-scx4200-2.00.92-2007011301.tar.gz
# cd fix-nopar

There are two versions of the fixed files: the "i386" one is for 32-bit x86 machines; the "x86_64" one is for 64-bit x86 machines. I recommend that you run the "check.sh" script to make sure you know which one you have to install:

# ./check.sh
The 32-bit library has been found at /usr/lib
You may replace it with the one in the "i386" directory

In this example, the script found the 32-bit version, so you would use the fix in the "i386" directory. You might also have both versions installed at the same time; in that case, you only have to follow the instructions for both versions.

After you enter each directory, you'll find some useful information in the README and differences.txt files. Read them as to be informed about what's going on.

I recommend checking the MD5 sums against those that appear in the README file, and aborting the procedure if they don't match:

# md5sum libmfp.so.1.0.1
6bb0691e05b5c8861b3439c5d4f5d536  libmfp.so.1.0.1
# md5sum /usr/lib/libmfp.so.1.0.1
cbf458742dd4ec98ea4516bcc9d2a86d  /usr/lib/libmfp.so.1.0.1

They match, so now you can make a backup of the original, unmodified file, and copy the fixed file over it:

# cp /usr/lib/libmfp.so.1.0.1 /usr/lib/oldlibmfp.so.1.0.1
# cp libmfp.so.1.0.1 /usr/lib

Now check that you can run "scanimage -L" as a normal user:

$ scanimage -L
insmod: can't read '/lib/modules/2.6.16-1-686/kernel/drivers/mfpportctrl/mfpport.ko': No such file or directory
device `smfp:SAMSUNG SCX-4200 Series on USB:0' is a SAMSUNG SCX-4200 Series on USB:0 Flatbed Scanner

If it doesn't work yet, try this:

# adduser YOUR_USER_NAME lp

Substitute your user name for YOUR_USER_NAME. And then, as a normal user:

$ newgrp lp

    Re-login for newgrp command to take effect on all shells.

$ scanimage -L
insmod: can't read '/lib/modules/2.6.16-1-686/kernel/drivers/mfpportctrl/mfpport.ko': No such file or directory
device `smfp:SAMSUNG SCX-4200 Series on USB:0' is a SAMSUNG SCX-4200 Series on USB:0 Flatbed Scanner

Now try xsane. If it complains for being ran as root, just reinstall it. It should work.  

If the fix doesn't work, you can undo it with:

# mv /usr/lib/oldlibmfp.so.1.0.1 /usr/lib/libmfp.so.1.0.1

---

### Post by Busta999 on 2007-04-23
I just guess I was one of the lucky ones.

I have installed the SCX-4200 Linux driver software from Samsung twice on newly installed Ubuntu 6.06 with no problems at all, except I had to run the install script as root, so it ran from the command line rather than a GUI.

I dl'd the latest Linux install software from [http://www.samsung.com/uk/support/productsupport/download/FileView.aspx?cttfileid=828690&type=Print+Solutions&typecode=&subtype=Multi+Function+Products&subtypecode=&cmssubtypecode=&model=SCX-4200&filetype=DR&language=&LSSI=/uk/module/ssi/left/lmenu_printsolutions_multifunctionproducts.sec&RSSI=/uk/module/ssi/right/rmenu_printsolutions.sec]("http://www.samsung.com/uk/support/productsupport/download/FileView.aspx?cttfileid=828690&type=Print+Solutions&typecode=&subtype=Multi+Function+Products&subtypecode=&cmssubtypecode=&model=SCX-4200&filetype=DR&language=&LSSI=/uk/module/ssi/left/lmenu_printsolutions_multifunctionproducts.sec&RSSI=/uk/module/ssi/right/rmenu_printsolutions.sec")

As I said went in really easy first time, scanner, printing etc all work fine

M

---

### Post by billy boy on 2007-04-26
Thanks for that link Busta 999. I downloaded the driver and installed it as per the instructions on the website. Printing and scanning seem to be working fine. I recommend wannabe SCX 4200 users try the straightforward route first - I think Samsung have updated the drivers very recently. 

However, I did get the following message in terminal when I executed the install:

william@william-laptop:~$ sudo cdroot/autorun
libstdc++ v3 (gcc 2.96) not found, install ... done
libtiff.so.3 not found, install ... done
./i386/share/guiinstall.bin: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory
****  It seems Qt library is not installed, or X display is not accessible.
****  Custom Qt library will be configured for use with this package. 

Being a newbie, I'm not sure what it means and whether it's significant....(as I say, things seem to be working okay) 

Bill

---

### Post by bruno666 on 2007-07-13
A french user reported a serious security problem with the latest version of [Samsung unified drivers]("http://www.samsung.com/ch/support/productsupport/download/FileView.aspx?cttfileid=264040&type=Drucker&typecode=300500&subtype=Farblaserdrucker&subtypecode=300503&cmssubtypecode=&model=CLP-510&filetype=DR&language=")

You can read the full thread [here]("http://linuxfr.org/forums/15/22562.html"). Sorry it's in french, but you can see the dirty code in the comments. After installing the drivers, he notice that some applications (ooffice and xsane) are now executed with root privileges and the /etc folder is now owned by the user !

You can also read [this thread]("http://ubuntuforums.org/showthread.php?t=500702") wich shows the ugly code in the driver installer.

---

### Post by warpuck on 2007-11-18
I had to login as root

extract samsung download

run ./install.sh

after finish

search for cups in menu
or type [http://localhost631/](http://localhost631/)  in browser url

select administration

check:  show printers
            Share published
            Allow users
            save debugging

and change settings

select Manage Printers

select Allowed users
pick allow these users to print

type in names of users dont forget  user root example:   gopher, warpuck, root
if you have a home LAN your windows and/or Mac user should be able to use your linux box as a print server, after drivers are installed

I have not set windows or mac desktops for network printing for 2 years, so I cant direct you any further.

[email]warpuck@comcast.net[/email] or [email]warren.puckett@va.gov[/email]

---

### Post by sylvaticus on 2007-12-26
That's my experience with the Samsung SCX-4200, latest downloaded drivers (SCX-4200 Unified Linux Driver ver.2.00.97 - 20070720152943906_UnifiedLinuxDriver.tar.gz - Updated : 2007/11/22) and Ubuntu 7.10:

The Samsung installer works - e.g. install the missing stl g++ library automatically - but it doesn't works the special port that Samsung create (/dev/mfp4).

The good point is that it is enough to delete the printer created with the Samsung configurator, reboot the pc and the printer, and when they are up again add the printer using CUPS ([http://www.localhost:631](http://www.localhost:631)) instead of the Samsung configurator.

When asked the connection device, specify "Samsung SCX-4200 Series USB #1 (Samsung SCX-4200 Series)" instead of "MFP USB Port #0 (SCX-4200 Series)", and wualà.. the printer works perfectly ;-))) (the scanner as well)

---

### Post by sylvaticus on 2007-12-26
> **warpuck said:**
> I had to login as root

extract samsung download

run ./install.sh

after finish

search for cups in menu
or type [http://localhost631/](http://localhost631/)  in browser url

select administration

check:  show printers
            Share published
            Allow users
            save debugging

and change settings

select Manage Printers

select Allowed users
pick allow these users to print

type in names of users dont forget  user root example:   gopher, warpuck, root
if you have a home LAN your windows and/or Mac user should be able to use your linux box as a print server, after drivers are installed

I have not set windows or mac desktops for network printing for 2 years, so I cant direct you any further.

[email]warpuck@comcast.net[/email] or [email]warren.puckett@va.gov[/email]

I don't think there is any need to go on the "allow users" tab.. by default all users can .. use it.
All default options has worked good for me, and by the way, CUPS is reached using [http://localhost:631](http://localhost:631) with the two dots before the port number...
):P

---

### Post by ElPato on 2008-03-09
Semi related post.

I plugged in a Sansa C250 to my Ubuntu 6.06 box for charging and forgot about it.  

About a week later, I went to print something.  Printing broke / stopped working on my Epson R320 printer in a very wierd way.  I would get a partial page, then nothing.

This message would show up in the syslog:
localhost kernel: [17266063.636000] drivers/usb/class/usblp.c: usblp0: nonzero read/write bulk status received: -71

Unplugging the Sansa and rebooting the computer cured the problem.  Hopefully someone will find this useful.

---

### Post by tayroni on 2008-04-22
Samsung SCX-4200 scanner does not work on Ubuntu 8.04 Hardy Heron
Summary: I have installed the samsung unified driver in gutsy and on hardy. The scanner works on gutsy but NOT on HARDY.

Description: I've installed the driver first using the script provided by samsung, and manually. The manual installation was done because that the script allows /etc read and write by users (I really want to know the name of the programmer who did this mess!)

In both ways: installation by script or manually, the driver for the printer and scanner works on a clean install of gutsy. The same don't happen for hardy: the printer works but the scanner is not recognized by xsane.

Output of sane-find-scanner (both Gutsy and Hardy). Using sudo scanimage -L, the scanner is found on gutsy, but not on hardy.
__________________________________________________ __________________________________________________ __________________________________________________ _
found USB scanner (vendor=0x04e8 [Samsung], product=0x341b [SCX-4200 Series]) at libusb:002:003
__________________________________________________ __________________________________________________ __________________________________________________ _


On GUTSY (sudo xsane and sudo scanimage -L WORKS), the relevant lines of /var/log/syslog are
__________________________________________________ __________________________________________________ __________________________________________________ _
Apr 21 19:14:25 galileu rmmod: ERROR: Module ppdev does not exist in /proc/modules
Apr 21 19:14:25 galileu kernel: [ 1263.159257] pnp: Device 00:0b disabled.
Apr 21 19:14:25 galileu kernel: [ 1263.246583] pnp: Device 00:0b activated.
Apr 21 19:14:25 galileu kernel: [ 1263.246596] parport_pc 00:0b: reported by Plug and Play ACPI
Apr 21 19:14:25 galileu kernel: [ 1263.246662] parport0: PC-style at 0x378 (0x77, irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Apr 21 19:14:25 galileu kernel: [ 1263.352916] lp0: using parport0 (interrupt-driven).
Apr 21 19:14:25 galileu kernel: [ 1263.394944] pnp: Device 00:0b disabled.
Apr 21 19:14:25 galileu rmmod: ERROR: Module ppdev does not exist in /proc/modules
Apr 21 19:14:25 galileu kernel: [ 1263.450626] pnp: Device 00:0b activated.
Apr 21 19:14:25 galileu kernel: [ 1263.450638] parport_pc 00:0b: reported by Plug and Play ACPI
Apr 21 19:14:25 galileu kernel: [ 1263.450702] parport0: PC-style at 0x378 (0x77, irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Apr 21 19:14:25 galileu kernel: [ 1263.564420] lp0: using parport0 (interrupt-driven).
__________________________________________________ __________________________________________________ __________________________________________________ _


On HARDY (sudo xsane DOESN'T WORK and sudo scanimage -L don't find the scanner) the relevant lines of /var/log/syslog are
__________________________________________________ __________________________________________________ __________________________________________________ _
Apr 21 19:11:46 kepler kernel: [ 1166.177485] lp: driver loaded but no devices found
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.236853] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_888').
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.253490] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_956').
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.257871] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_888').
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.275009] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_632').
Apr 21 19:11:46 kepler rmmod: ERROR: Module ppdev does not exist in /proc/modules
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.282338] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_956').
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.287454] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_632').
Apr 21 19:11:46 kepler kernel: [ 1166.453319] lp: driver loaded but no devices found
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.511863] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_956').
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.516347] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_956').
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.562628] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_888').
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.567925] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_888').
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.589722] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_632').
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.594256] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_632').
Apr 21 19:17:01 kepler /USR/SBIN/CRON[7696]: (root) CMD ( cd / && run-parts --report /etc/cron.hourly)
__________________________________________________ __________________________________________________ __________________________________________________ _


So, please, help me to figure out what's happening with the samsung scx-4200 scanner on hardy. Any help is welcome.


PS: To install the driver manually (best way), only for reference:

1) Download 20070720152943906_UnifiedLinuxDriver.tar.gz from samsung, extract the files, go to new directory cdroot and type these commands
cp Linux/noarch/at_root/etc/sane.d/smfp.conf /etc/sane.d/
cp -r Linux/noarch/at_opt/share/ppd/* /usr/share/ppd/custom/
cp Linux/i386/at_root/usr/lib/libmfp.so.1.0.1 /usr/lib/
cp Linux/i386/at_root/usr/lib/sane/libsane-smfp.so.1.0.1 /usr/lib/sane/
cp Linux/i386/at_root/usr/lib/cups/backend/mfp /usr/lib/cups/backend/
cp Linux/i386/at_root/usr/lib/cups/filter/* /usr/lib/cups/filter/
cd /usr/lib
ln -s libmfp.so.1.0.1 libmfp.so.1
ln -s libmfp.so.1.0.1 libmfp.so
cd sane
ln -s libsane-smfp.so.1.0.1 libsane-smfp.so.1
ln -s libsane-smfp.so.1.0.1 libsane-smfp.so

2) Edit /etc/sane.d/dll.conf and add the line "smfp" to the end of file. Add yourself to the groups lp and scanner.

3) Reboot

---

### Post by tayroni on 2008-04-24
I DID IT!!!!! The SAMSUNG SCX-4200 now works on HARDY HERON!!!!!!

The problem was the driver software by SAMSUNG looks for the usb device on

/proc/bus/usb/00*/00*

and 8.04 drops support to /proc/bus/usb/00*/00* and port all software to look only on /dev/bus/usb/00*/00*

To reenable support on /proc/bus/usb I edited

/etc/init.d/mountdevsubfs.sh

and modify the lines

#
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb

to

#
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

and reboot.

ONE CAVEAT: Using patched /usr/lib/libmfp.so.1.0.1 from [http://jacobo.tarrio.org/Samsung_SCX-4200_on_Debian](http://jacobo.tarrio.org/Samsung_SCX-4200_on_Debian) allows me to use xsane with normal user.

---

### Post by nejode on 2008-04-27
tayroni:
Would you happen to know the way to install "only" the printer driver?

My problem is that in my office, the scx-4200 in conected to a Win2003 server.  I installed the unified driver and through CUPS had it printing beutifully via samba.  But the problem comes when I try to scan with my locally installed HP-4180... neither xsane nor kooka work!... I unistall the samsung driver and both scanning apps work great, but I can't print to the remote scx-4200 :confused:

Or maybe one of the samsung laser printer drivers that come with Hardy (or CUPS) can work for that machine?  That way maybe it won't mess up sane.

... any ideas???... help appreciated.

---

### Post by tayroni on 2008-04-27
@nejode: You can try this to *disable* the scanner part of scx-4200: open /etc/sane.d/dll.conf and change the line

smfp

to

#smfp

But should there is an alternative way (that I don't know how) to use *both* scanners.

---

### Post by nejode on 2008-04-28
tayroni: 

...well, got this machine printing at last!!!  What I did was follow your post # 27, in the part about installing manually the driver, but by-passing any command that had "sane" in it.  That way only the printer driver y ppd files were installed and there are no conflicts with my local scanner!  Thanks for that guide, without it I would still be in the dark.

---

### Post by ajf44 on 2008-04-29
Hey,

Is anyone else having problems printing from Envice? Printing from every other application (tried open office, firefox, Adobe Acrobat reader, and GEdit) works fine. When I print from Envice, the printing looks enlarged 4-5 times and distorted. I tried printing the same PDF from Adobe Acrobat Reader and it works fine, so its not the PDF.

Thanks if you have found a work-around!

---

### Post by nik1979 on 2008-05-19
> **ajf44 said:**
> Hey,

Is anyone else having problems printing from Envice? Printing from every other application (tried open office, firefox, Adobe Acrobat reader, and GEdit) works fine. When I print from Envice, the printing looks enlarged 4-5 times and distorted. I tried printing the same PDF from Adobe Acrobat Reader and it works fine, so its not the PDF.

Thanks if you have found a work-around!


I have the same problem.

---

### Post by jackbox on 2008-07-05
How do you edit the LPD of the printer so the Jacobo Terrio fix works? I cannot figure out how to change the LPD to /dev/usb/lp0 as instructed for his modified libmfp.so.1.0.1 file to work. Now applications cannot find any scanner instead of the segmentation. The printer still works but I can only scan with the original libmfp.so.1.0.1 file and when running XSANE as SUDO.

---

### Post by helpme0k on 2008-07-06
Can someone help me? I'm a total noob to linux. I'm trying it out for the first time. 

I'm following the advice from post 27. I downloaded this exact file from samsung:

I go to the cdroot in terminal and typed:
cp Linux/noarch/at_root/etc/sane.d/smfp.conf /etc/sane.d/

The error I got was this:
cp: missing destination file opperand after 'Linux... (then exactly repeated the location i typed. 

:(

---

