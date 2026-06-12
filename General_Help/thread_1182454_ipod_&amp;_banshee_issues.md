---
title: "ipod &amp; banshee issues"
date: 2009-06-09
forum: General Help
---

### Post by sigixv on 2009-06-09
So far i did not yet have any problems with my ipod in linux until yesterday when i loaded some podcasts onto it, using banshee.

The podcasts were not loaded as podcasts, but[COLOR=Red] **were converted to mp3's [COLOR=Green](EDIT: they were not converted but remained in their respective extentions: mp3, m4a)[/COLOR]**[/COLOR] and listed in the standard music folderfor some obscure reason. I noticed in bashee in the ipod's device properties it is listed to encode files to LAME mp3, without an option to select other formats (drop down list is further empty). So it might be possible it converted them (but why should i want that if it's a compatible device?). However, i checked the podcast extentions in banshee and the majority of those i copied allready had an mp3 extention.
In the memory-usage bar of the ipod in banshee the podcasts i copied were listed as other instead of music but i don't know if this is normal presentation of podcasts or not.

Today i plugged it in and it was unable to mount, stating that it was busy or already mounted. After a few minutes another box came up saying that something timed out (clicked it away to fast ;))

I mounted the device with
```
sudo umount /dev/sdb1

sudo mkdir /media/sdb1
sudo mount /dev/sdb1 /media/sdb1
```after which it immediatly showed up. Banshee also found the device without problems and now i wanted to test why the podcasts in the ipod were listed as regular mp3s...
Banshee however listed in the menu bar that the podcast were loaded as actual podcasts - and not as a traditional song (the ipod however thought otherwise apparently).

A little confused i wanted to delete the podcasts from the ipod. The ipod has been listed on "manual maintenance" (don't know if that the right english translation), this when adding the podcasts yesterday as with deleting them today.
More than 30minutes have passed by now, and i'm still waiting until the **** actually will start deleting the measly 5 podcasts... The ipod is not even filled up to half its memory, battery is full (and is now of course charging/charged) and banshee is still saying:
"Synchronising iPod"
"Preparing Synchronisation..."
with a status bar-thing going left to right. Right next to the status bar is a red square with a cross but it is grayed out... #-o

Being a bit reluctant to simply pull the ipod out, so for the moment i leave it plugged in until i know what the hell banshee is doing with it. By now i've grown a bit too proud to ask someone for a windows pc, so i don't want to risk having to reformat the diabolic apple device...

The ipod is a 3G nano 8GB, Banshee 1.4.3, Ubuntu 9.04

Thanks in advance

---

### Post by sigixv on 2009-06-09
Just to make it a bit more visible what the actual questions are:

-How to make banshee load podcasts as a podcast on an ipod, instead as an mp3
            *How to set banshee to load files in their original extention (ie: podcast .aac)
-How to troubleshoot when Synching in banshee fails

---

### Post by sigixv on 2009-06-09
some extra info showing in banshee after some fooling around:

[I]Translated:
[/I]"Was unable to eject Musicplayer: org.freedesktop.Hal.Device.Volume.NotMountedByHal: Device to unmount is not in /media/.hal-mtab so it is not mounted by HAL"

---

### Post by sigixv on 2009-06-09
i unmounted the ipod on the command line, banshee kept saying it was synching the device even when the cable was plugged out.

When reconnecting the ipod, i had to use code again to mount. All podcasts were still listed, no changes were made.
When trying again to delete them (this time i only selected 1 to delete) the same problem occurs and the synching fails. Banshee keeps working and it is even possible to play music from the ipod in the meantime.

---

### Post by sigixv on 2009-06-09
i was able to delete the files in rhythmbox without issues, once i got the ipod to mount.
Mounting the ipod seems hit & miss ever since i uploaded the podcasts. Mostly i have to mount it using the command line, sometimes it will also mount by just clicking the drive in nautilus...
Logging in/out doesn't seem to make much difference.

I've noticed that ipods not mounting is a often reoccurring issue, i just find it strange this only happened to me after loading podcasts onto it...

I'm going to completely remove banshee later this evening and see if a fresh install might fix this, since i believe it will be banshee related...

Any thoughts so far?

---

### Post by sigixv on 2009-06-09
Ok, so i removed banshee and podsleuth. Ipod problems were immediately solved, he mounted again automatically with all the bells & whistles one could want.

Reinstalled banshee (podsleuth, a tool to read apple ipod drives, loads automatically with it), problems persisted.

Too bad, no more banshee for me until novell is able to fix this issue...

---

