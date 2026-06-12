---
title: "opening a dvd"
date: 2006-01-29
forum: Desktop Environments
---

### Post by Vinger on 2006-01-29
Hello,

i've installed kubuntu the afternoon...
In Ubuntu, everything worked great, but i wanted to test KUbuntu...

This is my problem...

i want to watch a DVD with Kaffeine, but i get the error:
> 
Could not read title information for DVD.

With dvdshrink, i get the error
> 
Dvdshrink encountered an error and cannot continue
failed to read file d:\

A normal audio cd is no problem...

grz

---

### Post by deity_me on 2006-01-29
i'm no linux guru but d:\ ??
i dont think that exists in the linux world unless you're running dvdshrink under wine

---

### Post by Vinger on 2006-01-29
yes... dvdshrink running under wine...

but kafeine doesn't play my dvd also...

---

### Post by deity_me on 2006-01-29
can you mount the DVD and cd into the folder and take a look around?

just thinking its not being mounted properly

---

### Post by Neo Ex on 2006-01-29
Make sure that the DVD is mounted properly (you can try mounting it manually). If you encounter this problem again, try installing kaffeine-xine and selecting the Xine engine in Settings -> Playback engine -> Kaffeine (I think in English it would be so).
I've only tried to play just one DVD a few days ago, but it worked for me.
But I've read on this forum that somebody has problems with DVD automounting: maybe the problem it's just this.

---

### Post by Vinger on 2006-01-30
Tx for the answers...

I see the DVD on my desktop-screen. When i open it in conqueror, i can see all the files...

I'll try to remount it this evening. (I'm at work now...)

grz

---

### Post by Vinger on 2006-01-30
I tried to mount DVD manually 
>  koen@Kubuntu:~$ mount /dev/hdc
mount: blok-apparaat /dev/hdc is schrijf-beveiligd, alleen-lezen aankoppelen
mount: /dev/hdc al aangekoppeld of /media/cdrom0 bezig
mount: volgens mtab, is /dev/hdc al aangekoppeld op /media/cdrom0

This is: 
mount: /dev/hdc is write protected, mount read only
mount: /dev/hdc is already mounted or /media/cdrom0 is busy
mount: mtab says: /dev/hdc is already mounted on /media/cdrom0

Nothing changes...
I can't watch using caffeine.
I reinstalled Kubuntu, but that doesn't make a difference...

I read in another forum about automounting dvd - [http://www.ubuntuforums.org/showthread.php?t=89224&page=2&highlight=dvd+automounting](http://www.ubuntuforums.org/showthread.php?t=89224&page=2&highlight=dvd+automounting)
I tried that but this is the error i get in Kaffeine then:
> 
There were no decoders found to handle the stream, you might need to install the corresponding plugins


I read about the file /etc/fstab, so i post it here...
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda3       /media/hda3     ext3    defaults        0       2
/dev/hda5       /media/hda5     ntfs    defaults        0       0
/dev/hdb1       /media/hdb1     ntfs    defaults        0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


---

### Post by DrBair on 2006-02-01
To the best of my knowledge, dvdshrink cannot open a DVD under wine. You need to first rip it to an image. dvdbackup would be a preferred program for ripping to disc to an image.

---

### Post by localzuk on 2006-02-01
Do you have the libdvdcss2 package installed? Take a look at ubuntuguide.org or the 'automatix' package (search these forums).

---

### Post by Vinger on 2006-02-03
Tx to automatix, my dvd is playing. Dvdshrink has no problems...

But i have another problem. When i'm playing a dvd in mplayer, i have no sound... 

Playing audio-cd's is no problem with amarok. in kscd, i have also no sound...

anyone an idea?

---

### Post by Neo Ex on 2006-02-03
For the sound problem in KsCD, try enabling the direct digital playback.

---

### Post by Vinger on 2006-02-04
Where do i have to enable that digital playback? 
In the mixer or the program? i don't find it...

---

### Post by Vinger on 2006-02-04
I noticed that in loud parts of the dvd, i hear a silent noice. (fe. when there's loud music in the film, i hear the music very silent...)
In other players (like Kaffeine) i hear the sound normal, but there the video isn't clear.

---

### Post by Neo Ex on 2006-02-04
[QUOTE=Vinger]Where do i have to enable that digital playback? 
In the mixer or the program? i don't find it...[/QUOTE]
KsCD -> Extra -> Settings -> Use the digital playback (it's under the CD-Rom device; to do this you have to stop the playback of the CD, if you are listening to one).

---

### Post by Vinger on 2006-02-06
Ok, tx!

I changed that, and KsCD played...
I searched for similar settings in Mplayer, and that program is also well functionning... :-)

---

