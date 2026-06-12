---
title: "USB startup disk help"
date: 2009-04-23
forum: General Help
---

### Post by Bearded-flower on 2009-04-23
OK, so i downloaded the jaunty ISO of of ubuntu.com right?
so i use unbootin to make a USB startup disk right.
I reboot my system and hit F11 and it comes up with the boot menu right?
so i scroll down and click on the USB right?
i hit enter right
it comes up with broken partition or something like that right
so whats the dealio with this?

---

### Post by Bearded-flower on 2009-04-23
Bump

---

### Post by andrewabc on 2009-04-23
Try installing to USB stick again.

With broken partition error, is it just a "broken partition table"? at top left of black screen?

I had something similar with an old pentium 4. I tried 2 usb sticks, and both failed. Yet they both worked fine on my core2duo.

See my thread:
[LiveUSB faster than liveCD and other liveusb questions](http://ubuntuforums.org/showthread.php?t=1107298)

Particularly:
> I could not get liveusb to work on my old pentium4 computer. After BIOS kingston usb would give flashing _ at top left of screen. rally2 would give invalid partition table_ at top left of screen.

---

### Post by Bearded-flower on 2009-04-23
Hmmm i removed all the files and re-installed but i would try another USB but my other 2G USB got flogged and now i only have this one which dosent seem to work and a few 1G ones.
Hmmm
ill try a 1G when i go home

---

### Post by Carl Hamlin on 2009-04-23
> **Bearded-flower said:**
> OK, so i downloaded the jaunty ISO of of ubuntu.com right?
so i use unbootin to make a USB startup disk right.
I reboot my system and hit F11 and it comes up with the boot menu right?
so i scroll down and click on the USB right?
i hit enter right
it comes up with broken partition or something like that right
so whats the dealio with this?

I and a bunch of other folks are having similar issues with Jaunty from USB. Not sure what's going on - there doesn't currently seem to be a published workaround.

---

### Post by Bearded-flower on 2009-04-23
God damn cutting edge technoligy!!!

---

### Post by Bearded-flower on 2009-04-23
MMMyep just like before
"invalid or damaged bootable partition"
WHAT IS THE EDAN DOING WRONG!!!

---

### Post by Bearded-flower on 2009-04-23
Woah thought just ocured, do you think i could create an 8.10 bootup disk install that and then upgrade to jaunty from there?

---

### Post by Bearded-flower on 2009-04-23
bump

---

### Post by Bearded-flower on 2009-04-24
So does anyone know?

---

### Post by Bearded-flower on 2009-04-24
Ummm BUMP!!!

---

### Post by Bearded-flower on 2009-04-24
Or you know, no one could help.
either way

---

### Post by Jason Pettitt on 2009-04-24
I've had similar woes in the past. What happened was that, in my haste, I didn't unmount (right click on its desktop icon and select 'Unmount Volume') my USB stick properly after creating the boot disk on it. Once I'd tried again and did a proper dismount it worked fine. I wonder if the same is happening with you?

---

### Post by MN Noob on 2009-04-24
I had similar issues when I installed Easy Peasy. At first I was getting that partition error. I put it in my mac and ran a disk check and found out it had some errors on it. Bought a new USB disk. Got further but errored out during install. Then I realized, as Jason did, I hadn't unmounted it properly. Did that and booted into easy peasy just fine.

I am going to go out on a limb and guess your USB drive is bad. Although, I would re download the img file and make sure you are unmounting the drive properly.

---

### Post by Bender2k14 on 2009-04-24
I don't have to time right now to upgrade a USB installation right now, but...

I know that this is not exactly the same problem, but does [this bug]("https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/277903") report help at all?  Specifically, does [this link from that bug report]("http://ubuntuliving.blogspot.com/2008/11/missing-operating-system-step-by-step.html") help?  It probably will not help, but it is worth checking out.

So, does that change anything?

---

### Post by Blue Sassley on 2009-04-24
Don't use unetbootin, I have never ever seen that program work, I find the best way to make a USB boot device is I burn the Live CD of Ubuntu and then I goto System --> Administration --> USB Startup Disk Creator and create all my USB boot devices from there. As a matter of fact I just finished the one for 9.04 and I'm booted on the USB right now and I'm downloading the NetBook Remix ISO to make a second USB device.

I hope this helps!
Blue

---

### Post by Bender2k14 on 2009-04-24
Oh...I didn't notice that you were using Unetbootin.  Why use Unetbootin to create USB installations of Ubuntu when Ubuntu has a superior tool to do that? I agree with Blue Sassley; you should try using the USB Startup Disk Creator.  You can even make it persistent!

---

### Post by Blue Sassley on 2009-04-24
> **Bender2k14 said:**
> You can even make it persistent!

Well I donno about the persistent part, for some reason with the 9.04 that doesn't seem to be working, but then again I could have screwed up.

Blue

---

### Post by Bender2k14 on 2009-04-24
> **Blue Sassley said:**
> Well I donno about the persistent part, for some reason with the 9.04 that doesn't seem to be working, but then again I could have screwed up.

It is not just you. I also tried to create a persistent USB installation of Ubuntu, but my changes were lost on reboot. I created [a thread]("http://ubuntuforums.org/showthread.php?p=7130156#post7130156") asking if anyone else had this problem, but no one else responded. However, it is supposed to be persistent.

---

### Post by Meow27 on 2009-04-24
**_make sure the partition is fat16_** i cant stress this enough

unet booting works fine in fat16,

make sure you have enough disk space

---

### Post by Kinst on 2009-04-24
Mine still doesn't work for netbook remix. The MD5 check says it's good. I tried 3 different usb sticks but none of them work. It always just says "boot error" when my computer boots off the usb. I follow the guide([https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)) and then carefully dismount it. I don't understand! :-(

---

