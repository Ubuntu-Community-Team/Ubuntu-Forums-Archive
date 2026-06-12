---
title: "reboot and select proper boot device or insert boot media"
date: 2009-04-20
forum: General Help
---

### Post by darthpenguin on 2009-04-20
HELP!

I have ubuntu installed on a 320GB IDE disk. I turned on the computer today and the HDD is making a terrible clicking sound. Grub will not load. I get an error saying "reboot and select proper boot device or insert boot media in selected boot device and press a key". I guess the hdd is dead or at least the boot sector is. I boot off the live cd and it can't see the drive. gparted says "no device found" and the file browser shows a SCSI device (which is actually the IDE I think) and I can't mount it.

I need access to the drive at least long enough to back up my home folder. I can install ubuntu 8.10 fresh on a new 500GB SATA that I have but I would like to copy the entire OS over so that I don't need to reinstall anything.

any help would be very much appreciated.

---

### Post by kestrel1 on 2009-04-20
From what you are describing, it sounds very much like the internall workings of the drive have failed. I have had some do this to me & they are normally non functional & cannot be retrieved. This is going to sound totally looney, but you may get to the drive for a short time when it is cool. You can try doing this by putting the drive in a sealed bag & sticking it in the freezer for a couple of hours. then reinstall it & boot up & see if you can get access. I would suggest that you boot from the live CD though.
I have had this work a couple of times, when the drive has got too hot & failed. The only other thing could be the controller board, but unless you can get the exact board it won't work & if it is not the board you are stuffed.
Anyway, the freezer trick might help, although it sounds looney.

---

### Post by darthpenguin on 2009-04-20
> **kestrel1 said:**
> From what you are describing, it sounds very much like the internall workings of the drive have failed. I have had some do this to me & they are normally non functional & cannot be retrieved. This is going to sound totally looney, but you may get to the drive for a short time when it is cool. You can try doing this by putting the drive in a sealed bag & sticking it in the freezer for a couple of hours. then reinstall it & boot up & see if you can get access. I would suggest that you boot from the live CD though.
I have had this work a couple of times, when the drive has got too hot & failed. The only other thing could be the controller board, but unless you can get the exact board it won't work & if it is not the board you are stuffed.
Anyway, the freezer trick might help, although it sounds looney.

Hmm. I was afraid of this.

Upon closer inspection I noticed that the hdd was sticky to the touch. It seems I neglected to remove the elastic bands from the power cords when I installed the new power supply a few months ago. I guess they melted and seeped into the hdd. eewww. so this is a hardware issue. I will try to cool it down but I'm afraid the drive is toast. 

What are some other methods of restoring data from a damaged disk? If I could access it could I clone the disk and boot Ubuntu off a clean HDD? is that possible?

thanks.

---

### Post by kestrel1 on 2009-04-20
Yes, if you could access the disk long enough to clone it you would be OK.
I wouldn't think that melted elastic bands would get in to a HDD enclosure. These are very well sealed, but if your system is getting so hot that it melts elastic, you have a real risk of frying the system. It sounds like the drive has got far too hot & failed because of this. try the cooling

---

### Post by theozzlives on 2009-04-20
In my experience (since 1993), what you described sounds like HDI (head disk interference). From my work at "unbutton" at Seagate, it's not pretty... I've seen big grooves dug into the media and all I could think is, that's someone's data.

Your data is prolly lost, but let this be a lesson, as I've preached for 16 years, BACKUP often. You are only guarinteed one thing with a HD and that is one day it WILL fail.

---

### Post by chomptown on 2009-04-20
There is very little chance you actually had something melt *into* your HD.  In the past they used to tell you not to smoke around your computer because the smoke would get into your HD.  This is a complete load of $%!+ as your HD is vacuum sealed.


sorry, that was no help whatsoever, but still funny...;)

---

### Post by darthpenguin on 2009-04-20
> **theozzlives said:**
> In my experience (since 1993), what you described sounds like HDI (head disk interference). From my work at "unbutton" at Seagate, it's not pretty... I've seen big grooves dug into the media and all I could think is, that's someone's data.

Your data is prolly lost, but let this be a lesson, as I've preached for 16 years, BACKUP often. You are only guarinteed one thing with a HD and that is one day it WILL fail.

HDI means that there are scratches on the disks themselves?  is that what you mean? Anyway I know I should have backed up. That is why I have a mac and a Time Capsule. I don't know why Windows or Linux doesn't have something similar. I don't need to fly back and get just one file, I never use that feature in Time Machine. But it does back up and that will be handy when my mac fails. i really wish Ubuntu had a backup system.

---

### Post by darthpenguin on 2009-04-20
> **kestrel1 said:**
> Yes, if you could access the disk long enough to clone it you would be OK.
I wouldn't think that melted elastic bands would get in to a HDD enclosure. These are very well sealed, but if your system is getting so hot that it melts elastic, you have a real risk of frying the system. It sounds like the drive has got far too hot & failed because of this. try the cooling

I see, but out of curiosity. How would I clone a disk? Can it be done from the live cd? is there a program or a terminal command? Could I clone to a USB HDD and boot off that?

thx

---

### Post by kestrel1 on 2009-04-21
You could use CloneZilla [http://clonezilla.org/](http://clonezilla.org/)
You may be able to boot from the USB HDD, but you would have to play around with Grub.

---

