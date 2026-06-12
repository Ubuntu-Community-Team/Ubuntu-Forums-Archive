---
title: "I want to copy a full .iso image from a dvd"
date: 2009-03-27
forum: General Help
---

### Post by redonwhite on 2009-03-27
Hello.  I would like to back up my dvd to an .ISO image.  I dont want to compress it at all.  I want the full ISO.  What app would you recomend for this.  I have tried a lot of the apps and many of them compress the file loosing the dvd quality.  THANKS

---

### Post by logos34 on 2009-03-27
easiest is to use the dd command:

> dd if=/dev/dvd of=file.iso

---

### Post by redonwhite on 2009-03-27
> **logos34 said:**
> easiest is to use the dd command:

Thank you logos.  So should i just pop in the dvd first then do the command?

---

### Post by logos34 on 2009-03-27
yeah, put it in, but if it mounts, unmount first:

sudo umount /media/cdrom0

(not technically necessary but speeds up the read/data transfer)


Add: post back if there's a size dispcrepancy between the original and the copy (I have this issue on x64 Hardy.  Probably won;t affect you though)

---

### Post by HermanAB on 2009-03-27
You can even use cat to do that:

$ cat /dev/sdb > file.iso

---

### Post by redonwhite on 2009-03-27
> **logos34 said:**
> yeah, put it in, but if it mounts, unmount first:

sudo umount /media/cdrom0

(not technically necessary but speeds up the read/data transfer)


Add: post back if there's a size dispcrepancy between the original and the copy (I have this issue on x64 Hardy.  Probably won;t affect you though)

excuse my ignorance.  When i type the dd command it says "dd: opening `/dev/dvd': No such file or directory".  Where would i create the dvd file.
When i go into the Dev file it wont let me create a file.

---

### Post by coffeecat on 2009-03-27
If you want a GUI app to do that, just use k3b. It's in the repos and will run under Gnome.

---

### Post by SuperSonic4 on 2009-03-27
> **coffeecat said:**
> If you want a GUI app to do that, just use k3b. It's in the repos and will run under Gnome.

With a load of dependencies though.

/dev/dvd is the location of your dvd drive, it's more likely to be /dev/cdrom. ```
sudo fdisk -l
``` may tell you.

mine is /dev/sr1

---

### Post by redonwhite on 2009-03-27
> **SuperSonic4 said:**
> With a load of dependencies though.

/dev/dvd is the location of your dvd drive, it's more likely to be /dev/cdrom. ```
sudo fdisk -l
``` may tell you.

mine is /dev/sr1

Ahhh /dev/sdb1 for me.  Thank you kind sir.

---

### Post by coffeecat on 2009-03-27
> **SuperSonic4 said:**
> With a load of dependencies though.

A few tens of megabytes of KDE libraries. With the size of hard drives these days, and so long as you've got broadband, I really fail to understand why people get so upset about this.

---

### Post by redonwhite on 2009-03-27
hmmm i typed , "sudo dd if=/dev/sdb1 of=file.iso"  hit enter and now its just hanging in the terminal.  Is it going on behind the scenes and i just dont know it?  Where would it be saving this .iso file?  Thanks for all your help guys and gals!

---

### Post by ByteJuggler on 2009-03-27
It would do its thing without output yes, you should however see dvd and hard drive activity.  The file goes in the current folder.  If you want it on your desktop instead, issue the command with "of=~/Desktop/file.iso"

---

### Post by redonwhite on 2009-03-27
> **ByteJuggler said:**
> It would do its thing without output yes, you should however see dvd and hard drive activity.  The file goes in the current folder.  If you want it on your desktop instead, issue the command with "of=~/Desktop/file.iso"

Thank you Byte.  Yeah there is definitely activity my computer is slowing down to a crawl =).  How will i know when the ripping is complete?

---

### Post by boof1988 on 2009-03-27
> **redonwhite said:**
> Ahhh /dev/sdb1 for me.  Thank you kind sir.

As I understand...

```
sudo fdisk -l
```
... will tell you the hard-disk-drive info.

So (I think) /dev/sdb1 is (most likely) one of you hard-drive partitions.

If you type in...
```
cat /etc/fstab
```
...it will print out the hard-drives and the optical (CD/DVD) drive mount-point information.

Here's mine:

```
*user@host*:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d6e63

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3187    25599546   83  Linux
/dev/sda2            3188        4863    13462470    5  Extended
/dev/sda5   *        3188        4781    12803773+  83  Linux
/dev/sda6            4782        4863      658633+  82  Linux swap / Solaris
```

```
*user@host*:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=b2e382a7-e747-4183-b1b7-2bf04e8f8c8e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=2d5affb9-7cfd-415c-ae5b-1c9ff1f47259 none            swap    sw              0       0
#
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

So (if using dd) I would type:
```
dd if=/dev/scd0 of=*~/path/to/file.iso*
```

Also (I hope someone else has the correct info about this) are there any special codecs or plugins which might be needed to copy some DVDs to hard-disk-drive?

---

### Post by dhughes on 2009-03-27
> **redonwhite said:**
> hmmm i typed , "sudo dd if=/dev/sdb1 of=file.iso"  hit enter and now its just hanging in the terminal.  Is it going on behind the scenes and i just dont know it?  Where would it be saving this .iso file?  Thanks for all your help guys and gals!

 It would take a while, at least, 4.7GB being duplicated and made into an image (iso). It should end up in your home directory after a little while, you can probably hear your CD/DVD drive spinning.

---

### Post by tom56 on 2009-03-27
Errr.. just so you all know for next time. Right click -> copy disk -> write to image file. And you're done :)

---

### Post by redonwhite on 2009-03-27
> **boof1988 said:**
> As I understand...

```
sudo fdisk -l
```
... will tell you the hard-disk-drive info.

So (I think) /dev/sdb1 is (most likely) one of you hard-drive partitions.

If you type in...
```
cat /etc/fstab
```
...it will print out the hard-drives and the optical (CD/DVD) drive mount-point information.

Here's mine:

```
*user@host*:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d6e63

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3187    25599546   83  Linux
/dev/sda2            3188        4863    13462470    5  Extended
/dev/sda5   *        3188        4781    12803773+  83  Linux
/dev/sda6            4782        4863      658633+  82  Linux swap / Solaris
```

```
*user@host*:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=b2e382a7-e747-4183-b1b7-2bf04e8f8c8e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=2d5affb9-7cfd-415c-ae5b-1c9ff1f47259 none            swap    sw              0       0
#
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

So (if using dd) I would type:
```
dd if=/dev/scd0 of=*~/path/to/file.iso*
```

Also (I hope someone else has the correct info about this) are there any special codecs or plugins which might be needed to copy some DVDs to hard-disk-drive?

Everyone ready to laugh.  I was creating an ISO of my Harddrive. haha.  Luckily i read this post ( thank you by the way ) and found the file in home at 61 Gigs!!!!!!!  hahaha.  okay im gonna try this again but gotta get this trash taken out first.

---

### Post by dhughes on 2009-03-27
> **redonwhite said:**
> Everyone ready to laugh.  I was creating an ISO of my Harddrive. haha.  Luckily i read this post ( thank you by the way ) and found the file in home at 61 Gigs!!!!!!!  hahaha.  okay im gonna try this again but gotta get this trash taken out first.

 We'll just call it a backup.

---

### Post by redonwhite on 2009-03-27
typed , "sudo dd if=/dev/scd0 of=file.iso" ...output , 

"dd: reading `/dev/scd0': Input/output error
5088+0 records in
5088+0 records out
2605056 bytes (2.6 MB) copied, 6.64486 s, 392 kB/s"

scratching head*

---

### Post by boof1988 on 2009-03-27
> **tom56 said:**
> Errr.. just so you all know for next time. Right click -> copy disk -> write to image file. And you're done :)

This is a *very* good idea.  I have used this method.  But you have to have the full Ubuntu (ubuntu-desktop(?)) install to have this feature.  I use the minimal install so I don't have this feature.

---

### Post by redonwhite on 2009-03-27
> **tom56 said:**
> Errr.. just so you all know for next time. Right click -> copy disk -> write to image file. And you're done :)

I've tried this before and it would always freeze about 80 to 90 percent of the way in.

---

### Post by logos34 on 2009-03-27
> **redonwhite said:**
> typed , "sudo dd if=/dev/scd0 of=file.iso"

(back from break)...wow, such troubles...I was about to suggest scd0, but the point is you should have symlinks in /dev ('dvd'-->scd0, cdrom-->scd0, etc)...Annoying how the newer ubuntu releases don't apparently do that by default, dunno.

Maybe try using the image option in the gui, as mentioned above (nautilus or konqueror)

Edit: although I now see even that option is not working for you:

> **redonwhite said:**
> I've tried this before and it would always freeze about 80 to 90 percent of the way in.

---

### Post by redonwhite on 2009-03-27
I tested out the right click--copy as image.  It started up copied for about 1 minute and now says completed.  File is only 2.5 mb large though.

---

### Post by boof1988 on 2009-03-27
> **redonwhite said:**
> typed , "sudo dd if=/dev/scd0 of=file.iso" ...output , 

"dd: reading `/dev/scd0': Input/output error
5088+0 records in
5088+0 records out
2605056 bytes (2.6 MB) copied, 6.64486 s, 392 kB/s"

scratching head*

I suspect you may need some codecs or plugins (as noted [in this post](http://ubuntuforums.org/showpost.php?p=6968759&postcount=14) to copy this DVD.  You might need to enable the [medibuntu repository](https://help.ubuntu.com/community/Medibuntu) and then install libdvdcss2 &/or w32(64)codecs in order to copy the DVD to hard-disk.

Please ask if you need further explanation of this.

Also... this [Restricted Formats Page @ Ubuntu Community Document](https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs) may be useful.

---

### Post by redonwhite on 2009-03-27
> **boof1988 said:**
> I suspect you may need some codecs of plugins to copy this DVD.  You might need to enable the [medibuntu repository](https://help.ubuntu.com/community/Medibuntu) and then install libdvdcss2 in order to copy the DVD to hard-disk.

Please ask if you need further explanation of this.

Also... this [Restricted Formats Page @ Ubuntu Community Document](https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs) may be useful.

Thank you Boof.  I will look into this.  I'm currently giving k3b a try as its one of the few i haven't tried yet.  I don't know my way around K3b but i chose copy dvd and i guess when it ask me to insert the blank dvd ill just ignore it and steal my ISO from the folder haha.  Can anyone confirm that im doing this right that is familiar with k3b.  I consider my self to have a decent understanding of computers and im really embarrassed i'm having so much trouble ripping a dvd.  oh well we all gotta learn somehow. haha.

---

### Post by boof1988 on 2009-03-27
> **redonwhite said:**
> Thank you Boof.  I will look into this.  I'm currently giving k3b a try as its one of the few i haven't tried yet.  I don't know my way around K3b but i chose copy dvd and i guess when it ask me to insert the blank dvd ill just ignore it and steal my ISO from the folder haha.  Can anyone confirm that im doing this right that is familiar with k3b.  I consider my self to have a decent understanding of computers and im really embarrassed i'm having so much trouble ripping a dvd.  oh well we all gotta learn somehow. haha.

That small (few MB) iso will not be an image of the DVD.  I am pretty sure you will need to enable [Medibuntu Repositories](https://help.ubuntu.com/community/Medibuntu) and install w32codecs (for 32bit-Ubuntu) or w64codecs (for 64bit-Ubuntu) in order to rip the DVD to hard-disk.

---

### Post by logos34 on 2009-03-27
> **boof1988 said:**
> I am pretty sure you will need to enable [Medibuntu Repositories](https://help.ubuntu.com/community/Medibuntu) and install w32codecs (for 32bit-Ubuntu) or w64codecs (for 64bit-Ubuntu) in order to rip the DVD to hard-disk.

??  that's news to me...

> **redonwhite said:**
> I don't know my way around K3b but i chose copy dvd and i guess when it ask me to insert the blank dvd ill just ignore it and steal my ISO from the folder haha.  Can anyone confirm that im doing this right that is familiar with k3b.

EDIT: yep (as you found out)...OR --> 'copy dvd'>settings>check 'create image'>check 'Only create image'>uncheck 'remove image'>cancel after rip.  Forgot you could do it that way.

wonder what the deal is...what does
> 
isoinfo -d -i /dev/scd0

show?

---

### Post by boof1988 on 2009-03-27
> **logos34 said:**
> ??  that's news to me...

Have you looked [here](https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs) and [here](https://help.ubuntu.com/community/Medibuntu)?

:)

---

### Post by redonwhite on 2009-03-27
> **logos34 said:**
> ??  that's news to me...



can't do that.  k3b will only burn image/iso (although it can rip video dvds and audio cds)...

wonder what the deal is...what does


show?

How do you guys put your output in those internal boxes?
heres the output of isoinfo -d -i /dev/scd0

CD-ROM is in ISO 9660 format
System id: 
Volume id: WAKINGLIFE
Volume set id: WAKINGLIFE
Publisher id: 
Data preparer id: 
Application id: 
Copyright File id: 
Abstract File id: 
Bibliographic File id: 
Volume set size is: 1
Volume set sequence number is: 1
Logical block size is: 2048
Volume size is: 3640504
NO Joliet present
**BAD RRVERSION (0)
NO Rock Ridge present
 

I was able to get the ISO from K3b.  I just chose to copy the dvd.  Then when it hit 50 percent it asked me to insert a double layer.  I then canceled and took the .iso file out of the /tmp.  Quality doesnt look excellent but it does say 6.9 gigs.

---

### Post by logos34 on 2009-03-27
> **boof1988 said:**
> Have you looked [here](https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs) and [here](https://help.ubuntu.com/community/Medibuntu)?
:)

You don't need any of that to just copy the iso

> **redonwhite said:**
> 
I just chose to copy the dvd.  Then when it hit 50 percent it asked me to insert a double layer.  I then canceled and took the .iso file out of the /tmp. 

oh, I see what you mean now.

---

### Post by SuperSonic4 on 2009-03-27
k9copy is better for DVD Ripping

---

### Post by redonwhite on 2009-03-27
> **SuperSonic4 said:**
> k9copy is better for DVD Ripping

It sets it to a 4gig file size though.  And once i went in and changed it to 8 gig and it stalled 90 percent of the way through.

---

### Post by tom56 on 2009-03-27
> **redonwhite said:**
> I've tried this before and it would always freeze about 80 to 90 percent of the way in.

I expect either the disc is scratched or you need to install libdvdcss2 (or both)
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Ubuntu%208.10%20(i386,%20amd64](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Ubuntu%208.10%20(i386,%20amd64))

EDIT: I'm guessing you have enough free space on the hard drive you are copying to

---

### Post by boof1988 on 2009-03-27
> **redonwhite said:**
> It sets it to a 4gig file size though.  And once i went in and changed it to 8 gig and it stalled 90 percent of the way through.

One way to copy the full DVD (to one iso file) on your hard-disk is to:
[LIST=1]
[*]Enable [medibuntu repository](https://help.ubuntu.com/community/Medibuntu)
[*]Install w32(0r 64)codecs
[*]Use the <right-click> copy as file (iso) method you tried earlier (one reason it may no have worked is if you don't have the w32(or 64)codecs installed)
[/LIST]

---

### Post by boof1988 on 2009-03-27
> **tom56 said:**
> i expect either the disc is scratched or you need to [color="red"]install libdvdcss2[/color] (or both)
[https://help.ubuntu.com/community/restrictedformats/playingdvds#ubuntu%208.10%20(i386,%20amd64](https://help.ubuntu.com/community/restrictedformats/playingdvds#ubuntu%208.10%20(i386,%20amd64))

+1

---

### Post by fidibidabah on 2009-03-27
or alternatively the dvd is from universal or warnerbrothers... in which case it's possible neither one of those things would be the problem, depending on the drm used...

---

### Post by HotShotDJ on 2009-03-27
> **redonwhite said:**
> but i chose copy dvd and i guess when it ask me to insert the blank dvd ill just ignore it and steal my ISO from the folder haha.  Can anyone confirm that im doing this right that is familiar with k3b. :confused:

Why didn't you just choose "Only Create Image" from the DVD Copy dialogue?  Then click on the "Image" tab to define the path and name of the ISO you want to create.  You don't have to trick it into doing what you want... just select the appropriate options (they are not hidden or given obscure names).  See attached screenshot.

---

### Post by logos34 on 2009-03-27
> **HotShotDJ said:**
> :confused:

Why didn't you just choose "Only Create Image" from the DVD Copy dialogue?  Then click on the "Image" tab to define the path and name of the ISO you want to create.  You don't have to trick it into doing what you want... just select the appropriate options (they are not hidden or given obscure names).  See attached screenshot.

+1

But what's odd is this: k3b can copy the image where dd fails--even in the case of encrypted content (and the "Ignore Read errors" advanced option makes no diff -- which is what protected multimedia discs use to defeat dd).  I'm guessing that's what the problem was.  For instance, I just tried to copy the iso of Neil Young Greendale DVD with dd command but it failed right off.  However k3b starts up just fine no matter what setting.

Add: and that is precisely what the problem appears to be...I just tried dd_rescue to rip the iso (without error check) and it goes fine. 

There's an interesting thread on how to do this here:

[http://ubuntuforums.org/showthread.php?t=1010331&page=2](http://ubuntuforums.org/showthread.php?t=1010331&page=2)

---

