---
title: "How To Partition An SD Card?"
date: 2008-12-21
forum: General Help
---

### Post by Just Another User on 2008-12-21
I have seen a few of these questions, and I finaly had it answered here
[http://geeks.pirillo.com/profiles/blogs/how-to-partition-an-sd-card](http://geeks.pirillo.com/profiles/blogs/how-to-partition-an-sd-card)
I have Ubuntu on a Live CD, However, my SD card does not show up in the list of devices in the partition editor. Any idea why? I'm so close to partitioning it, yet so far away.:(

---

### Post by 2hot6ft2 on 2008-12-21
> **Just Another User said:**
> I have seen a few of these questions, and I finaly had it answered here
[http://geeks.pirillo.com/profiles/blogs/how-to-partition-an-sd-card](http://geeks.pirillo.com/profiles/blogs/how-to-partition-an-sd-card)
I have Ubuntu on a Live CD, However, my SD card does not show up in the list of devices in the partition editor. Any idea why? I'm so close to partitioning it, yet so far away.:(
I partitioned one just a few days ago.
If it's not seeing it unplug it and plug it back in you may even browse to it BEFORE starting the partition editor to make sure the system sees it.
Only I did it in Ubuntu not on the live cd just went to System?Administration>Partition Editor (GParted) selected it from the drop down then the fun begins you have to make sure to right click each partition and UNMOUNT them before making changes
Once you make a change it will remount them and you have to UNMOUNT them again.

It works best if you only make one change at a time otherwise it will remount after the first change and give you an error (because it remounted them). pic attached of mine.

---

### Post by Just Another User on 2008-12-21
Mine doesnt have that, just the local HDD. /dev/sda. Should I call the SD something specific?

---

### Post by 2hot6ft2 on 2008-12-21
Are you doing it from linux or windows. Windows will not let you do it period. Does the card read like it should in a running system? I know you said the livecd so that should work if the card is not having other issues.

Always unmount external devices such as cards or drives before removing them or shut the pc down normally then remove them otherwise you will have issues.

---

### Post by nlz on 2008-12-21
have you tried the button on the right upper side of the screen to select a different device?

---

### Post by Just Another User on 2008-12-21
Yes, I have tried changing the device, I have also looked at the list of the devices the partition editor picked up, its the HDD thats it. I am using the Live CD so it would be Ubuntu, I havnt taken the SD card out, its been in since system start up. It appears fine, I can use it fine, I'm listening to music off it right now. The only other thing plugged in is my USB mouse. thats it. it doesnt appear in the partition editor. What if I formatted it? I have backed it up on the laptop. :confused:

---

### Post by 2hot6ft2 on 2008-12-21
> **nlz said:**
> have you tried the button on the right upper side of the screen to select a different device?
I was sure hoping that's what he meant by list of devices but you're right start with the obvious...lol.

---

### Post by 2hot6ft2 on 2008-12-21
Personally I don't boot up with a usb stick or sd card already in the pc unless I'm booting from it so you might try stopping whatever is using it, unmounting it, removing it and then putting it back in and once it shows up starting the partition editor.

Unless you want to try the command line way of doing it but that could be dangerous if you don't know what you're doing in linux.

---

### Post by Just Another User on 2008-12-21
you mean. shut down, remove it, start up, and then insert it once ubuntu is up and running again?

---

### Post by 2hot6ft2 on 2008-12-21
> **Just Another User said:**
> you mean. shut down, remove it, start up, and then insert it once ubuntu is up and running again?
That's one way. The other is does it show up as an icon on your desktop? If so right click and select unmount. Then remove it wait a few seconds then put it back in.

---

### Post by 2hot6ft2 on 2008-12-21
It should show up in the partition editor like shown in the pic attached.

---

### Post by nlz on 2008-12-21
are you sure that the SD card reader drivers are loaded on the liveCD?
In other words: is the SD card reader working at all?

---

### Post by 2hot6ft2 on 2008-12-21
> **nlz said:**
> are you sure that the SD card reader drivers are loaded on the liveCD?
In other words: is the SD card reader working at all?
You may have hit on something there. I am using a USB SD card adapter so it's seeing mine as a USB drive. I have not tried it with just the SD card slot. I don't know if it would work or not using a card slot.

I would think so but I haven't tried it.

I tried my sd card in the slot and it still shows up in partition editor but the icons representing the partitions have changed in nautilus. I don't know if that would matter.

---

### Post by nlz on 2008-12-21
can you open the SD card in nautilus?
Try to create an empty file (in nautilus or by using touch in the terminal), to be sure you have access.

---

### Post by Just Another User on 2008-12-21
definately works, it does come up as an icon. I would post a screen but the attachment thing keeps saying the files wrong:confused: And, what is Nautilus???

---

### Post by 2hot6ft2 on 2008-12-21
> **Just Another User said:**
> definately works, it does come up as an icon. I would post a screen but the attachment thing keeps saying the files wrong:confused: And, what is Nautilus???
If you renamed it you probably wrote over the files extension. just right click on it select properties and add .png to the end and close properties. Been there done that.

---

### Post by 2hot6ft2 on 2008-12-21
nautilus is the file browser like explorer in windows it opens folders.

---

### Post by Just Another User on 2008-12-21
Aaah, in which case, yes I can open it. The first picture (Screen) is of what it was like before unmouting. The second (Screen shot) is after unmouting and putting it back in. it then changed to like a drive...

---

### Post by 2hot6ft2 on 2008-12-21
Ok, now does it show up in the drop down in gparted? top right drop showing the drives.

---

### Post by Just Another User on 2008-12-21
nope:(
However, check out the properties in the attached. Pretty weird. It reads it as a hard disk and everything

---

### Post by 2hot6ft2 on 2008-12-21
It should show up if you restsarted gparted and clicked on the part I have circled

---

### Post by Just Another User on 2008-12-21
It doesnt. Just the HDD

---

### Post by 2hot6ft2 on 2008-12-21
That's weird, It may just be that card since it's not showing and vendor info or anything in properties. I'm at a loss to explain it. Sorry that I can't be anymore help but you've got me.

If you got it off ebay then maybe you got a bogus card (one where they have changed it to say it has more capacity than it really does). Hope you figure it out.

---

### Post by 2hot6ft2 on 2008-12-21
Only other option I can think of would be deleting the partition in windows and the making a new partition and trying gparted again.

Some sd cards come with a program on them (for lack of a better description) that causes problems using gparted and qparted on them. I read about it in the [http://forums.remote-exploit.org](http://forums.remote-exploit.org) forums you may try finding it. It can be removed and then they work fine.

---

### Post by Just Another User on 2008-12-21
It is a genuine SD. 2GB Sandisk. well, it is a micro SD in an SD addapter. I formatted it a while ago because it got corrupt. It is FAT. If it helps. But thanks anyway. :)

---

### Post by 2hot6ft2 on 2008-12-21
Micro sd aka transflash card. Haven't tried that yet. Might make it at least FAT32 and try again. Are you planning on making it bootable? I would be interested in seeing how that turned out. Just out of curiosity.

SanDisk shouldn't have any problem with and the size 2GB should work in most if not all readers. Good luck

---

### Post by Just Another User on 2008-12-21
Well, My Wii needs to read it. So I need to partition it, to put Whiite linux on it, a version of linux for the Wii. Thus the HOMEBREW SD name. It will only work on the Wii if it is FAT, I dont think FAT 32 works. In windows it appears as FAT. I'll format it as FAT 32 and see if it works :) Sit back and enjoy:popcorn:

---

### Post by 2hot6ft2 on 2008-12-21
Ok, I see. Cool. Hope you get it straightened out then.

---

### Post by Just Another User on 2008-12-21
Ok thanks. If I formatted as FAT 32, then added a 1GB partition, then formatted back to FAT. Would the partition still be there?

---

### Post by Just Another User on 2008-12-21
And, no luck, Gparted still doesnt pick it up

---

### Post by 2hot6ft2 on 2008-12-21
> **Just Another User said:**
> Ok thanks. If I formatted as FAT 32, then added a 1GB partition, then formatted back to FAT. Would the partition still be there?
Yes, formatting doesn't remove partitions. Partitions have to be deleted. Guess it wont work on a micro sd (transflash).

---

### Post by mamboo on 2009-02-13
Hi This might be a bit late, but I just had a very similar problem. 
The SD card did not show in gparted. I solved this by using the blockdevice name. In my case this was /dev/mmcblk0.

I tried "sudo gparted /dev/mmcblk0" et voila! a nice overview of my HCSD card with several partitions to be thrown away. :-)
What had happened is a long story about Ubuntu thinking that card was a nice place to install itself :P

Try something like "sudo ls /dev/mm*" and you'll get a list with partitions
a "sudo cat /dev/mm*" will show a lot of crap in your terminal, but gives you the time to check the led of your card reader (if there is any).

Another trick to see if the blockdevice is the correct one is to remove the card and try ls again.

hope this helps

---

### Post by mortana176 on 2009-02-27
I am also having this problem, although with a microSD card. Need to format it, because it is an 8 GB card, but only shows 56 KB available space in Nautilus when I put it in.

---

