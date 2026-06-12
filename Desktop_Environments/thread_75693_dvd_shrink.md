---
title: "dvd shrink"
date: 2005-10-14
forum: Desktop Environments
---

### Post by b3nw on 2005-10-14
Has anyone been able to get DVD Shrink working with the latest version of Wine in breezy. The [old method]("http://mrbass.org/linux/ubuntu/dvdshrink/") on hoary no longer works because wine has a different structure and config now.

Currently it says to do apt-get install wine winesetuptk but these 2 packages don't play nice together anymore it seems. I currently have got dvd shrink going but when I try to open a disk I get 

```
DVD Shrink encountered an error and cannot continue.

Failed to initalize ASPI device

```

Frusterating as this is the only thing keeping windows on my box.
Thanks for your time,

---

### Post by manicka on 2005-10-14
If you already have it installed, hit alt-f2 and run the command 'winecfg'. This will bring up the new winecfg panel. 

In the applications tab click on 'add appplication' and navigate your way to the dvdshrink .exe. Then set the windows version to 'windows xp' for dvdshrink.
Click on the drives tab and let it autodetect your drives.
Close winecfg and start dvdshrink again and the ASPI error should be gone.

The other problem you're going to have is a that the compression rates won't work properly when you open a disc for analysis. What I am doing at the moment is copying the whole dvd to the hardrive using dvdbackup. It's a command line program but works really well. Once installed you can use this command to backup the whole disc to your home directory

dvdbackup -i /dev/dvd -o /home/*yourusername*/ -M

I then choose 'open files' in dvd shrink and it is able to analyse the files from the hard disc (created by devbackup) properly and backup in the usual way. I usually backup to an iso image then burn with nautilus or k3b.

It's a clunky solution and adds about 10 minutes to the whole process but it is the only way I can get it to work. Apparently this bug is solved in the 20050310 release of wine but we don't have a deb for it yet and I haven't been able to successfully compile it.

HTH :)

P.S. You need libdvdcss2 installed for dvdbackup to work properly

---

### Post by b3nw on 2005-10-14
thanks alot for your quick reply. I have gotten rid of the error, but a new has taken its place.

As soon as its starts analyzing the disk i get.

```
DVD Shrink encountered an error and cannot continue.

Failed to read file "D:\"

No access to memory location


```

*update: i was able to get past this error by disabling video preview. trying the rest now.

Thanks again,

---

### Post by brenx on 2005-10-23
Try to open movie with any player and pause it. And then DVD Shrink will open it.

---

### Post by manicka on 2005-10-24
Opening the movie is not the issue. DVD Shrink won't analyse the disc properly so that it can be reduced to a single layer disc.

---

### Post by fizgig on 2005-10-24
Opening the movie is an issue to me as I get the same "Failed to read file..." error (even with the winxp change in winecfg).  I didn't get this with the Hoary version of wine.  :(  Anyhow, I'm using dvdbackup to copy the entire dvd to disk now and see if dvdshrink can handle it.  I'll report how it goes.

---

### Post by bonifacio on 2005-10-25
manicka, 

I tested your method and it is fabulous!  One thing I notice though is that creating an iso from dvdshrink took a LOT of time.  The speed by which shrink process the backuped dvd in the hard disk is dubiously slow (I avg about 1300 kbps).  Is there any way I can speed up that process?  Thanks.

---

### Post by bionnaki on 2005-10-25
how long did it take?

I know dvdbackup took me about an hour to rip the dvd.

---

### Post by bonifacio on 2005-10-25
bionnaki,

It's not dvdbackup I'm complaining about.  It's dvdshrink.  It took a hell of a lot time to create the iso from the backuped source.  I'll say more than an hour (my guesstimate).  The thing is this creation of iso is all happening now in the same hard disk.  There is no overhead of reading from a dvd device (thats done already after dvdbackup).

---

### Post by manicka on 2005-10-25
Mine generally take about 10-15 mins to rip, then 20-30 minutes to process depending on the complexity of the disc. I have a fairly new dual layer burner.

do you have dma enabled on that drive?

---

### Post by bjhess on 2006-01-29
[QUOTE=manicka]Mine generally take about 10-15 mins to rip, then 20-30 minutes to process depending on the complexity of the disc. I have a fairly new dual layer burner.

do you have dma enabled on that drive?[/QUOTE]

I'd like to resurrect this thread because it was hitting on exactly what I've asked elsewhere in the forum.  I have the latest libdvdcss2 and libdvdread3 (3, I think?) packages installed and my dvd rips with DVD Backup take 45-50 minutes.  Any reason why that could be?

---

### Post by manicka on 2006-01-29
Do you have dma enabled?

[http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2514447](http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2514447)

---

### Post by bjhess on 2006-02-01
Thank you, thank you, thank you!  Not sure why Ubuntu installed without enabling DMA for my DVD-ROM.  That's really frustrating.  Anyway, this sped the particular rip I tried last night up to < 20 minutes.  And viewing DVD's from the ROM is now bearable.

Thanks!

---

