---
title: "On CD/Multimedia Collection Capture and Storage"
date: 2005-12-30
forum: General Help
---

### Post by stardotstar on 2005-12-30
I have just unpacked some boxes from storage: my entire "original" CD collection, and being in a somewhat ruthless mood, I have taken the discs out of each case and thrown away the box, inserts and all (the reasoning being that the disc is for listening and thus data and not for reading and therefore the analogue component superfulous - there were notable exceptions of course (my whole Ween Collection, some Pink Floyd etc - which I just had to keep!) thus ending up with a large stack of discs and a massive space saving... and a new project...

Finding that Sound Juicer automatically picks up all the discs accurately I am considering taking the next step and ripping the entire collection to some mass storage with appropriate indexing- searchable etc. and setting up some kind of home AV system driven by a linux server.

I'm sure there are some threads on this kind of thing (not to mention articles I am reading in LJ) and I am currently searching, but:

I want to discuss how to determine if there are discs that are damaged and thus not capturable without attempting to repair them.  Many of them have scratches and blemishes from years of use and storage on a multitude of players.

Is there a tool that fast scans a disc and checks if there is possible damage on certain tracks? 

Without listening to each and every disc - a momumental task!

Thoughts and pointers to threads that I have clearly not bothered to sufficiently search for appreciated :)

---

### Post by GrammatonCleric on 2005-12-30
If you are planning on using a tool to scan the CD's why not just try to rip/encode them?  If it works...then you're good, if not then note that CD needs to be repaired in some fashion and continue to the next CD? 

For discs that are really scratched up you may want to look at something like the [**Aleratec DVD/CD Disc Repair Plus**]("http://www.amazon.com/gp/product/B0002A9SJ2/sr=1-1/qid=1135972255/ref=pd_bbs_1/103-2926047-0655034?%5Fencoding=UTF8") to repair them.

- GC

---

### Post by stardotstar on 2005-12-31
Thanks Cleric I didn't know if the ripping process would work that way - and it seems to be working great.

I am continuing to break my entire collection down to Ogg.  Next step some kind of home entertainment system based on Ubuntu.

---

### Post by GrammatonCleric on 2006-01-01
There are several threads on how to build a MYTHTV system. Unless you are planning adding on tivo like functionality just ignore the PVR configuration and setup.

I've setup something like what you are looking to do....but I was forced into using Windows for the server OS.  I came to the conclusion that I could spend a ton of cash trying to make a PC silent so the fan and HD noise wouldn't drive me crazy.  I opted to split the the functionality into two systems.  One system would be a server (noisy) that would host my music, video collections and record TV (thus replacing my TIVO) that would reside in a room away from my stereo/tv.  The second would be a stateless device (no noise) that would reside in my stereo cabinet and stream both music and video from the server via wireless (802.11g).  After looking around  the **[Buffalo Link theater]("http://www.buffalotech.com/products/product-detail.php?productid=96&categoryid=18")**  looked to be the best choice for me since it supported just about every file type that I use.
 

 [LEFT][FONT=Frutiger-Bold, sans-serif][SIZE=2]**Video Files: **[FONT=Frutiger-Light, sans-serif]dat, mpg, mpe, mpeg, m2v, m1v, vob, avi, asf, divx,[/FONT][/SIZE][/FONT][/LEFT]
   [LEFT][FONT=Frutiger-Light, sans-serif][SIZE=2]xvid, rmp4, mp4, vro, m4v, m2p, hnl, wmv, wmv hd, divx hd[/SIZE][/FONT][/LEFT]
   [LEFT]
[/LEFT]
   [LEFT][FONT=Frutiger-Bold, sans-serif][SIZE=2]**Audio Files: **[FONT=Frutiger-Light, sans-serif]mp3, mp2, ogg, wav, aac, wma, pls, m4a, ac3,[/FONT][/SIZE][/FONT][/LEFT]
   [LEFT][FONT=Frutiger-Light, sans-serif][SIZE=2]mp1, mpa, asf, m3u[/SIZE][/FONT][/LEFT]
   [LEFT]
[/LEFT]
   [LEFT][FONT=Frutiger-Bold, sans-serif][SIZE=2]**Picture Files: **[FONT=Frutiger-Light, sans-serif]jpg, gif, bmp, tif, png[/FONT][/SIZE][/FONT][/LEFT]
   [LEFT]
[/LEFT]
   [LEFT]
[/LEFT]
   [LEFT]Everything works great the only down site is that I have to use Windows for the Server since the Link theater's server software only works on either Windows or OS X.   I should mention that the server has no keyboard, mouse or monitor.  I've enabled RDP (terminal services) on the server and then use rdesktop from my ubuntu workstation and laptop to administer it.

- GC
  [/LEFT]

---

### Post by stardotstar on 2006-01-02
Awesome, I am going to do some research since we are building a new house and the kind of noise and streaming issues you mention are critical to the success of the AV side of the project!

BTW WRT the use of SoundJuicer to determine if there are errors on the discs I am finding that the software is not nearly as bothered by damage as any CD player I have ever come across - it would seem that it is able to read and reread till it gets enough data to proceed at the level of compression  being used - I am using ogg of course.  However it seems that when Sound Juicer really does get stuck it hangs and the CD drive is left doing wind up/wind down cycles and the software does not repsond.

I have looked at the bug reports and nothing there - any ideas?  I was expecting and error or timeout of some kind...

Thanks for the reply... :)  I will def check out the buffalo

Will

---

### Post by GrammatonCleric on 2006-01-02
For CD ripping I perfer to use GRIP.  If a CD is scratched I think that cdparanoia does a much better job scratch detection/repair. Here's a thread that talks about how to install it...

[http://ubuntuforums.org/showthread.php?t=99115&highlight=grip]("http://ubuntuforums.org/showthread.php?t=99115&highlight=grip")

My GRIP settings are a little extreme and may take a little longer but the quaity is better.

[B]My Encoder Commandline settings:
[/B]
```

-m j --clipdetect --preset extreme -q 0 --vbr-new -V 0 %w %m

``` 
If you choose to use GRIP under the ID3 tab make sure you add check marks next to both ID3 tag add settings.  Also you may have to play with the "Rip file fomat" and Encode file format output settings, mine are....

**Rip file format:**

```
~/Audio/ripped/%A/%d/%t_%n.%wav
``` 
**Encode file format:**

```
~/Audio/ripped/%A/%d/%t_%n.%x
``` 
After the tracks are ripped the output should look as follows.

```
/home/yourdir/Audio/ripped/artist/album/01_tracktitle.mp3
``` 
Grip supports OGG all you need to do is under the ENCODE tab select oggenc as the encoder then change the "Encoder command-line" to...

```
-q 8 -o %m -a %a -l %d -t %n -d %y -G %g  %w
``` 
FYI.. the higher the "-q" the better the quality. The "-q" option does have a max range from -1 (low quality) to 10 (highest quality).


Just as a recommedation, before you've encoded your whole CD collection into ogg think about the chance that you might ever...get an ipod, mp3 playing car stereo, share your collection with friends, etc. consider that many devices do not read or decode the ogg format.  Once you commit to an entire collection encoded as ogg and you do plan on doing any of the above you'll have to re-encode your music to a format that those devices can decode (i.e. mp3) before you can use it.  

Hope this helps.

-GC

---

### Post by stardotstar on 2006-01-02
Thanks for all that and the useful link - I have got GRIP now and begun playing with some of the multimedia settings and run into problems...

When I insert discs they launch SJ so I went to gnome-volume-properties and turned off the auto launch setting for SJ.

However even when I set the GRIP configuration for the CD to /media/cdrom it does not see the drive/disc...

If I look at mtab there does not appear to be a mount for the CD...

```
/dev/hda3 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
usbfs /proc/bus/usb usbfs rw 0 0
tmpfs /lib/modules/2.6.12-10-386/volatile tmpfs rw,mode=0755 0 0
/dev/hda1 /media/win ntfs rw,umask=0222 0 0
/dev/hda5 /media/qstore vfat rw 0 0
tmpfs /dev tmpfs rw,size=10M,mode=0755 0 0

```

The above is the mtab output with the audio cd mounted and playable by SJ.

Not sure why GRIP has trouble with seeing the volume and this means I am not clear on where and how the CD is mounted - I would have thought I could use a terminal to browse to /media/cdrom or /media/cdrom0 and ls it - but it is empty.

When I try to tackle it in Nautilus it get the error:

> 
"cdda:///dev/hdc" is not a valid location.

So I think I am needing some more help and enlightenment on how these things work.

I appreciate your detailed thoughts on the encoding format - perhaps a more universal media like mp3 is desirable - I will do more reading before I commit the entire catalogue - I have done over 50 discs already!!!

Will

---

### Post by GrammatonCleric on 2006-01-02
Audio CD's are not mounted per se.  Try this.  In your cd/dvd rom put a data disc (i.e. Ubuntu install disc).  Once it is mounted and you see an icon on your desktop open a terminal and type "df"...minus the quotes.  You should see something like information below.  


```


gcleric@ares:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             109G  6.6G  103G   7% /
tmpfs                 507M     0  507M   0% /dev/shm
tmpfs                 507M   13M  494M   3% 
[COLOR=Red]**/dev/hdf               38M   38M     0 100% /media/cdrecorder**[/COLOR]
//apollo/m$           306G  183G  123G  60% /media/music
//apollo/d$            79G   36G   44G  45% /media/videos
//apollo/i$            77G   67G  9.5G  88% /media/data



``` 

The drive in bold red is my DVDRW.  Using the above either /dev/hdf or /media/cdrecorder should work in GRIP as the CD Rom device.

Let me know if that works.

- GC

---

### Post by stardotstar on 2006-01-02
I get with a data CD:

```
wparker@gecko:/media $ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3             5.7G  3.5G  1.9G  66% /
tmpfs                 506M  4.0K  506M   1% /dev/shm
tmpfs                 506M   13M  494M   3% /lib/modules/2.6.12-10-386/volatile
/dev/hda1              25G   22G  2.6G  90% /media/win
/dev/hda5             6.9G  2.4G  4.5G  36% /media/qstore
/dev/hdc              575M  575M     0 100% /media/cdrom0

```

used /dev/hdc in GRIP and all GOOD :)

Thanks.

---

