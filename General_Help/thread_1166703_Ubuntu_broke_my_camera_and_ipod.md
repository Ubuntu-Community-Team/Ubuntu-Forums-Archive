---
title: "Ubuntu broke my camera and ipod?"
date: 2009-05-22
forum: General Help
---

### Post by shorxrore on 2009-05-22
Hi,

After hooking up and using my Ipod and digital camera on my laptop with Ubuntu they are no longer recognized on my main PC that uses Windows Vista.

I am not an Ubuntu expert but this is the only thing they both have in common since not working. Both my ipod and camera are completely unrecognized by Vista now, not only that but while my ipod was hooked up to my laptop Ubuntu randomly erased/corrupted a majority of the files making them unreadable by my ipod.

has anyone experienced anything like this? I have no way to change or, now, fix the music on my ipod and no way of getting pictures off my camera (i'll have to buy a SD card reader for my pc now)

help?

---

### Post by nandemonai on 2009-05-22
> **shorxrore said:**
> Hi,

After hooking up and using my Ipod and digital camera on my laptop with Ubuntu they are no longer recognized on my main PC that uses Windows Vista.

I am not an Ubuntu expert but this is the only thing they both have in common since not working. Both my ipod and camera are completely unrecognized by Vista now, not only that but while my ipod was hooked up to my laptop Ubuntu randomly erased/corrupted a majority of the files making them unreadable by my ipod.

has anyone experienced anything like this? I have no way to change or, now, fix the music on my ipod and no way of getting pictures off my camera (i'll have to buy a SD card reader for my pc now)

help?

Simply plugging them in will not change anything on the devices. It will try and mount then and if it can't then error out. I use both a camera and IPOD with Ubuntu fine. Something tells me that another issue is to blame here, I've never heard of Linux randomly formatting anything, (unlike Windows, where if it doesn't understand something it asks you to format it right away).

Are you sure you didn't do something to try and get them working?

---

### Post by crazypeppo on 2009-05-22
LOL... "Ubuntu did it..."
Sue 'em for sure.

---

### Post by scouser73 on 2009-05-22
> **shorxrore said:**
> Hi,

After hooking up and using my Ipod and digital camera on my laptop with Ubuntu they are no longer recognized on my main PC that uses Windows Vista.

I am not an Ubuntu expert but this is the only thing they both have in common since not working. Both my ipod and camera are completely unrecognized by Vista now, not only that but while my ipod was hooked up to my laptop Ubuntu randomly erased/corrupted a majority of the files making them unreadable by my ipod.

has anyone experienced anything like this? I have no way to change or, now, fix the music on my ipod and no way of getting pictures off my camera (i'll have to buy a SD card reader for my pc now)

help?

You silly sausage.

---

### Post by shorxrore on 2009-05-22
thanks, i'll continue to try and fiddle with it but it just seems like they've been reformatted and aren't recognized by windows. oh well, i'll just have to wait and see.

---

### Post by ActiveFrost on 2009-05-22
> Both my ipod and camera are completely unrecognized by Vista now, not only that but while my ipod was hooked up to my laptop Ubuntu randomly erased/corrupted a majority of the files making them unreadable by my ipod.
Ubuntu does not randomly delete files :p

---

### Post by abhilashm86 on 2009-05-22
> **shorxrore said:**
> thanks, i'll continue to try and fiddle with it but it just seems like they've been reformatted and aren't recognized by windows. oh well, i'll just have to wait and see.

always you should mount and umount devices, ubuntu treats even your hard disk in this manner, so be carefull!!
when you plug in ipod or digital devices, ubuntu ask whether to run device or cancel.......... better option is to cancel, then make your decisions.
My philips mp3 player works fine and find no error.........

---

### Post by abhilashm86 on 2009-05-22
> **ActiveFrost said:**
> Ubuntu does not randomly delete files :p

yea thats beauty of linux:) cheers. always remember ubuntu thinks like you know what actually you are performing:) 
so be carefull, ask forums whenver you have doubt..........

---

### Post by geirha on 2009-05-22
With USB mass storage devices, you must always remember to right-click and choose unmount before you unplug it. If you just unplug it without unmounting, there may be buffered data left that was yet to be written to the USB, and so you risk losing files you wanted to write to it, and also risk corrupting the filesystem on it. The latter has probably happened in this case, so you'll want to run a filesystem check on it.

---

### Post by shorxrore on 2009-05-22
thanks for the advice re: properly mounting etc

although i'm 99.9999% sure i never unmounted incorrectly i'll take your advice and attempt to run a filesystem check on it.

problem is i dont have my ubuntu laptop right now and my PC with windows wont recognize anything :\ so i'll have to wait till i get the laptop again

hopefully this is the problem

---

### Post by PumaSpeedCat on 2009-05-28
If you can't access your iPod using either Ubuntu or Windows, (just make sure that's it IS corrupted first) you will have to restore it by using iTunes(in windows)...., then you can re-sync all your songs, as in reality, you can't REALLY brick an ipod. (you can, but I will not list how...based on simple linux command which is VERY damaging.)

I hope this helps ya, 

I use my iPod touch and Digital Camera with Ubuntu all the time, and so far no problem!  :p

---

