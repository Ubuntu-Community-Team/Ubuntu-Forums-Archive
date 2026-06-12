---
title: "Dell Wireless 1390 WLAN Mini-PCI Card"
date: 2007-08-04
forum: Dell  Ubuntu Support
---

### Post by circuz_phreak on 2007-08-04
Currently using Ubuntu 7.04, it detects my wireless card but doesn't allow my to connect to my wireless network.  I have a hard-wired internet connection.  I've tried implementing the cvm43xx-fwcutter method found in other posts.  However, not even the first step went smoothly.

sudo apt-get install build-essential...went fine until I was prompted to put the cd in and hit enter, would not recognize either cd's i mounted iso's on, (live cd or text installer).

sudo apt-get install bcm43xx-fwcutter...Couldn't find package bcm43xx-fwcutter

I'm not sure how to proceed from here...any ideas??

---

### Post by X-626 on 2007-08-04
I have the same card and I managed to get it working using ndiswrapper.  You will have to go to Dell's website and download the wireless driver for your model.  I used the howto found here: [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

I'm not for sure about the build-essential problem you are having, though.  Although you could go to [http://packages.ubuntu.com](http://packages.ubuntu.com) to download any packages that you are unable to download via apt-get.  After downloaded, you will be able to just double-click on the .deb file to install it.

---

### Post by circuz_phreak on 2007-08-05
Thanks but no go, can´t get anywhere without the packages.  I´ve tried already downloading the packages myself, however some still need the OS cd installed, so when it won´t read it, only some of the files are installed.  I don´t understand how i can do an install, but then it won´t read the contents of my cd.  I can´t even mount the drive when the cd´s inside it, but in windows it reads it fine....strange!  so because of this problem i cannot fix my wireless situation or my video driver situation.  any suggestions?

---

### Post by nick_h on 2007-08-05
If you are having problems with the CD then edit your */etc/apt/sources.list* file and comment out the cdrom: line (near the top).  You may want to take a backup first.

---

### Post by circuz_phreak on 2007-08-05
then how can i go about installing all the proper files without the cd-rom?  Won´t that just bypass the cd-rom and not allow for complete download of the essential build package?

EDIT:  bad news, just tried other cd´s on my dvd burner/cd-rom drive and no luck, which means the drive isn´t being ecognized.  I´ve had no luck mounting it.  I do not want to bypass it, I want to get it mounted and be able to read content.  First time linux user and i´m having nothing but problems, now I have to wait untill I resolve this issue until i can deal with my wireless or video driver situations.  Any ideas?

---

### Post by nick_h on 2007-08-05
Yes, my suggestion would bypass the cdrom and download packages from the internet.

Are you saying that the cdrom did work with Ubuntu but has now stopped working?  Can you test it with Windows to check the hardware?

---

### Post by circuz_phreak on 2007-08-05
Yes it does work fine in windows, but would bypassing it fix the problem, don´t i need it for the essential build packages?  Here&#347; what i get in fstab if it helps.  Why is it so difficult to mount?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=2254cf8c-f4f5-4662-bf8b-f7fcf95443b6 /               ext3    defaults,erro$
# /dev/sda7
UUID=13497107-d3af-45f6-8e64-b7a938c91833 none            swap    sw           $
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by jongkind on 2007-08-06
There is an excellent HOWTO for installing the 1390 WLAN Mini-PCI Card here:

[http://ubuntuforums.org/showthread.php?t=297092&highlight=1390]("http://ubuntuforums.org/showthread.php?t=297092&highlight=1390")

---

### Post by nick_h on 2007-08-06
My fstab line is the same except my cdrom device is /dev/scd0.

Have a look at System->Preferences->Hardware Information - look for the *block.device* line for the cdrom and check that it is /dev/hda

---

### Post by circuz_phreak on 2007-08-06
There's no trace of it on my system, can't go look there for the device because i'm guessing the system doesn't see it at all....don't know what to do.

---

### Post by X-626 on 2007-08-06
More than likely, your CD drive is actually /dev/scd0 (although, there is a chance it isn't).  There is one thing you could try.  You could try using the eject command to open the disc tray.  Try both of these, and if neither work, then I don't know the answer (this is the only way I know how to check):
```
eject /dev/scd0
```If that works, replace /dev/hda in your fstab with /dev/scd0
```
eject /dev/hda
```I'm not sure of your problem if that one ejects.

---

### Post by Sam Liu on 2007-08-07
Well actually I have a computer with this card and looked up "AirForce One 54g Drivers Ubuntu" and got a good tutorial.

Just a little tip.

Dont forget to blacklist the default driver.

---

### Post by nick_h on 2007-08-07
If that fails try:
```
sudo lshw > hw.txt
```
and then edit hw.txt and search for "cdrom".

---

### Post by michael37 on 2007-08-07
> **circuz_phreak said:**
> Currently using Ubuntu 7.04, it detects my wireless card but doesn't allow my to connect to my wireless network.  I have a hard-wired internet connection.  I've tried implementing the cvm43xx-fwcutter method found in other posts.  However, not even the first step went smoothly.

sudo apt-get install build-essential...went fine until I was prompted to put the cd in and hit enter, would not recognize either cd's i mounted iso's on, (live cd or text installer).

sudo apt-get install bcm43xx-fwcutter...Couldn't find package bcm43xx-fwcutter

I'm not sure how to proceed from here...any ideas??

How about this suggestion:

1) enable the universe and multiverse repositories.  The faq is [here](http://www.ubuntux.org/how-to-add-universe-and-multiverse-repository).

2) start System/Administration/Synaptic Package Manager.
Click on Settings/Repositories.

On the first tab, named Ubuntu Software, unclick CDROM.


3) Rerun your 'sudo apt-get' commands.  It should download the packages you need from repositories.

---

