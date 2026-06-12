---
title: "Unsupported DVD-burner in K3b (cdrdao - isn't it?)"
date: 2005-08-28
forum: Desktop Environments
---

### Post by daller on 2005-08-28
Hi All,

I just bought a nice Pioneer DVR-109, but unfortunately it is unsupported - I'm afraid.

It's a 16x DL DVD burner, but it burn with 1,7x - And the written data is corrupted!

Booting up my old Windows XP machine (Against my will :)), I tested the drive, and it works perfectly.

Is there a list somewhere, where such support-information is available?

---

### Post by incinerator on 2005-08-28
To resolve the speed issue, try [this](http://ubuntuguide.org/#speedupcddvdrom) .

How would you know the data is corrupted? Have you used k3b's "verify" option in the "write cd/dvd" dialog? People have made the error of burning an iso image using the "Data CD/DVD" project before. When you write iso images, make sure you use the right item from the extras menu (or right-click with the mouse pointer in the main lower "welcome to k3b" panel to add the appropriate buttons).

---

### Post by daller on 2005-08-28
Well, I'll try!

I think the data was corrupted, cause I couldn't access the content at all!

Started writing a bunch of VOB's to a "VideoDVD" - Now it burns just fine - I love you man!

Well wait a second - Just stalled (80%) - maybe it sucks!

The disc is not readable (drive tries to spinup all the time!)

Is there a way to keep the speed down to 8x??? - K3b overrules my command of 8x!

---

### Post by incinerator on 2005-08-28
In the "Write CD/DVD" dialog, there is a blue button next to the speed selector field. Before starting the writing process, Insert the empty dvd medium into the writer and click that button. The speeds available in the selector field should now reflect the capabilities of your drive/media combination. If a lower speed than 8x is not available that may be caused by either the media or the the drive not supporting lower speeds.

Also, make sure you have the latest firmware installed on your writer. I would also recommend not using dvdrecord but instead growisofs from the dvd+rw-tools package.

---

### Post by daller on 2005-08-28
How do I choose growisofs over dvdrecord?

I have the newest firmware!

Pressing the refresh-button makes me choose between: "4, 6, 8, 12 and 16x" - Choosing 8x writes at approximately 12,5x - Weird, isn't it?

"On the fly" disabled makes no difference - does it? I mean the data is read directly from the harddisk. 

By the way, should I use a better cable, than just an ordinary 40pin-IDE cable?

---

### Post by godzero on 2005-08-29
growisofs:
It seems to use it as default if it's installed & you're creating a file system (like copying files from HD to DVD). Deffinate must-have.

40 pin cable:
Good to ~16x, since no DVD drives use data rates above ~22MB/s, the 40 pin (33MB/s) is OK, but if you have a spare 80 pin, go for it.

on the fly:
Creates the .iso as needed in real time. No need to create an .iso to HD before burning. Works good as long as you CPU doesn't hit 100% during burn.

As far as copying movie DVDs:
I haven't tried to under Linux so I don't know what tools to use, but I know under windows you have to strip the copy protection. If not the disk will technically burn right, but would be unusable.

---

### Post by incinerator on 2005-08-29
Make sure you install the dvd+rw-tools package and play around with k3b's configuration. Look around in the menu bar for something like "configure k3b". Somewhere a window can be found that lists all the helper programs k3b has found, there you will be able to see if growisofs is utilised or not. Check the official k3b documentation for details.

The Pioneer website says you NEED a 80-pin cable for that drive (now, why did I have to look that up for you? Have you really checked you've got the latest firmware release?)

Try writing at 4x speed. Weak media often produce bad results when written to with higher speeds.

For things like large .vob file switching "on-the-fly" off should not make a big difference imho.

---

### Post by daller on 2005-08-29
I checked pioneer's homepage some time ago, and the latest firmware was 1.57 (If it works fine in Windows XP, it's not a problem with the firmware, is it? (Well, Windows XP also can't burn at 16x, without making errors, but in Nero I can't decrease the speed) - Ugly comparing, I know!)

Sorry about the cable-thing - Didn't notice it!
I'll try with the 80pin-cable!
Is it a bad idea to have a DVD-ROM connected at the same cable?

growisofs is on the check-list.

Still can't keep the speed down - It still burns around 12x!

Thanks for your help so far!

---

### Post by daller on 2005-08-29
The 80pin-cable didn't help anything!

Burning at 4x (in K3b) burns with approx. 6x! (Seems like a general factor of 1,5 - no glue why...)

Stalled at 92%

The disc is not readable!

---

### Post by incinerator on 2005-08-29
The manuals of many dvd writers do indeed say that the writer should be the only device connected to the ide cable. Imho that should not be necessary but it is certainly worth a try.

As for the writing speed issues, I have never heard of such before. I would check the k3b message board and mailing list in order to find out if other users have similiar problems. The message board can be found by clicking the "Feedback" link at [http://k3b.org/](http://k3b.org/)

---

### Post by godzero on 2005-08-30
I had a problem writing to my cd-r/w with my (old) dvd rom drive hooked up on the same channel... weird speeds (slow), high cpu, lots of bad burns, etc. 
I had to power down, disconnect my dvd rom and power back up to burn. You might be seeing similar troubles.

On the speed thing... There's wiggle room in what is considered 1X; throw CAV, CLV and zoned CLV in the mix and a factor of 1.5X expected isn't too suprising. Try reducing your speed to 2 or 3X if you want.
Actually, for now I'd burn at the lowest speed your disks support for testing purposes.

---

### Post by drizek on 2005-08-30
same thing happens with me. i have a 16x burner, 8x dvd's and it burns at less tahn 1x. both dvd's ive burned with it were corrupt as well.

---

### Post by kassetra on 2005-09-01
[QUOTE=daller]Hi All,

I just bought a nice Pioneer DVR-109, but unfortunately it is unsupported - I'm afraid.

It's a 16x DL DVD burner, but it burn with 1,7x - And the written data is corrupted!

Booting up my old Windows XP machine (Against my will :)), I tested the drive, and it works perfectly.

Is there a list somewhere, where such support-information is available?[/QUOTE]

This particular drive has a firmware bug (which is not fixed yet, through version 1.58 of the firmware) that prevents it from writing some dvd media correctly using growisofs. If you want to burn a dvd with this drive and it will not work in k3b, gnomebaker, or nautilus - you will need to burn the dvd from a terminal window using the growisofs command - manually, like this:
 ```
sudo growisofs -use-the-force-luke=dao -speed=2 -dvd-compat -Z /dev/hdX=filename.iso
``` 
Where /dev/hdX is your device and filename.iso is your file.  Unfortunately, the speed has to stay around 2 in order to properly write the dvd for now.

---

### Post by daller on 2005-09-13
When do you think this will be fixed?

Many users on this forum seems to have the same problem...

Someone (Edit: that was you :)) think that its the powersupply that isn't powerful enough... Haven't tried a bigger one - should I?

[http://ubuntuforums.org/showthread.php?t=34516&page=3&pp=10&highlight=DVR-109](http://ubuntuforums.org/showthread.php?t=34516&page=3&pp=10&highlight=DVR-109)

It's really sad... this is the only thing that keeps me from clean-installing (deleting my XP partition)

Do you know about another _working_ DVD writer with support for at least 8x? (For about $70)

---

### Post by Slackitude on 2005-09-13
I have a Lite-On model SOHW-1673S that's given me zero problems in Linux. I've burned DVDs, SVCDs and just about anything else you could want/need to burn with not so much as a hiccup. Plus it was fairly inexpensive. Hope that helps and sorry the one you've got is giving you trouble.

---

### Post by daller on 2005-09-14
Thanks... I'll consider buying that one...

...But is there no hope for my DVR-109? (kassetra)

---

### Post by daller on 2005-09-20
[QUOTE=kassetra]This particular drive has a firmware bug (which is not fixed yet, through version 1.58 of the firmware) that prevents it from writing some dvd media correctly using growisofs. If you want to burn a dvd with this drive and it will not work in k3b, gnomebaker, or nautilus - you will need to burn the dvd from a terminal window using the growisofs command - manually, like this:
 ```
sudo growisofs -use-the-force-luke=dao -speed=2 -dvd-compat -Z /dev/hdX=filename.iso
``` 
Where /dev/hdX is your device and filename.iso is your file.  Unfortunately, the speed has to stay around 2 in order to properly write the dvd for now.[/QUOTE]

Hi Kassetra,

Please unsticky this???

[http://ubuntuforums.org/showthread.php?t=27310](http://ubuntuforums.org/showthread.php?t=27310)

...IMHO not relevant anymore...

---

### Post by daller on 2005-09-28
[QUOTE=Slackitude]I have a Lite-On model SOHW-1673S that's given me zero problems in Linux. I've burned DVDs, SVCDs and just about anything else you could want/need to burn with not so much as a hiccup. Plus it was fairly inexpensive. Hope that helps and sorry the one you've got is giving you trouble.[/QUOTE] 

Just received the drive today! - Seemed like it work - Burned a Video DVD project at approx 16x - Great it actually worked! (tested it on my DVD-player) 

...but after a reboot, something weird is going on!Now - for some weird reason - It's down to 1,2x which is really annoying! - any ideas? 

...I ran a dist-upgrade just before rebooting - can it have anything to do with that?

---

