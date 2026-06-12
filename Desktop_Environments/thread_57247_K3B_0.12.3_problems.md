---
title: "K3B 0.12.3 problems"
date: 2005-08-15
forum: Desktop Environments
---

### Post by Shamanix on 2005-08-15
Can't fins K3B 0.12.3 .deb file.
Can't install K3B 0.12.3 from source, getting this message in the end after tryins to "./config": 

checking for KDE... 
configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!

Can anyone help please?

---

### Post by PeP on 2005-08-15
[QUOTE=Shamanix]Can't fins K3B 0.12.3 .deb file.
Can't install K3B 0.12.3 from source, getting this message in the end after tryins to "./config": 

checking for KDE... 
configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!

Can anyone help please?[/QUOTE]

you need the headers from the kde source code: install kdebase-dev.

Just a hint if you don't know what a header is and why you didn't have it, use the k3b provided by ubuntu or at least try the version that is in breezy. Do you really need the 0.12.3 k3b?

---

### Post by SGC on 2005-08-15
Try installing this package:
sudo apt-get install kdelibs4-dev

---

### Post by PeP on 2005-08-15
[QUOTE=SGC]Try installing this package:
sudo apt-get install kdelibs4-dev[/QUOTE]

whaha!
I hadn't filed my post for 1 mn that you reply (I guess) more accurately than me.

Shamanix: theses two answers are not so different that it first seems to: kdebase-dev includes (depends on to be exact ...) kdelibs4-dev

---

### Post by SGC on 2005-08-15
[QUOTE=PeP]whaha!
I hadn't filed my post for 1 mn that you reply (I guess) more accurately than me.

Shamanix: theses two answers are not so different that it first seems to: kdebase-dev includes (depends on to be exact ...) kdelibs4-dev[/QUOTE]
 Hi PeP, I was leaving the page open for a few minutes. I saw your post after posting mine.

---

### Post by PeP on 2005-08-15
[QUOTE=SGC]Hi PeP, I was leaving the page open for a few minutes. I saw your post after posting mine.[/QUOTE]
Hi SGC
I don't doubt about this, I looked at the time of your post ;-).

Anyway, are you sure that the kdelibs headers are enough to compile (I have no clue about that, so kdebase-dev was a safe bet)

---

### Post by SpEcIeS on 2005-08-15
Just a thought, because I like to compile my own software, unless it is currently available, when I install a package the dev package is also installed. Keeps things on the up and up, however not everyone has the HDD space. These days lots do. :)

---

### Post by PeP on 2005-08-15
SpEcIeS: you must be some kind of frustrated gentoo user then ;-)

---

### Post by SpEcIeS on 2005-08-15
[QUOTE=PeP]SpEcIeS: you must be some kind of frustrated gentoo user then ;-)[/QUOTE]
Actually no, but I am interested in trying [COLOR=DarkOrchid]Gentoo[/COLOR] oneday. Looks nice, but Ubuntu is pretty good. :)

---

### Post by SGC on 2005-08-15
[QUOTE=PeP]Anyway, are you sure that the kdelibs headers are enough to compile [/QUOTE]

No I'm not sure about that, but I can compile kde programms without kdebase-dev

---

### Post by PeP on 2005-08-15
[QUOTE=SpEcIeS]Actually no, but I am interested in trying [COLOR=DarkOrchid]Gentoo[/COLOR] oneday. Looks nice, but Ubuntu is pretty good. :)[/QUOTE]
I switched from gentoo a couple of month ago, it was a nice learning experience, but I really missed the possibility to install a new program I need in a couple of minutes.

---

### Post by SpEcIeS on 2005-08-15
[QUOTE=PeP]I switched from gentoo a couple of month ago, it was a nice learning experience, but I really missed the possibility to install a new program I need in a couple of minutes.[/QUOTE]
More often that not, I have had better success with software that is compiled on my own system. A friend of mine indicated that 
[COLOR=DarkOrchid]Gentoo[/COLOR] was probably what I was looking for, however, like I said before, Ubuntu is really nice. :grin: As far as being up to date, they really work hard at it, but I really have an itch to build the latest greatest all of the time. Packages can be a pain in the backside, but you are right, it does offer fast access to what you need.

Currently I am attempting to build a [COLOR=Red]deb[/COLOR] package for k3b-0.12.3. The 0.12.2 works nice, but like I indicated above, the latest greatest. Besides lets move out those bugs. :)

---

### Post by PeP on 2005-08-15
[QUOTE=SpEcIeS]
Currently I am attempting to build a [COLOR=Red]deb[/COLOR] package for k3b-0.12.3. The 0.12.2 works nice, but like I indicated above, the latest greatest. Besides lets move out those bugs. :)[/QUOTE]
 

if you compile everything as a .deb package, why not make a deb repository.
Just call it morethanexperimental ;-) or experimental_backports if you're in Hoary

---

### Post by PeP on 2005-08-15
I am compiling amarok1.3 ...
I love the warning:> ==================================
 ===  AMAROK WILL NOT BE BUILT  ================================================
 ==================================
 =
 = No suitable multimedia framework was detected. You need to install at least
 = one of the supported frameworks as detailed in the amaroK README.
 = If you are thinking, 'I have aRts you stupid configure!', then you probably
 = need to install kdemultimedia-devel. 

it is both clear and funny :-)

---

### Post by SpEcIeS on 2005-08-15
Yeah that one is pretty funny. :)

I do not always compile deb packages, although some are, however mostly I just compile, make, and make install. Building the deb packages can be a pain, well at least with Gnome. I was running into scrollkeeper issues when building deb packages for gnome.  Eh..  whatever.. :) Probably something I missed out on, but now I am using KDE 3.4.2, which I find runs much quicker.

Now back to the k3b 0.12.3 build. Seems that I need the dev for ffmpeg, which does not come in the repo. Off to build that one and install it over the debber.  :grin:

---

### Post by Shamanix on 2005-08-16
Thanks guys, worked fine now. Needed kdelibs4 for "./config" and kdebase_dev for "make". The reason why i wanted a new version is because, when i try to burn my bin/cue images the burning failes on various places (6%, 18% is what i have seen)... :P got me mad!! lol

The burning on CD-RW works fine, also simulation works... Don't understand this.

btw, yes, i'm new to linux, used for only 1-2 weeks (Kubuntu 5.04), and i LOVE it :D my 7 year old dream finaly came true :P

Here's the log:

System
-----------------------
K3b Version: 0.12

KDE Version: 3.4.0
QT Version:  3.3.3
Kernel:      2.6.10-5-k7
Devices
-----------------------
_NEC DVD_RW ND-3520AW 3.04 (/dev/hdb, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD-R DL; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-R Dual Layer Sequential; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96R; RAW/R96R; Restricted Overwrite]

SONY DVD RW DRU-500A 2.1a (/dev/hda, ) at /media/cdrom1 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD+R; DVD+RW] [DVD-ROM; DVD-R Sequential; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96R; RAW/R96R; Restricted Overwrite]
Used versions
-----------------------
cdrdao: 1.1.9

cdrdao
-----------------------
Cdrdao version 1.1.9 - (C) Andreas Mueller <andreas@daneb.de>
  SCSI interface library - (C) Joerg Schilling
  Paranoia DAE library - (C) Monty
Check [http://cdrdao.sourceforge.net/drives.html#dt](http://cdrdao.sourceforge.net/drives.html#dt) for current driver tables.
Using libscg version 'schily-0.8'
/dev/hdb: _NEC DVD_RW ND-3520AW Rev: 3.04
Using driver: Generic SCSI-3/MMC - Version 2.0 (options 0x0010)
Burning entire 79 mins disc.
Starting write at speed 32...
Process can be aborted with QUIT signal (usually CTRL-\).
WARNING: No super user permission to setup real time scheduling.
Turning BURN-Proof on
Executing power calibration...
Power calibration successful.
Writing track 01 (mode MODE1_RAW/MODE1_RAW )...
Wrote 1 of 659 MB (Buffers 100%  91%).
Wrote 2 of 659 MB (Buffers 100%  25%).
Wrote 3 of 659 MB (Buffers 100%   7%).
Wrote 4 of 659 MB (Buffers 100%  76%).
Wrote 5 of 659 MB (Buffers 100%  41%).
Wrote 6 of 659 MB (Buffers 100%  10%).
Wrote 7 of 659 MB (Buffers 100%  45%).
Wrote 8 of 659 MB (Buffers 100%  52%).
Wrote 9 of 659 MB (Buffers 100%  17%).
Wrote 10 of 659 MB (Buffers 100%  34%).
Wrote 11 of 659 MB (Buffers 100% 100%).
Wrote 12 of 659 MB (Buffers 100%  27%).
Wrote 13 of 659 MB (Buffers 100%  30%).
Wrote 14 of 659 MB (Buffers 100%  99%).
Wrote 15 of 659 MB (Buffers 100%  69%).
Wrote 16 of 659 MB (Buffers 100%  24%).
Wrote 17 of 659 MB (Buffers 100%  19%).
Wrote 18 of 659 MB (Buffers 100%  76%).
Wrote 19 of 659 MB (Buffers 100%  37%).
Wrote 20 of 659 MB (Buffers 100%  11%).
Wrote 21 of 659 MB (Buffers 100%  80%).
Wrote 22 of 659 MB (Buffers 100%  31%).
Wrote 23 of 659 MB (Buffers 100%  12%).
Wrote 24 of 659 MB (Buffers 100%  81%).
Wrote 25 of 659 MB (Buffers 100%  80%).
Wrote 26 of 659 MB (Buffers 100%  11%).
Wrote 27 of 659 MB (Buffers 100%  45%).
Wrote 28 of 659 MB (Buffers 100%  96%).
Wrote 29 of 659 MB (Buffers 100%  55%).
Wrote 30 of 659 MB (Buffers 100%   6%).
Wrote 31 of 659 MB (Buffers 100%  60%).
Wrote 32 of 659 MB (Buffers 100%  78%).
Wrote 33 of 659 MB (Buffers 100%  30%).
Wrote 34 of 659 MB (Buffers 100%  48%).
Wrote 35 of 659 MB (Buffers 100%  99%).
Wrote 36 of 659 MB (Buffers 100%  51%).
Wrote 37 of 659 MB (Buffers 100%  33%).
Wrote 38 of 659 MB (Buffers 100%  15%).
Wrote 39 of 659 MB (Buffers 100%  15%).
Wrote 40 of 659 MB (Buffers 100%  83%).
Wrote 41 of 659 MB (Buffers 100%  35%).
Wrote 42 of 659 MB (Buffers 100%  23%).
Wrote 43 of 659 MB (Buffers 100%   6%).
Wrote 44 of 659 MB (Buffers 100%  49%).
/usr/bin/cdrdao: Success.  : scsi sendcmd: no error
CDB:  2A 00 00 00 4E 22 00 00 17 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 4B 7E 0A 00 00 00 00 0C 00 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
Sense flags: Blk 19326 (not valid) 
resid: 47104
cmd finished after 23.320s timeout 180s
ERROR: Write data failed.
ERROR: Writing failed - buffer under run?
ERROR: Writing failed.

cdrdao command:
-----------------------
/usr/bin/cdrdao write --device /dev/hdb --driver generic-mmc:0x00000010 --speed 32 -n -v 2 --force --eject --remote 15 /home/shamanix/ds2/a/rld-ds2a.cue

---

### Post by SpEcIeS on 2005-08-16
Well got past the ffmpeg issue, and it would seem that I was missing a dev package for a library. Ooooppppsss... :)

Anyway, what is the best way of building [COLOR=Red]deb[/COLOR] packages? Currently I have been using checkinstall.

---

### Post by PeP on 2005-08-17
I use checkinstall to but I am not familiar with alternates methods.

---

### Post by SpEcIeS on 2005-08-17
Yeah...  I find checkinstall to be the easiest, so far, however I did use this method for a while. It is a little more involved:

[b]Dillo Example:

1) unpack tarball
2) cd into directory
3) run: dh_make -e [email]contact_species@hotmail.com[/email] -f ../dillo-0.8.5.tar.gz
4) sudo dpkg-buildpackage[/b]

You have to make modifications to the CONTROL file and others..  I think. It has been a while.
I like checkinstall. The easy way is not always the best way, but it is still the easy way. :D

---

### Post by Shamanix on 2005-08-21
Anything i can do to not get "Writing Failed"? (see my last post) works fine in windows, but HATE that OS!

---

### Post by SpEcIeS on 2005-08-21
[QUOTE=Shamanix]Anything i can do to not get "Writing Failed"? (see my last post) works fine in windows, but HATE that OS![/QUOTE]
It would seem that I had a similar problem, if not the same. While making a backup data DVD, I received an error, so I saved the project, exited the program, then re-entered the K3B and opened the project. Also, make iso was applied.

It would seem, on my system at least, 0.12.2 worked without error issues. Downgrade?  :-P  ](*,)

What is win .. dows.... ?  :)

---

### Post by Shamanix on 2005-08-22
heheh, don't quite remember what " win .. dows...." was, think it was something about making computers HELL :P

I'll try to downgrade to 0.12.2, maybe latest version isn't compatible with kubuntu, thanks.''

EDIT: same thing happened in 0.11.x, so don't think any version will work unless i do something else.
Also: Won't burn faster that 1x on DVD...

---

### Post by SpEcIeS on 2005-08-23
[QUOTE=Shamanix]heheh, don't quite remember what " win .. dows...." was, think it was something about making computers HELL :P

I'll try to downgrade to 0.12.2, maybe latest version isn't compatible with kubuntu, thanks.''

EDIT: same thing happened in 0.11.x, so don't think any version will work unless i do something else.
Also: Won't burn faster that 1x on DVD...[/QUOTE]
As far as the not burning faster than 1x on DVD, I found the same thing, but I wonder if the reading is not accurate. 
When burning a data DVD, I used the "Determine supported writing speeds" beside the "Speed" selector. This determined how fast the DVD will burn, and it seems accurate, since it read my 8x DVD-R as such.
Now, when burning a DVD, approx. 3.7GB of data, at the bottom K3B indicated that my burner was burning at 1.7, but this would change. However, the whole process, including creating an ISO, took approx. twenty-five minutes. Also, the FIFO does not operate when burning DVD's.
I am no expert on the hardware calculations, but that does seem on target. So far I am just going with it. If this is an error reading the current burning speed, then oneday it will be corrected. :)

---

### Post by Shamanix on 2005-08-25
got another problem now, haha. when i try to burn a CD-R image, K3b says the file doesn't exist :P, tried with several images...

---

