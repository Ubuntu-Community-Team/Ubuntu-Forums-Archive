---
title: "cant play dvd's"
date: 2009-02-07
forum: General Help
---

### Post by yarn on 2009-02-07
for some weird reason i can not play dvd's i have tried multiple different softwares to try and play them and i have installed the libdvdcss2...but it still says something about can not read from recources...if i try using MPlayer then it will open the dvd but it skips and acts as if it is buffering at 1 kb/s or something lol....any help would be much appreciated. thanks

---

### Post by mc4man on 2009-02-07
Is this related to the other thread about the laptop? If so, did you manage to ck. and or set the region?
A lot of dell's come with Matshita drives which absolutely need the region set. (and will only allow playback when there is a region match

---

### Post by yarn on 2009-02-07
yes it is about the laptop.   and i dont know how to check or change the region code on the drive...also   how you been...been a while since i talked to u.

---

### Post by mc4man on 2009-02-07
Pretty good
Let's ck. a few things, put a dvd in the drive and close out any player if it opens.
Run this and post the *cdrom:0 listing
```
sudo lshw -c disk
```

If not already go 
```
sudo apt-get install regionset
```

Then with *the dvd in the drive* run 
```
regionset
```

Look at or around line 4 if it says "type: SET" then answer n  and exit (note what region it is set to

If it says "type: NONE" then answer y and enter your region (1 - N. America, 2 - Europe
If your somewhere else answer n and post your location

---

### Post by hyper_ch on 2009-02-07
what does it exactely say?

---

### Post by yarn on 2009-02-07
*-cdrom                 
       description: DVD reader
       product: CDRWDVD TSL462D
       vendor: TSSTcorp
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom0
       version: DE09
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/cdrom0
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted
  *-disk
       description: ATA Disk
       product: Hitachi HTS54321
       vendor: Hitachi
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: FBBO
       serial: 080908FB0B00LGG57N8A
       size: 111GiB (120GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=08000000

what do u mean...if not already go?

---

### Post by yarn on 2009-02-07
also when i ran region set before i i said yes to changing region code it said      
drive plays discs from region(s):, mask=0xFF

---

### Post by scouser73 on 2009-02-07
Have you checked is **Movie Player (xine)** is installed? This can be found by going to; **System, Preferences, Main Menu** click on the Sound & Video section and make sure that **Movie Player (xine)** is checked.

---

### Post by yarn on 2009-02-07
i did try that and it didnt work...thanks though

---

### Post by mc4man on 2009-02-07
> what do u mean...if not already go? 
jus meant if you hadn't already installed regionset

Your good there, your set to region 2 and that dvd drive you have doesn't enforce region coding anyway.

vlc is much better for troubleshooting and totem-xine is a better totem player

go
```
sudo apt-get install vlc totem-xine libxine1-ffmpeg
```

After they're installed right click on Applications -> edit menus. Scroll down to sound & video, highlight it and then in r. side box right click on vlc -> properties. Change the command from vlc %U to 
```
vlc %f
```
Then try vlc (open vlc from the terminal with 

vlc
 go file -> open disk and post output if no good on playback

Yarn - am assuming your using 8.04 - right?

---

### Post by yarn on 2009-02-07
ok so i went to change it to u to f and it was already set to f...i went to go play the dvd and it played fine..thank you so much....i really appreciate it...gets boring during class...haha

---

### Post by mc4man on 2009-02-07
Are you using 8.04 or 8.10?

Edit: just to close this out for you 
if you installed libxine1-ffmpeg then totem-xine will also now work.

For 8.04 if you want to set vlc as the default (autorun) player see here
[http://ubuntuforums.org/showthread.php?p=4986640#post4986640](http://ubuntuforums.org/showthread.php?p=4986640#post4986640)

For 8.10 many ways, 
[http://ubuntuforums.org/showthread.php?p=6223490#post6223490](http://ubuntuforums.org/showthread.php?p=6223490#post6223490)

---

### Post by yarn on 2009-02-08
yea i am using 8.10...thanks again for the help.

---

