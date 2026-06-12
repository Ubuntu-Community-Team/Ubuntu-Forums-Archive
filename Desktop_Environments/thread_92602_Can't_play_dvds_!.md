---
title: "Can't play dvds ??!"
date: 2005-11-19
forum: Desktop Environments
---

### Post by malacoda on 2005-11-19
I don't get it... what am I missing?? :confused: 

I can't get dvds to play - and from what I can tell it seems like mix of issues from not playing to not being mounted properly...

I've got a Rosewill DVD-RW/CD-RW (RD-162 dual layer DVD burner) drive and have libdvdcss 1.2.9 installed.

If I put a dvd into the drive I get mixed results depending on the dvd.  W/ two of the three commercial DVD movies I've tried - LA Confidential and Fist of Legend to be specific -  the disc will spin, Konquerer opens to it yet shows no files, Kaffine opens, tries to access it and then gives the following error:

'Could not read title information for DVD'

If I then right click in the 'DVD - undefined' icon on my kde desktop and 'Open' with either Mplayer or VLC I get the following error:

Could not mount device.
The reported error was:
mount: block device /dev/hda is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hda,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

Then, if I reach down and press the eject button on the drive the tray will open - e.g. another reason I believe it was never actually mounted.

With the third DVD - Matrix - the drive spins, the 'DVD-Matrix' (it recognizes the name) icon appears on the desktop, Kaffine opens, Konqueror opens with the message "Open 'media:/hda'?  Type: DVD Video Disk'", Kaffine tries to play it, and then gives the error window with title "'Kaffeine Player' is not responding. This window belongs to application kaffeine (PID=10073, hostname=localhost).
Do you wish to terminate this application? (All unsaved data in this application will be lost.)".

If I try to open with VLC or Mplayer, they crash and I get error; "/media/cdrom0 is a folder, but a file was expected."

Konquer does list the files: several are shown, if I click on 'autoplay.exe' nothing happens and I get the impression the 'install' executable has something to do w/ PC apps that might be on the disc and the remaining files won't be of use getting it to start playing. 

If I then press my dvd drive eject button it WON'T physically eject.  At this point if I right click on the 'DVD-undefined' icon and select 'unmount' some times it'll unmount and then I can eject, others it'll try to unmount for infinity (well, 50-60 seconds is the longest I waited) and I can't stop the unmount 'attempt' in any way other than by shutting down my system.

All of the multimedia apps work - I can play pretty much any type of video clip I come across on the web w/o a problem.

I believe the DVD-CD drive itself is fine since I can read CDs - both data and video  files such as divx avi's , play music CDs, burn CDs, etc. etc,.. but I can't play DVDs. 

I'm honestly not too concerned with watching DVDs on my PC but I DO want to burn some DVDs (there's an old discontinued TV series I liked that I've found and want to burn to watch on TV... 36" screen beats 19" LCD any day...) and I'm concerned that, if I can't watch DVDs, then I probably can't burn 'em... at least not without errors and a lot of wasted DVD-Rs.

Anyone have any suggestions?

Malac

---

### Post by Remmelas on 2005-11-20
I might suggest a forum mod move this to the kde forum instead of a Gnome forum, but here's a fairly general help link to at least make sure you have the essentials to enable dvd playback  [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by iH8forcedRegistration on 2005-11-20
What happens when you try to mount DVDs manually from Terminal or Konsole?

Insert your favorite move, open up a terminal and type ```
mount /dev/hda
```, then see what happens. Hopefully that'll give slightly more insight as to what's wrong.

Assuming the error you get from mount is similar to the one mplayer is giving you, there's a chance that the problem is with your fstab configuration. Again in a terminal, run ```
cat /etc/fstab
``` and paste the results onto this forum.

---

### Post by kruz on 2005-11-20
herm bad dvd playback sounds like a mounting problem

it said bad mount on /dev/hda???
your cdrom would most likely be something like

sudo mount /dev/scd0 if its usb in my case

but other than that im not sure

---

### Post by manicka on 2005-11-20
Try using kaffeine-xine instead of kaffeine and enabling dma on your dvd drive

[http://doc.gwos.org/index.php/DMA](http://doc.gwos.org/index.php/DMA)

---

