---
title: "New iPod nano not supported under Ubuntu?"
date: 2006-09-17
forum: Desktop Environments
---

### Post by Flecko on 2006-09-17
Hey all,

I just got back from the store with a new iPod nano for my wife(the pink one if you must know) and it doesn't appear that Ubuntu supports it. I myself have an iPod video and it works fine when I plug it in. Its recognized and gets a desktop icon, and banshee launches to put music on it. When I plug my wifes nano in...nothing...nada. No icon, no banshee, no nothing. When I launch banshee manually, it doesn't find it.

Here is my dmesg output for those in the know:

```
[17912233.988000] usb 2-8: configuration #1 chosen from 2 choices
[17912233.988000] scsi9 : SCSI emulation for USB Mass Storage devices
[17912233.988000] usb-storage: device found at 11
[17912233.988000] usb-storage: waiting for device to settle before scanning
[17912238.992000]   Vendor: Apple     Model: iPod              Rev: 1.62
[17912238.992000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17912238.992000] SCSI device sdb: 1982464 2048-byte hdwr sectors (4060 MB)
[17912238.996000] sdb: Write Protect is off
[17912238.996000] sdb: Mode Sense: 68 00 00 08
[17912238.996000] sdb: assuming drive cache: write through
[17912239.000000] SCSI device sdb: 1982464 2048-byte hdwr sectors (4060 MB)
[17912239.000000] sdb: Write Protect is off
[17912239.000000] sdb: Mode Sense: 68 00 00 08
[17912239.000000] sdb: assuming drive cache: write through
[17912239.000000]  sdb: sdb1 sdb2
[17912239.004000] sd 9:0:0:0: Attached scsi removable disk sdb
[17912239.004000] sd 9:0:0:0: Attached scsi generic sg1 type 0
[17912239.004000] usb-storage: device scan complete
```

Any ideas? Anyone else have a new iPod nano and have this problem?

Thanks in advance everyone!
-Flecko

---

### Post by baldy1324 on 2006-09-17
maybe it needs a new version of the libipod-sharp that banshee uses. since ubuntu keeps the same version of packages for 6 months this might be the case. so in about 2 months or something edgy will come out with all the newest packages fresh from debain sid/unstable. if you're too anxious you can download the edgy 3 alpha iso off ubuntu's website.

---

### Post by christhemonkey on 2006-09-17
Try mounting it manually and see what happens:
```
sudo mkdir /media/ipodshuffle
sudo mount -t vfat /dev/sdb2 /ipodshuffle
```

---

### Post by cmost on 2006-09-17
This may be a dumb question, but did you first initialize the iPod on a Windows machine?  I've found iPods formatted with Apple's HFS filesystem to be a bit flaky in Linux.  Just a suggestion.

---

### Post by Flecko on 2006-09-17
Heh. I'm a linux-only user. I hadn't initialized it. My brother got me my ipod video as a gift...so he probably did that on his XP computer first.

I'll see if I can't find a windows computer to do it on and then use it under Ubuntu. I'm glad to see its not a problem with Ubuntu.

Thanks everyone!
-Flecko

---

### Post by Flecko on 2006-09-17
I changed my mind. The iPod nano isn't automounting, even after I've 'initialized it' on an XP computer. I've tried resetting its settings through iTunes and all that...no luck.

If I manually mount the thing, I can see whats on it and eventually get gtkpod to talk to it....but what gives? My wife uses ubuntu as well, but I can't expect her to manually mount it and diddle with it everytime she wants to put some more tunes on.

UPDATE: And banshee won't even see the nano after I mount it...only gtkpod..and it doesn't seem to like it very much. This is a 2nd Generation iPod nano.

Any ideas?
Thanks all!
-Flecko

---

### Post by DougInKY on 2006-09-17
I dont have any ideas for you but just wanted to thank you for posting your problems. My birthday is in three weeks and I was going to ask for one of the new Nano's. Probably won't go that route now.

Thanks.

---

### Post by SimonJW on 2006-09-18
The problem is that with the new iPods, Apple changed the way that certain files are stored on the hard drive. Because this is a proprietary, closed-source product, they of course didn't tell anyone and so Linux support for these new ipods is broken. I read about this a few weeks ago on planet.gnome.org, it is to do with a file that Apple removed from the iPod_Control folder that is used by Linux to tell which version of the iPod is present. 

For now, you can manually mount your iPod, and then it should work as usual. As far as I know, this will continue to affect users of the new Video and Nano iPods, as well as users of the older 5G Video iPods with the new firmware installed. I'm sure a fix will be uploaded to the repos soon.

---

### Post by _asc_ on 2006-09-18
Hello!

As SimonJW said, the problem is that Apple removed a configuration file that Banshee uses:

[http://abock.org/2006/09/14/we-need-you-and-apple-sucks-part-2/](http://abock.org/2006/09/14/we-need-you-and-apple-sucks-part-2/)

---

### Post by SimonJW on 2006-09-19
Thanks, **_asc_**, for finding that link. I was looking for ages, but couldn't get it anywhere. I bow to your google-ing skills! :)

The good news is it looks like an update is potentially on the way, as I just read this post on planet.gnome.org :

[http://www.snorp.net/log/2006/09/18/maybe-theyre-not-as-bad-as-i-thought/](http://www.snorp.net/log/2006/09/18/maybe-theyre-not-as-bad-as-i-thought/)

---

### Post by JeffBlouin on 2006-09-23
Hi,

     Same problem here with the new nano 8gb... anyone found i way to make it work ?


I saw that Banshee is working on something.. What about Amarok?

Thanks

---

### Post by Raffo on 2006-10-05
Same problem with my Nano 2G, I'm now mounting it manually, but I'm really waiting for a fast fix...

---

### Post by stonemu2001 on 2006-10-06
hi, I am a new Ubuntu user. I've just get me a nano ipod, I wonder if anyone can show me how to manually mount my ipod. Thanks

---

### Post by gosh on 2006-10-06
> **stonemu2001 said:**
> hi, I am a new Ubuntu user. I've just get me a nano ipod, I wonder if anyone can show me how to manually mount my ipod. Thanks

sudo mkdir /media/ipod
sudo mount -t vfat /dev/sdb2 /ipod

---

### Post by deeptingler on 2006-10-20
I have had the same prob since buying my new silver nano 2g around a month ago - its been one of the more frustrating things to try and use with kubuntu - I have to dmesg each time and manually mount grrr :twisted:

---

### Post by test on 2006-10-22
It seems that if you reformat your 2G nano to mac (hfs+) then ubuntu 6.10RC works perfectly, and I presume 6.06.  Of course, then you loose the ability to write.

---

### Post by MiniJames on 2006-11-12
I have just bought the black 8gb second generation iPod Nano.

I updated it with iTunes 7 and enabled the manual management / disk options. I then proceeded to plug the iPod into my laptop running Ubuntu Edgy.

The device is listed correcly by **dmesg | tail -n 20**

```
james@kami:~$ dmesg | tail -n 20 
[17183687.128000] usb 4-3: configuration #1 chosen from 2 choices
[17183687.128000] scsi1 : SCSI emulation for USB Mass Storage devices
[17183687.132000] usb-storage: device found at 3
[17183687.132000] usb-storage: waiting for device to settle before scanning
[17183692.132000] usb-storage: device scan complete
[17183692.132000]   Vendor: Apple     Model: iPod              Rev: 1.62
[17183692.132000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17183692.136000] SCSI device sda: 3964928 2048-byte hdwr sectors (8120 MB)
[17183692.140000] sda: Write Protect is off
[17183692.140000] sda: Mode Sense: 68 00 00 08
[17183692.140000] sda: assuming drive cache: write through
[17183692.140000] SCSI device sda: 3964928 2048-byte hdwr sectors (8120 MB)
[17183692.140000] sda: Write Protect is off
[17183692.140000] sda: Mode Sense: 68 00 00 08
[17183692.140000] sda: assuming drive cache: write through
[17183692.140000]  sda: sda1 sda2
[17183692.144000] sd 1:0:0:0: Attached scsi removable disk sda
[17183692.144000] sd 1:0:0:0: Attached scsi generic sg0 type 0
```

The command...

[B]sudo mkdir /media/ipod
sudo mount -t vfat /dev/sdb2 /ipod[/B]

...doesn't work:

```
james@kami:~$ sudo mkdir /media/ipod
Password:
james@kami:~$ sudo mount -t vfat /dev/sdb2 /ipod
mount: mount point /ipod does not exist
james@kami:~$ sudo mount -t vfat /dev/sdb2 /media/ipod
mount: special device /dev/sdb2 does not exist
james@kami:~$ 
```

Because the iPod wont mount, gtkPod cannot do anything with the device.

Please advise :) -- I am sure that I'm doing something stupid :KS

---

### Post by MiniJames on 2006-11-12
**UPDATE**

The following manual commands worked for me :)

[B]sudo mkdir /media/ipod
sudo mount -t vfat /dev/sda2 /media/ipod[/B]

I've compiled ([COLOR="DarkOrange"]with lots of help from jdong on #ubuntuforums[/COLOR]) gtkpod version V0.99.8 and I'm hoping that its going to work a charm!

---

### Post by MiniJames on 2006-11-12
Does anyone know how to safely remove the new iPod? Eg. the equivelant of right clicking on a flash disk desktop icon and clicking "Eject". After running: **sudo umount /media/ipod** the iPod screen still reads "*Do not dissconnect*"

Your thoughts please ;p

---

### Post by MiniJames on 2006-11-12
I figured it out!

```
james@kami:~$ sudo eject /dev/sda2
Password:
james@kami:~$
```
[U]
I feel like a complete tool now [/U];p

The whole manual process works like a charm, the songs copied up to my iPod perfectly and **I am listening to my banging music** as I type this.

**[COLOR="Red"]I love linux ;p[/COLOR]**

---

### Post by SlCKB0Y on 2006-11-13
my second gen ipod nano works fine with ubuntu.

It has never even been plugged into a windows computer.

---

### Post by deeptingler on 2006-11-13
check this thread which was a great help to me...

[http://www.ubuntuforums.org/showthread.php?t=268550&highlight=ipod+nano+2g](http://www.ubuntuforums.org/showthread.php?t=268550&highlight=ipod+nano+2g)

---

### Post by Kingfield on 2006-11-28
> **SlCKB0Y said:**
> my second gen ipod nano works fine with ubuntu.

It has never even been plugged into a windows computer.

so long as you never update the firmware

---

