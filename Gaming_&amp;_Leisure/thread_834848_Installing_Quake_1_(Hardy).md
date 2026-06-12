---
title: "Installing Quake 1 (Hardy)"
date: 2008-06-19
forum: Gaming &amp; Leisure
---

### Post by Mako Eyes on 2008-06-19
I don't mean to flog a dead horse here, as there are countless threads here asking the same question and all of them seem solved. However, I'm having trouble following the instructions within.

Basically, what I intend to do is install Quake 1 from my Ultimate Quake pack on Ubuntu 8.04. Something I absolutely must get out of the way right now is the fact that I do not want to play Quake using hardware acceleration. I am unable to obtain proper hardware accelerated drivers, so things like glquake are not really my concern. Windows runs Quake in software mode just fine, am I right to assume Ubuntu would? I sure hope so.

Anyway, as I have said, I find the various threads in this form a tad difficult to follow. I'm still a bit new to Linux, but I'm learning quite fast. I have run across guides such as [The Linux Quake How-To](http://tldp.org/HOWTO/Quake-HOWTO.html) (along with its [predecessor](http://webpages.mr.net/bobz/howto/)), but I find the instructions very vague and I'm running into problems which aren't mentioned in the troubleshooting guide and Google isn't really turning up any results.

So, I ask, is there any guide online (or can someone provide one) that gives step-by-step instructions on how to install Quake in Ubuntu Hardy that will run in software mode?

Many thanks. If you need more information, just say so.

---

### Post by th3t1nm4n on 2008-06-20
Hi, I looked at your previous threads and you might want to look into this to get your driver working: [http://ubuntuforums.org/showthread.php?t=190133&highlight=ATI+X800](http://ubuntuforums.org/showthread.php?t=190133&highlight=ATI+X800) , or look into using a script for Debian and Ubuntu called "envy" - but look into that first to make sure your card would be supported by it, I know that some ATI cards give it issues. (my old laptop did)

Software quake, sounds like you'd want either SDL Quake (which is a real pain) or TyrQuake.

First - Download TyrQuake
[http://sourceforge.net/project/downloading.php?group_id=124987&use_mirror=internap&filename=quake-lq-1.0.1.tgz&95114630](http://sourceforge.net/project/downloading.php?group_id=124987&use_mirror=internap&filename=quake-lq-1.0.1.tgz&95114630)
Extract it, it will make a folder called "quake".
Find your Quake 1 CD.
Copy the "ID1" folder into the new "quake folder"
Go into the "quake" folder and rename "ID1" to "id1"
Go into "id1" and rename "PAK0.PAK" to "pak0.pak" and rename "PAK1.PAK" to "pak1.pak" (Linux is case-sensitive)
Open up a terminal and go to the quake directory
(cd ~/Desktop/quake)
Run the tyrquake binary
(./tyr-quake)
And hope that your audio works because mine doesn't with TyrQuake :/

<--Edit--> I just got DarkPlaces working and there's an SDL binary that might work for you, I get audio with it on Hardy.
DL it: [http://icculus.org/twilight/darkplaces/files/darkplacesengine20071120.zip](http://icculus.org/twilight/darkplaces/files/darkplacesengine20071120.zip)
Extract it.
Put that "id1" folder from the steps I had before into that folder.
Run it with "./darkplaces-linux-686-sdl"

---

### Post by Mako Eyes on 2008-06-20
> **th3t1nm4n said:**
> Hi, I looked at your previous threads and you might want to look into this to get your driver working: [http://ubuntuforums.org/showthread.php?t=190133&highlight=ATI+X800](http://ubuntuforums.org/showthread.php?t=190133&highlight=ATI+X800) , or look into using a script for Debian and Ubuntu called "envy" - but look into that first to make sure your card would be supported by it, I know that some ATI cards give it issues. (my old laptop did)

Software quake, sounds like you'd want either SDL Quake (which is a real pain) or TyrQuake.

First - Download TyrQuake
[http://sourceforge.net/project/downloading.php?group_id=124987&use_mirror=internap&filename=quake-lq-1.0.1.tgz&95114630](http://sourceforge.net/project/downloading.php?group_id=124987&use_mirror=internap&filename=quake-lq-1.0.1.tgz&95114630)
Extract it, it will make a folder called "quake".
Find your Quake 1 CD.
Copy the "ID1" folder into the new "quake folder"
Go into the "quake" folder and rename "ID1" to "id1"
Go into "id1" and rename "PAK0.PAK" to "pak0.pak" and rename "PAK1.PAK" to "pak1.pak" (Linux is case-sensitive)
Open up a terminal and go to the quake directory
(cd ~/Desktop/quake)
Run the tyrquake binary
(./tyr-quake)
And hope that your audio works because mine doesn't with TyrQuake :/

<--Edit--> I just got DarkPlaces working and there's an SDL binary that might work for you, I get audio with it on Hardy.
DL it: [http://icculus.org/twilight/darkplaces/files/darkplacesengine20071120.zip](http://icculus.org/twilight/darkplaces/files/darkplacesengine20071120.zip)
Extract it.
Put that "id1" folder from the steps I had before into that folder.
Run it with "./darkplaces-linux-686-sdl"

Excellent, the first method works like a charm. I even have audio. I can't hear CD audio though, but the drive *is* attempting to play audio. Any advice regarding that?

I'm trying to make a shell script containing the "./tyr-quake" command so that I can so that I can put a shortcut icon in the Applications menu. When running the script from Terminal it runs just as I would like it to, but the shortcut icon (with the command "*sh /<directory>/quake.sh*") doesn't do anything when clicked. What's that about? I also want to make a [custom icon](http://library.galciv2.com/mvlib/ss/quakefullview.jpg) for this menu entry. How do I do this?

As for the drivers, I appreciate you trying to help but it's just a lost cause. I have an X800 and they're known to overheat severely when running on the Linux Catalyst drivers.

Thank you very much for your assistance!

---

### Post by th3t1nm4n on 2008-06-20
Well, here's how I would go about making that script to run quake.
```
#!/bin/bash
# /home/user/bin/quake/quake - a script for running tyr-quake
cd /home/user/bin/quake
./tyr-quake
```
Then I'd save that and "chmod +x" it so that it's executable.

For the launcher icon in the menu, you should be able to make one within alacarte (in GNOME), that's "alacarte".

---

### Post by Mako Eyes on 2008-06-20
> **th3t1nm4n said:**
> Well, here's how I would go about making that script to run quake.
```
#!/bin/bash
# /home/user/bin/quake/quake - a script for running tyr-quake
cd /home/user/bin/quake
./tyr-quake
```
Then I'd save that and "chmod +x" it so that it's executable.

For the launcher icon in the menu, you should be able to make one within alacarte (in GNOME), that's "alacarte".

Perfect, it's excellent now. Thanks a million! Is there anything you can help me with in regards to the CDaudio?

EDIT: Actually, I don't have an analog CDaudio cable. Could this be it? Windows always did it fine with old games, but I'm not sure about Linux. That's probably why I overlooked it.

---

### Post by th3t1nm4n on 2008-06-22
By CDaudio do you mean the thing in Quake where you can play music off of a CD, or something outside of Quake?

---

### Post by Mako Eyes on 2008-06-22
> **th3t1nm4n said:**
> By CDaudio do you mean the thing in Quake where you can play music off of a CD, or something outside of Quake?

Yeah, Quake (like most of those great classic shooters of its era) has a redbook soundtrack on its CD. It plays along with the game or, if you like, you can put your own music in there and play along.

Why do you ask?

---

### Post by th3t1nm4n on 2008-06-22
I wasn't sure if you were bringing in a different topic or not.

I know that Quake has that, I've never used it though, I use a media player to play music off my HDD when I'm ingame, I try to keep my game and music discs in the best shape so I copy them all to my computer, that way they're less likely to get scratched and I can always re-copy them if I end up with something bad happening to my computer.

I'm not sure if that Quake binary is current enough to be able to do that with Ubuntu 8.04, I'm sure it worked on older Linux systems, but it seems that a lot of older games (even Quake 3) have audio issues that you run into with running them on current Linux desktops.

Sorry I can't help you there.

---

### Post by Mako Eyes on 2008-06-23
> **th3t1nm4n said:**
> I'm not sure if that Quake binary is current enough to be able to do that with Ubuntu 8.04, I'm sure it worked on older Linux systems, but it seems that a lot of older games (even Quake 3) have audio issues that you run into with running them on current Linux desktops.

Sorry I can't help you there.

Darn.. Oh well, thanks for your help!

EDIT: Actually, what would be the standard procedure for doing that? I'm curious now. Is there a way to extract an ISO from my Quake CD and get the game to run the music from that somehow?

EDIT 2: I see there is a command line switch for tyr-quake called "*[-cddev](http://tldp.org/HOWTO/Quake-HOWTO-2.html#ss2.2)*." Is there any way to use that with the disc image?

EDIT 3: Using: ```
$ sudo mount ~/Games/quake/disc/Winquake.iso -t iso9660 -o loop=/dev/loop0

``` to mount *appears* to work (ie: I get no error messages, but the output seems to imply that I'm missing something):

```
$ sudo mount -t iso9660 ~/Games/quake/disc/Winquake.iso -o ro.loop=/dev/loop0
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
```

Here's what happens when I try to run Quake using it: 

```
$ ./tyr-quake -cddev /dev/loop0 -cdaudio -fullscreen -width 1280 -height 1024
Playing registered version.
Console initialized.
UDP Initialized
Exe: 11:35:41 Jul  2 2007
16.0 megabyte heap
Using XFree86-VidModeExtension Version 2.2
4252k surface cache
VID: shared memory id=15138833, addr=0xb67f4000
VID: shared memory id=15171602, addr=0xb62f4000

Sound Initialization
Sound sampling rate: 11025
**CDAudio_Init: open of "/dev/loop0" failed (13)**
Callback: in_dgamouse ON
Callback: _windowed_mouse OFF
3 demo(s) in loop
========Quake Initialized=========
```

I assume "(13)" is an error classification? Research (and by that I mean Google) says that an Error 13 in Linux is a "Permission Denied" error, but here's what happens when I run the command using sudo:

```
$ sudo ./tyr-quake -cddev /dev/loop0 -cdaudio -fullscreen -width 1280 -height 1024
Playing registered version.
Console initialized.
UDP Initialized
Exe: 11:35:41 Jul  2 2007
16.0 megabyte heap
Using XFree86-VidModeExtension Version 2.2
4252k surface cache
VID: shared memory id=15302673, addr=0xb6792000
VID: shared memory id=15335442, addr=0xb6292000

Sound Initialization
Sound sampling rate: 11025
[B]CD Audio Initialized
CDAudio_Init: No CD in player.
ioctl CDROMVOLCTRL failed[/B]
Callback: in_dgamouse ON
Callback: _windowed_mouse OFF
3 demo(s) in loop
========Quake Initialized=========
```


So I guess there's no way to do it then, huh? It's not that big of a deal, I just like creepy music to go along with my Quaking. Trying to figure this out makes for good practice too, I guess.

Then again, I'm probably thinking this is way easier than it is in reality.

---

### Post by RIchard James13 on 2008-06-23
Quake tells the CD-ROM drive to play a particular track. The audio is then sent along the analog cable to your sound card. In most modern systems there is no cable because they use the ATA interface cable to read direct from the CD, that is how some modern media players work without that cable. If you don't have that cable and your game is using that to play the music then you won't hear anything.

The only real alternatives are 
a) Rewrite the game so it pays the music differently
b) Play the music via a media player at the same time as playing the game

---

### Post by Mako Eyes on 2008-06-24
> **RIchard James13 said:**
> Quake tells the CD-ROM drive to play a particular track. The audio is then sent along the analog cable to your sound card. In most modern systems there is no cable because they use the ATA interface cable to read direct from the CD, that is how some modern media players work without that cable. If you don't have that cable and your game is using that to play the music then you won't hear anything.

The only real alternatives are 
a) Rewrite the game so it pays the music differently
b) Play the music via a media player at the same time as playing the game

I would like to add the music plays fine in Windows (even for other old games, such as Age of Empires), without the analog cable. However, this isn't Windows and I guess this sort of thing must be OS-specific instead of game-specific.

Oh well, thanks anyway.

---

### Post by Sleaka J on 2008-06-24
I have exactly the same problem playing CD Audio (redbook) in Quake 2 under Linux. Tried using Linux versions of Quake 2 and installed Quake 2 using Wine, same result. DVD drive light comes on indicating that CD audio should be playing, however it doesn't play.

Under Windows, Quake 2 plays the CD audio perfectly. I DO have the cable from my soundcard to the DVD-Drive.

The same CD plays in Rhythmbox perfectly, just won't play in-game.

It's definitely a Linux thing. I've posted 2 threads in separate sections on the Ubuntu forums asking for help and got no responses. Since I got no help, I play Quake 2 in Windows where it works.

---

### Post by RIchard James13 on 2008-06-26
> **Sleaka J said:**
> The same CD plays in Rhythmbox perfectly, just won't play in-game.

That seems to imply that the code for Quake 2 is broken or the library it is using (SDL) is broken. It is quite possible for SDL to be broken considering that no new games use CD AUDIO they all use compressed files, so no-one will test to see if it still works. I might check tonight and see if SDL can still play CD AUDIO.

OK I tried a simple SDL program from the SDL wiki and it says the following about my 18 track CD which plays fine in rythmbox.

Name: /dev/scd0
Tracks: 0

So Quake will see no tracks and play no songs. Maybe this is due to a difference in the way CD-ROM drives are handled under the newer Kernals? Time to send a bug report to someone, who I don't know yet, the Ubuntu or Debian maintainer of the SDL package or maybe the SDL people if the problem manifests itself in a non Debian Distro.

Nope the problem occurs in Slackware 11 with a 2.6 Kernal.

---

### Post by trilobitomorph on 2009-01-28
yeah, works for me just fine too, only i can't get it full screen..
any hints?

---

