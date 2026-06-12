---
title: "Simple Scan Failed to Scan: Unable to connect to Scanner"
date: 2015-01-02
forum: Desktop Environments
---

### Post by daniele-p891 on 2015-01-02
Hello everyone.

I have an old desktop PC (motherboard: Microstar model MS 6330) on which I am running Ubuntu  10.04.1 Desktop 32 bit.
Yesterday I plugged in an old scanner (Agfa Snapscan e20) to the usb port. When I tried to run Simple Scan it gave me this:

[IMG]http://s21.postimg.org/lcewvh28n/Simplescan01.png[/IMG]

then I looked for that question over the internet, finding this thread: [http://ubuntuforums.org/showthread.php?t=1758404](http://ubuntuforums.org/showthread.php?t=1758404);
after searching for an hidden config folder "/.xsane" in the home directory (as suggested by Irony) , without finding anything I proceeded step by step with this guide: [http://www.flagar.com/en/risorse/linux_inspiron_mandrake8.1#scanner_agfa_snapscan_e20](http://www.flagar.com/en/risorse/linux_inspiron_mandrake8.1#scanner_agfa_snapscan_e20) , linked by tredegar but nothing changed.

Still that window appears everytime I open Simplescan. This is what I get when I run sane-find-scanner from Terminal: 

```
 # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x06bd [AGFA ], product=0x2091 [SNAPSCAN]) at libusb:002:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.


```

I hope somebody would care to help. Thanks in advance.

---

### Post by sammiev on 2015-01-02
10.04 has reach EOL ( End of Life ). You no longer can update the software. You can try 12.04 which is good for another 2+ years. 

You can also try [Linux Puppy]("http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm") which uses very little resources.

---

### Post by daniele-p891 on 2015-01-02
Dear sammiev, thanks for your prompt answer;
I hope I'm not digressing too much saying the following: I already tried to upgrade my system to the 12.04, but right after the  "ubuntu booting screen my display went  off and then this message appeared:"**Sync out of range**".
the videocard is an **Ati Rage 128 pro 32 MB**;
the screen I'm using is a **Samsung SyncMaster 750s**.

I've been told to set this: **radeon.nomodeset=1** in the **boot option** but I didn't quite figure out where and when should I actually type that in.

Thanks again.

---

### Post by Bucky Ball on 2015-01-02
Welcome. How far did you get with the 12.04 install? You're saying you got it installed by on first boot you got that error message or you got that error message when you tried to boot the install media? You are trying to install from install media or doing an 'in place' upgrade via the Software Updater (don't remember what that was called in 10.04 LTS).

Please see [here]("http://ubuntuforums.org/showthread.php?t=2229730") re. forum recommendations for EOL releases. [This]("https://help.ubuntu.com/community/EOLUpgrades") may also be handy. ;)

Personally, I would download and install 14.04 LTS, supported until April 2019. LTS releases now receive five years support (non-LTS release get nine months). I notice you are using the 32bit version. You have a 32bit machine? If 64bit, use that version of the Ubuntu ISO. Also, if lower spec or older machine, you might be better with Xubuntu or Lubuntu which are less resource hungry.

PS: Not digressing. We would be pleased to help with your new install as generally not a lot we can do with an unsupported release. I can change the name of the thread to reflect that and move the thread to the appropriate forum section if that is the way you want to go.

---

### Post by daniele-p891 on 2015-01-03
Thanks for your answer Bucky Ball and your willingness to help;
well it is a 32 bit machine from 1999 with 1 GB RAM and 850 MHz CPU (motherboard: Microstar model MS 6330).
I tried to install 12.04 from a Live CD but before the process it showed me that error message: "Sync out of range"; hence I installed 10.04 smoothly and ran the in-place 12.04 upgrade from the Update Manager: it **seemed** to work (I followed **each** step of the process i.e. setting time-zone, detecting keyboard) but every time I booted, after the Ubuntu loading screen that error message reappeared.

Thank you again

---

### Post by Bucky Ball on 2015-01-03
From [HERE]("https://help.ubuntu.com/community/Installation/SystemRequirements"):

> Ubuntu Desktop 11.04 and up uses Unity as the default GUI while the previous releases used GNOME Panel by default. In order to run Unity the system needs a more capable graphics adapter &#8211; see more here or below:

* 1000 &#924;Hz processor (about Intel Celeron or better)
* 1024 MiB RAM (system memory)
* 3D Acceleration Capable Videocard with at least 256 MB

_From experience, we all know that it is recommended to have 2048 MiB RAM to properly run a day to day Ubuntu._
A good start should be with minimum 1024 and recommended 2048 MiB RAM. 

The underlining is mine. You may not get a very satisfactory experience with 12.04 and 1Gb of RAM, particularly with multiple programs open or LOTS of Firefox tabs, but at least you almost have it running so you'll find out when we've cracked the current nut. 

Having said that, I think one of your issues could be that 12.04 LTS (and beyond) uses the more resource hungry Unity desktop environment and perhaps it's not the graphics card causing the blank screen. Or perhaps it's a combination of the graphics and Unity. I'm still thinking Xubuntu might be a better option, but regardless, perhaps try the command you found previously. When you are at the grub menu after boot:

1/ Choose the kernel you want to boot;
2/ Press 'e' to edit it;
3/ Find the kernel line that ends with 'quiet splash' or any combination of those words;
4/ At the end of that line, after 'quiet splash', add 'radeon.nomodeset=1'.

So the end of the line should look like:

```
quiet splash radeon.nomodeset=1
```

From memory it is ctl+x to save the changes and 'b' to boot. Check with the instructions at the bottom of that screen. Let us know if that has any effect and if not we can dig deeper.

---

### Post by daniele-p891 on 2015-01-04
Hello and thank you again Bucky Ball;
Today I put into practice what you explained to me: I upgraded the OS from 10.04 to 12.04 via the Update Manager, booted, pressed 'e' after selecting the kernel and saw this on my screen as expected:

[IMG]http://s24.postimg.org/ln75a5pat/WP_20150104_001.jpg[/IMG]

I placed that string of code after the **initrd /boot/initrd.img&#8230;**, pressed F10 to boot the system but once again, after that, the screen went off and that "sync out of range" showed up.

I tried several times, placing that string right after **quiet splash** and after **$vt_handoff** but I always got that error message. 
I did not see how to save the edited kernel code by the way, but placing it before **$vt_hand&#8230;** gave me different results (errors) so I knew something was changing.

Thanks again for your help.

---

### Post by daniele-p891 on 2015-01-13
Hello again,
12.04 did is hungry for resources, so, to cut a long story short, here's what I did:

[LIST=1]
[*]I downloaded the x and the l ubuntu *flavors*' .ISOs; 
[*]I followed the guide at [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows) and made a xubuntu bootable USB; 
[*]I went to [Elmar Hanlhofer's website]("http://www.plop.at/en/bootmanager/download.html"), downloaded and loaded Plop Boot Manager 5.0.14 on a floppy disk; 
[*]I booted from the floppy disk (changing BIOS settings), only tried xubuntu and, seeing that still the system was too slow I repeated step 2 with lubuntu and installed it. 
[/LIST]


Now, I **could not** find a solution for the "Sync Out of range" message. It appears to be a problem related to the video-card's driver, but since my **[AMD/ATI] Rage 128 PRO** doesn't seem to be included into the *Catalyst* driver's suitable cards' list, looks like I can only use the OpenSource driver featured in the OS.
Hence I opened Synaptic and tried to re-install the xserver-xorg-video-r128 package:

[IMG]http://s15.postimg.org/5yfy0s1pn/2015_01_13_175633_1024x768_scrot.png[/IMG]

after re-booting the system nothing changed: I have been and am still using the workaround suggested by [**alejandro.mc**]("http://ubuntuforums.org/member.php?u=326940") in this thread: [http://ubuntuforums.org/showthread.php?t=1243094](http://ubuntuforums.org/showthread.php?t=1243094) > Once the "Sync. Out of Range" sign comes up (the monitor is down and you  see nothing but the sign moving around the screen) you have to start  trying to find the frequency by typing:

CRLT + ALT + "+"

and

CRLT + ALT + "-"

Do it slowly, press it once, see if anything changes, press the same  combination again, see if anything happens, press it again...

Somehow the third or fourth time you change it (by pressing those key  combinations) the sign will disappear and image will come up. 

which allows the display to work eventually, though in a glitchy way.

Regarding the scanner, same error, different operating system:

[IMG]http://s8.postimg.org/82me44ew5/2015_01_13_175722_1024x768_scrot.png[/IMG]

Still the scanner **is** correctly recognized but cannot operate.

Any help or useful suggestion will be much appreciated.:) Thanks in advance

---

### Post by oldrocker99 on 2015-01-13
Are there drivers for this scanner? You did look to install them, right?

---

### Post by daniele-p891 on 2015-02-20
Hello everyone;
I eventually got my scanner to work properly after re-installing its driver on my Windows XP partition.
(on WinXP) Since I could not load the ScanWise's setup program from the CD, I deleted the scanner device on Control Panel>System>Device manager, unplugged the scanner, rebooted on Windows XP, plugged it back in with the Scanwise CD loaded and followed each step of the installation wizard.
I think it'll possibly be fine 'till I don't power my scanner off though...
Still that "Sync. out of range" error message appears every time I boot my LUbuntu. Any ideas?
Thanks everyone for your time and willingness

---

