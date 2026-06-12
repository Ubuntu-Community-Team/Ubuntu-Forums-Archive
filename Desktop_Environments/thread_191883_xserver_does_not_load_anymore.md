---
title: "xserver does not load anymore"
date: 2006-06-08
forum: Desktop Environments
---

### Post by olaf_noehring on 2006-06-08
Hi
 
I have installed fs-driver ([http://www.fs-driver.org/](http://www.fs-driver.org/)) in my windows. I have mountes 2 ext3 partitions (/exchange and /home) in windows (XP pro) and can access them read & write. 
BUT: When I boot to Ubuntu 6.0.6 the Xserver can not be started because a /var/.... (besides others) is suddenly "read-only". Is this a fs-driver problem or an ubuntu weirdness.

PS: I am new to ubuntu.... 
 
Olaf

---

### Post by an.echte.trilingue on 2006-06-08
I doubt very much that this has to do with the driver that you installed in windows.  Just to be sure, will you post the contents of /etc/fstab?

Was X ever working?

Did you install anything in ubuntu lately?

Is the partition that has /var on it full? (type df in a terminal to see how much free space you have)

Can you give us some more precise error output?

---

### Post by olaf_noehring on 2006-06-08
Hi

well, yes I did install some things (recommended on [http://www.beginningubuntu.com/dapper_tips.html](http://www.beginningubuntu.com/dapper_tips.html) ):
- I set up multiverse and universe repositories
- I added "deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free "
- and then these packages: 
w32codecs,
libdvdcss2,
realplay,
mplayer,
mozilla-mplayer,
vlc,
vlc-plugin-esd,
flashplugin-nonfree,
gftp,
firestarter

VLC was not recommended on that site. (which is currently down due to high traffic)

Xserver (gdm) was working. Weird: I had the problems before that xserver did not start. I did well - something - (reboot, recovery boot, I do not know anymore) and then it did work again.

The partition which has /var should be / - right? If so it can not be full (/ has about 5gb, /home is different partition with 6gb)

I will take a picture of the screen later (for better error output) and post it here (I have to restart ;-) ).

How can I post /etc/fstab? (How can I list it ...)

Olaf

---

### Post by an.echte.trilingue on 2006-06-09
To look at fstab, just type "gedit /etc/fstab".  You can cut and paste it from there.  This only works in a graphical environment, of course, so you might have some issues if X isn't starting.

Or, for the command line option, you can "cat /etc/fstab" to look at the file and "cat /etc/fstab > *filename*.txt" will create a text file *filename*.txt in your current working directory with the contents of your fstab in it that you can upload to the forums for us to look at.  Of course, this is just a long shot, I just want to look at it to make sure that you have windows on /dev/hda1 since having it elsewhere will cause many different problems.

While you are at it, please also post the output of these:
```
cat /etc/X11/xorg.conf
lspci
```
Remember that you can use ">" to create a new file with the output of those for easier posting to these forums.
Also let us know what your video card is and if it is configured properly.  I suspect that this is where your problem is.

---

### Post by olaf_noehring on 2006-06-09
Hi
currently I am at work - but I will get on it tonight.
Most weird: When I started my PC at home this morning, the xserver did LOAD! - Do not ask why. Suddenly it's there. I will run the commands anyways and post the output as I expect that the Xserver does not start again when I have run windows before.

Olaf

---

### Post by olaf_noehring on 2006-06-09
HI

fstab as follows:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb1       /60gb           ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda6       /home           ext3    defaults        0       2
/dev/hda5       /tausch         ext3    defaults        0       2
/dev/hda1       /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda7       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0 

I have not done the rest yet, will do it tomorrow. Another weird thing happened when I came back from work: Ubuntu was still running, but i then was unable to access the internet through Firefox / ubuntu update ... (but router was still online!)

Olaf

---

### Post by an.echte.trilingue on 2006-06-09
I just had an epiphany.  The fs-driver does not maintain file permissions.  That can really bugger a *nix system.  Were you poking around in /var under windows with this driver?

I hope you enjoy the WM.  I saw a thing on TV last night about the big screen set up in the Main...

---

### Post by olaf_noehring on 2006-06-10
Hi

I am not a soccer fan and I hope Cologne - where I live - will not be to crowded on days when there are games here.
I am not doing anything in /var vrom windows.
See my last post (fstab)
/dev/hda6 /home ext3 defaults 0 2
/dev/hda5 /tausch ext3 defaults 0 2
are the two partitions which I have set drive letters for in fs-driver under windows. **I** (maybe windows did) have not done anything from windows on /dev/hda6 (/home).
On /dev/hda5 is afaik only windows file structure (yes, etx3 partition)

Olaf

---

### Post by olaf_noehring on 2006-06-10
Hi

so I was lucky - the error is back :-o

Here is a screenshot after I said "sudo reboot":
[IMG]http://www.team-noehring.de/extern/error/divers004.jpg[/IMG]

here is the cat... output:
[http://www.team-noehring.de/extern/error/cat.txt]("http://www.team-noehring.de/extern/error/cat.txt")

here the lspci:
[http://www.team-noehring.de/extern/error/lspci.txt]("http://www.team-noehring.de/extern/error/lspci.txt")

and at last the xsession-errors:
[http://www.team-noehring.de/extern/error/xsession-errors.txt](http://www.team-noehring.de/extern/error/xsession-errors.txt)

Olaf

---

### Post by olaf_noehring on 2006-06-11
Hi

ubuntu seems more weird to me every day.
This morning: Xserver started - but had read-only access to the /tausch partition (ext3)
I tried a couple of things but was not successfull to get back to the xserver after a reboot.
Please see the images for information.
**Do you think I should reinstall Ubuntu?**

[IMG]http://www.team-noehring.de/extern/error/fehler_001.jpg[/IMG]

[IMG]http://www.team-noehring.de/extern/error/fehler_002.jpg[/IMG]

[IMG]http://www.team-noehring.de/extern/error/fehler_003.jpg[/IMG]

Olaf

---

### Post by an.echte.trilingue on 2006-06-12
Well, quite the oposite of what I thought at first, I guess the fs-driver did mess your file system up.  Sorry to send you looking for wild gooses.  Your video card is set up fine as far as I can tell (90% of the problems with X are video card related), although I have heard that the proprietary nVidia drivers are better than the nv driver that comes with Ubuntu. 

Get a bootable CD (like the ubuntu one), boot from it (obviously) and then try to unmount everything and run fsck then (you can't do that when the fs is mounted, and it has to be mounted to boot off of it).




I'm not a football fan either.  I kind of feel sorry for you guys since you are the closest WM city to England...  I kind of assumed that since you were signing off kind of early on Friday you were going to watch the game.

---

### Post by olaf_noehring on 2006-06-12
Hi

I have started Ubuntu from the life cd and ran e2fsk for the drives (except the swap partition - this did not work).

The developer of the fs-driver wrote me that /var/log/messages announces problems:
 
[COLOR="DarkOliveGreen"]Jun  5 14:24:20 olaf-ubuntu kernel: [4294679.169000] EXT3-fs: INFO: recovery
required on readonly filesystem.
Jun  5 14:24:20 olaf-ubuntu kernel: [4294679.169000] EXT3-fs: write access will
be enabled during recovery.
...
Jun  5 14:24:20 olaf-ubuntu kernel: [4294679.234000] hda: dma_intr: status=0x51
{ DriveReady SeekComplete Error }[/COLOR]

He sees the problem in
 DriveStatusError BadCRC. 
Which hints to hardware problems (he says): Not enough energy, IDE cables,harddrive is on it's way to die completely....

What do you think?

I am pretty curious if the problem with starting ubuntu returns after I have run windows a couple of times/starts

Olaf

---

