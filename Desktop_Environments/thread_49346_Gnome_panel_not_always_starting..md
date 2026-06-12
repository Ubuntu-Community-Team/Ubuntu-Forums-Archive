---
title: "Gnome panel not always starting."
date: 2005-07-15
forum: Desktop Environments
---

### Post by musther on 2005-07-15
Sometimes I boot my system, log in, and get gray bars where my panels should be, sometimes I get a desktop background, sometimes not, sometimes I can get a menu by right clicking on the desktop, then open a terminal, and kill the panel, sometimes not.  If I kill the panel, it reloads, but is still gray.  If I restart x (ctrl alt backspace), sometimes it starts working, that's pretty much how I get it working again, just keep restartng x and occasionally the machine.

Once it's running, no probs.

Any ideas?

---

### Post by hydra on 2005-07-15
yep im having the same problems just when sometimes using mozilla firefox it sometimes get stucked then i have to forceit to close....I have to reboot  and when i login i just see the toolbar but without icons on desktop or cant interact with the toolbar like if it wasnt loaded right.


Any ideas??? I think this may be a bug and i have updated my buggy list and send a message to developers i think...but still dont know how to fix it


** I have realized that when i get in a page where mozilla needs some plug-ins to be installed it get stucked**

---

### Post by musther on 2005-07-16
Yeah, I've managed to crash x a couple of times, that seemed to trigger it, but it happened on it's own too.  Very strange...

---

### Post by hydra on 2005-07-16
yep man i fix this by re-installing ubuntu unfurtunately :( 

but no one is responding and this is the closest solution i got....so i will now can figure out what the problem was by configuring it again

---

### Post by adrian440 on 2005-07-16
[QUOTE=musther]Sometimes I boot my system, log in, and get gray bars where my panels should be, sometimes I get a desktop background, sometimes not, sometimes I can get a menu by right clicking on the desktop, then open a terminal, and kill the panel, sometimes not.  If I kill the panel, it reloads, but is still gray.  If I restart x (ctrl alt backspace), sometimes it starts working, that's pretty much how I get it working again, just keep restartng x and occasionally the machine.

Once it's running, no probs.

Any ideas?[/QUOTE]
 I had this trouble, it seemed intermittent. Didn't know what to do to fix it. I deinstalled hal & gnome-volume-manager and haven't seen it do this since.

---

### Post by hydra on 2005-07-16
It got stuck sometimes now that ive reinstalled it but anyways i solve this by inserting a cd-rom ...weird??? but this probably make apps to "wake up"  and i can use it perfectly

---

### Post by musther on 2005-07-16
That kind of makes sense, it's a problem with hal, or at least it seems to be, it causes some of the same problems on powerbooks if you suspend them.  Removing hal solves the problem, but then you get 'error, could not initialise hal' popping up now and again, and of course you have none of it's functions.  Keeping a CD in the drive may do something to get hal working - I don't know a lot about it, but hal manages automounts and the like.

I wonder if somebody who does know more about it can help mow that we've identified that it's hal, and now we know of a workaround, however odd.

Well, maybe we're getting there!!!  Smile!

---

### Post by musther on 2005-07-16
Out of interest, what hardware are you having this trouble on?

---

### Post by hydra on 2005-07-16
I have a sony comp PCV-RS25MV pent 4  2.66Ghz......80GB.....256 RAM

nothing fancy just the essential im thingk in in expanding it to 512 or more and maybe a RADEON or Nvidia card 



u?


PS: I found ubuntu patch some buggy stuff already from the hal-device-manager 

> * Fixes from the ubuntu package:
    + Added debian/patches/hal-dbus_max_match_rules_per_connection.diff
      - Allow more matching rules per connection. Fixes problems with
        hal-device-manager on systems with lots of devices.
 + Added debian/patches/harddisk-volumes.patch
      - fdi/90defaultpolicy/storage-policy.fdi: If a volume has an empty
        fsusage, set it to "filesystem" to work around the fact that the
        non-root hald cannot read harddisk partitions.
      - libhal-storage/libhal-storage.c: Do not declare a volume as invisible
        if hal does not know the file system (hald cannot read harddisk
        partitions).

but still not for us and were getting closer :) haha

---

### Post by musther on 2005-07-16
Hal, or possibly gnome-volume-manager is hanging on login, thanks for the tip with the CD though, it seems to work so far.  It may be the volume manager and not hal, because if you have hal installed but not volume-manager, it still happens.  I'm posting a bug report now.

---

### Post by hydra on 2005-07-16
I found also a guy that installs xcfe and have the same prob we have and this is what he do:

he creates a directory in home named Desktop/Autostart and he leaves in there a file called desktop.sh with the following content **xfdesktop &** and with the following perms **chmod +x desktop.sh** so u may try this but just change the content in desktop.sh for gnome desktop and maybe it should work Im gonna try it...tell u later

---

### Post by musther on 2005-07-16
Most people don't seem to have this trouble, I wonder if we can figure out why we do, maybe it'll be a start.  Tell me more about your system, as it's the volume manager, maybe we should start there:

Drives and info:
1 3.5" Floppy
1 CD/DVD-RW
1 120gb Seagate HD
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1912    15358108+   7  HPFS/NTFS
/dev/hda2            1913        2034      979965   82  Linux swap / Solaris
/dev/hda3   *        2035        3128     8787555   83  Linux
/dev/hda4            3129       14593    92092612+   5  Extended
/dev/hda5            3129        3736     4883728+  83  Linux
/dev/hda6            3737       14593    87208821    b  W95 FAT32

I don't know what I'm looking for really, nothing much special there, do you have an extended partition?

---

### Post by hydra on 2005-07-16
Do u have this problem for another apps like for running some application or something??...i sometimes have probs with xmms and limewire when starting my desktop like this (triggered by CD)

---

### Post by musther on 2005-07-16
I havn't got xmms installed at the moment, although I'm going to soon.  What kind of problems, i'll look out for them.  Any luck with the autostart file?

---

### Post by hydra on 2005-07-16
nop im having the same problem and with xmms, it started well but then i load the playlist  and add a file correct..but when i play it it get stucked :| i reinstalled it but the same...mann

---

### Post by hydra on 2005-07-16
hey man now it shows a message showing "HAL unable to load" so now i know its a HAL problem....but it's strange how can it be not loaded and still can autodetect the devices :| ....well im still figuring out how to solve it

Did u come out woth something??

---

### Post by musther on 2005-07-17
Yeah, I think I've got something.  I think it's having trouble with extended partitions.  How's your HD set out, 'sudo fdisk -l' will tell you if you're not sure.  If I'm right (which I may not be) you'll have an extended partition.  Maybe the volume manager doesn't get along with them, all I can tell you is what happened to me:

I've tried 64 and 32 bit ubuntu 5.04 on the same machine, at that time it had one 120gb hard drive with four partitions, that's three primary and an extended which contained two logical drives.  The first was a windows NTFS, the second was a linux swap, third linux root, fourth linux home and fifth shared FAT32 storage.  Under both versions I had the same problem.  Now I've dug out a 40gb drive so I have the following setup.  The first drive, the 120gb has two primary partitions, a windows NTFS and a shared fat32 for storage, the second has three primary, a linux swap, linux root and linux home.  So now I have no extended partitions and everything seems fine (I say that with my fingers crossed).

With reference to the xmms problem, I had that before, and I still do now, so my guess is it's nothing to do with this gnome panel thing.

Hope I've helped, at least a little bit!!!  Let me know if you have an extended.

---

### Post by hydra on 2005-07-17
so this is what ive got:

```

Disco /dev/hda: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/hda1   *           1        9639    77425236   83  Linux
/dev/hda2            9640        9729      722925    5  Extendida
/dev/hda5            9640        9729      722893+  82  Linux swap / Solaris

```

so yep i have an extended one as u can see.....any hints??

---

### Post by musther on 2005-07-17
But that's ok, you've only got two partitions, so there's no need for the extended, and you're lucky because you have only got your linux swap in an extended.  What you need to do is go into fdisk and remove the linux swap (hda5) then delete the extended partition (hda2) then create a new primary partition which will be hda2 and make it your swap.  You won't lose any data and it should fix your problem!!!

Good luck, let me know how it goes.

---

### Post by musther on 2005-07-20
Well, it seemed to solve my problem for a while, but it's doing it agian now, I don't know, it's really annoying.

---

### Post by Ezzet on 2005-07-21
Hi - I have same problem here! Have anyone solved the problem? I reinstalled whole system but nothing happened. I think maybe it's something to do with the restricted repositories?? I choosed them and updated whole system - the problem began!

---

### Post by hydra on 2005-07-21
Nop i havent solved it....It happens to solve for a little while like musther but i kept the "eject and insert CD" option to make it work....at least while we get a solution

---

### Post by Ezzet on 2005-07-21
Ok! Strange problem...

---

### Post by musther on 2005-07-21
Maybe Ezzet has a point, after I removed my extended partition and reinstalled the system, it was fine for quite a while, then I updated as he did, and some time after that the problem started again.  

As far as getting into your system goes, here's what I've done.

Keeping a CD in the drive was the first thing I tried, a solution kindly suggested by hydra, and although it worked for a while, it doesn't now.

Secondly I tried removing hal and gnome-volume-manager, and although this works, it's not a great solution as they're useful.

Then I resorted to doing what I expect those of you with this problem do to get into gnome, boot up, log in, kill x do 'sudo killall gnome-panel', restart x and hope, then if it doesn't work, repeat this and try starting failsafe gnome.

Today however, my fiance figured out that if you log in and this happens, you can get everything working by pressing Ctrl + Alt + Del a few times, give it a try, you'll get the hang of when to press it and how long to wait etc.  It's the quickest way I've found to get up and running.

I hope we get this sorted soon, it's really starting to make me angry.

Good Luck!

---

### Post by hydra on 2005-07-22
ctrl + alt + del   was one of my first options but it didnt work much time....i dont know why the cd tip i gave u doesnt work now still works for me....I strangely fix the problem for a while I think  but don know what i did maybe i added some library or something but nothing concrete to tell...unfortunately

---

### Post by micom2020 on 2005-07-22
I have a variation of the problem: ](*,) 
There are three user names, of which 2 work perfectly.
On the third I have the following problem:
On logging in:
..The desktop background is displayed OK.
..The top and bottom panels are displayed as empty rectangles.
..Both panels then commence FLASHING ON AND OFF repeatedly every second several  times.
..The login proces then stops with only the background remaining.

The CD trick has not helped. CTL + ALT +BKSPC restarts but does not fix the problem. 
Deleting this user and recreating a new user (with different name) works for a while but then the new user (only) starts to have the same problem again. 

Is "GConf" and its associated default schemas the possible culprit??

---

### Post by Ezzet on 2005-07-22
Hi again! Now suddenly I get a "failed to initialize HAL" error message! Maybe there is somekind connection with the panel-problem?

[http://ubuntuforums.org/showthread.php?t=24146](http://ubuntuforums.org/showthread.php?t=24146)

---

### Post by musther on 2005-07-22
I get the "Failed to initialize HAL" messgage if I log in and then leave it, (if I don't do something like control alt backspace to kill x).  I think this is something to do with it, as it explains why the CD trick helps, (although it doesn't seem to work for me any more).  Removing HAL and gnome-volume-manager solves the problem, but it's not a solution.

---

### Post by varunus on 2005-07-22
I'm jumping into this kind of late, but it seems that updating HAL causes the problem..maybe try downgrading in synaptic using the "force version" option?  If that works, then I think you should file a bug report about the new HAL...well, you should file a bug report anyway.

---

### Post by musther on 2005-07-22
There only seems to be one version, maybe that's because I'm using ubuntu 64, but the only version Synaptic can find is 0.4.7-1ubuntu15 (hoary).

---

### Post by moberry on 2005-07-22
Try deleteing your .gnome2 directory.. This will reset your settings, but could fix the problem.

-jordan

---

### Post by musther on 2005-07-22
Where is .gnome2, I'd like to take a backup copy first?

---

### Post by Wandering Wombat on 2005-07-24
[QUOTE=musther]Where is .gnome2, I'd like to take a backup copy first?[/QUOTE]

/home/*username*/.gnome2 <<<prob have to select view hidden files!

This worked for me the only noticable difference was that I lost the standard panel icons eg. firefox, evolution and cant even remember the other one lol. Just right click top panel and select add and choose what you want to be able to run from the panel. 
Thanx for the tip! Fingers crossed. :wink:

---

### Post by musther on 2005-07-24
Damn, it didn't work.  :-(  I really am very sad!

---

### Post by Vati-Khan on 2005-07-28
I think I got it to work 

it appears that filesystem-errors on my vfat sata drives caused the problem ]

/dev/sda1 and /dev/sdb1 had errors (vfat).

running  fsck.vfat -a on the drives fixed it for me 

wish you good luck

Vati K.

---

