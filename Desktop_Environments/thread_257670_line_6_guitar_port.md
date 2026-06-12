---
title: "line 6 guitar port"
date: 2006-09-14
forum: Desktop Environments
---

### Post by greyash99 on 2006-09-14
Will the guitar port work in ubuntu?

---

### Post by greyash99 on 2006-09-14
bump

---

### Post by greyash99 on 2006-09-15
bump

---

### Post by anaconda on 2006-09-15
> **greyash99 said:**
> Will the guitar port work in ubuntu?

Öööö..What is a guitar port?

if you mead souncards line-in port, then yes..

---

### Post by mixmaster87 on 2006-12-12
this is a guitar port [IMG]http://www.guitars101.com/reviewpost/data/26/7262gport-large.jpg[/IMG]
homepage: [http://www.line6.com/guitarport/](http://www.line6.com/guitarport/)
its a device to plug a guitar into your computer with digital amps running on your computer. anyone using it and know how to install/configure etc?

i really want this question answered myself:KS
(i know im bringing up an old thread)

---

### Post by fdimmling on 2006-12-12
I am rather shure that it will not work unless you use VMWare or the like. I'm using a M-Audio Fast Track USB with a guitar and a micro input which work because it is a standard USB audio interface but any software shipped with it does not, because it is windows or Mac software. I have looked in the Wine aplication database but guitarport is not mentioned.
There is a Linux live distribution for musicians called Studio to Go! where you can see what Linux is offering for musicians.

Friedrich

---

### Post by mixmaster87 on 2006-12-12
the guitarport is rather expensive, and its not that long since i got it... so i "must" have it working..:(

---

### Post by fdimmling on 2006-12-12
If you _must_ have it working I would 

1) first install wine then 

2) start the logviewer from system->administration, set it to observe "messages"

3) plug in your guitarport and look what new lines are appearing in log "messages". 

4) Install the software you got with the guitarport

5) Tell the complaints or messages you get

Friedrich

---

### Post by mixmaster87 on 2006-12-12
these came when i inserted the guitar port. ```
Dec 12 22:17:00 prodigy kernel: [17195490.020000] ohci_hcd 0000:00:02.0: wakeup
Dec 12 22:17:00 prodigy kernel: [17195490.404000] usb 1-1: new full speed USB device using ohci_hcd and address 2
```

and i couldnt even read the files on the disk:(

---

### Post by fdimmling on 2006-12-13
> **mixmaster87 said:**
> 
and i couldnt even read the files on the disk:(

Do you mean that the system didnt react any more?

Friedrich

---

### Post by mixmaster87 on 2006-12-13
when i inserted the disk, and opened it, i got an error message telling me that the disk was empty. when i pressed "ok" i came to a cd drive with nothing in it

---

### Post by mixmaster87 on 2006-12-13
update:

i could open up the cd and move the files now, but when i tried to start the setup file, it opened the installer, and on the setup screen that appeared, everything just close down (like i would press cancel on the first menu)

---

### Post by fdimmling on 2006-12-13
> **mixmaster87 said:**
> update:

i could open up the cd and move the files now, but when i tried to start the setup file, it opened the installer, and on the setup screen that appeared, everything just close down (like i would press cancel on the first menu)

It is better to open a terminal window, make 

cd /cdrom

or the like until you see the file Setup.exe by entering 

ls

and then manually start the setup by

wine Setup.exe (You need wine of course from the repos)

However according to my experience such programs packed with hardware more often do not install or work - but lets try it.

Friedrich

---

### Post by mixmaster87 on 2006-12-14
i have tried to install it through wine, from the cd, and from the disk (after copying the disk into the hard drive. when it starts up, the setup screen comes, and then, in windows, there is a window coming up with licence stuff and installation setup and all that, its like its coming up, but before anything is shown in the window that appear, its like i just pressed cancel. so this is what happens:

wine /guitar\port/setup.exe
setup screen appear
installation window appear, no wait, its gone again (happens in a split second, i just see it come and go) and then everything is off.

the whole cd is on 172mb. thanks for atleast trying to help then:D

---

### Post by fdimmling on 2006-12-14
> **mixmaster87 said:**
> wine /guitar\port/setup.exe
setup screen appear
installation window appear, no wait, its gone again (happens in a split second, i just see it come and go) and then everything is off.

the whole cd is on 172mb. thanks for atleast trying to help then:D

I'm afraid there is no way to run the software with wine, you would have to use VMware or the like which run real Windows systems. However you would have to pay for it and you must have a Windows installation CD. 
I am a Linux only user for about 5 years now and I would never buy a peace of hardware before checking the web for reports on how it is supported in Linux. 
As to the guitar I use Korgs Pandora PX4 and PXR4B for practising because it seemed easier for me compared to a compter based solution.

Best wishes

Friedrich

---

### Post by gosh on 2007-01-17
I am trying to run GuitarPort through a VMWare Windows XP session.
Wine doesn't support USB-devices AFAIK.
VMWare does.

I have it installed, but the only problem still is the sound.
It seems that VMWare is not good enough with streaming USB audio or something.

When I know more, I'll drop in again

---

### Post by belovedmonster on 2007-03-04
The lack of Linux support for my Line 6 Tone Port is the reason why I still run Windows. If I didnt have a toneport, or it worked in Linux then I would have ditched windows by now.

---

### Post by bogr@ on 2007-06-18
Rather late bump, but checkout this link at the line6 site:
[http://line6.com/support/thread.jspa?messageID=41055&#41055](http://line6.com/support/thread.jspa?messageID=41055&#41055)
Cheers.

---

### Post by RockTonic3 on 2007-06-22
i feel like i did it right...  but in audacity there is still no option to use my toneport as the recording/playback device...  I'm also clinging to windows only for recording purposes..  i hope i can get this to work!  this was the output when i did make install:

```
christopher@chris-voltaire:~/Desktop/line6usb-0.7.2$ sudo make install
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/christopher/Desktop/line6usb-0.7.2 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
mkdir -p /lib/modules/2.6.20-16-generic/kernel/sound/usb
cp line6usb.ko /lib/modules/2.6.20-16-generic/kernel/sound/usb
mkdir -p /usr/bin
cp *.sh *.pl /usr/bin
/sbin/depmod -a
/sbin/modprobe line6usb
```

Any ideas?  maybe the driver is working and it just isn't recognized by audacity...?  how can i find out if the driver is working?  Thanks.

---

### Post by RockTonic3 on 2007-09-26
Still playing with this thing trying to get it to work...

I tried wine to install gearbox, and all goes well till it says gearbox needs to be installed on windows xp or later and then aborts.  is there a way to set the compatibility mode in wine?  

does wine really not support usb devices?

---

### Post by stevejesus on 2008-01-27
I have been able to use the Guitarport using creox.c.  It's not as good as the guitar port interface, but it works.  Audio streams over USB just fine so long as you have JACK running and a kernel that supports real-time audio.
Also, with JACK, you can just hook the guitar-port up over USB, with having it loop out to your speakers.  Thats a bonus.

About creox.c though...  It sucks.

---

### Post by darkeale on 2008-02-03
stevejesus: please let me know how you did this. have you got guitarport working as the proper soundcard or is it just as an interface?

cheers 

alex

---

