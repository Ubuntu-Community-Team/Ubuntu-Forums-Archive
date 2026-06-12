---
title: "[SOLVED] session lasted less than 10 seconds"
date: 2006-10-16
forum: Desktop Environments
---

### Post by Hiroshima on 2006-10-16
I just installed Ubuntu on my laptop.

I made three partitions, 1 gig "swap", 4 gig "/" 4 gig "home" and 9 gig "hda3", all of which I formatted prior to install.

It started up nicely, and then I ran automatix to get everything configured.

Automatix came back with a list of errors of programs not installed, and then I restarted.

At the login screen, I get > Your session lasted less than 10 seconds.
the error log says:
> /etc/gdm/Xsession: Beginning session setup..
mkdtemp: private socket dir: No space left on device

Even if I messed up the partitioning, each drive should be big enough to handle everything... unless automatix left a lot of temp files around...

Any ideas would be great!

Cheers, 

Hiroshima

---

### Post by mozetti on 2006-10-16
Do a search for "session lasted less than 10 seconds". There are multiple reasons this can occur. I experienced it myself, but can't remember exactly what it was (sorry) -- it had something to do with my video driver and/or xorg.

---

### Post by kwalo on 2006-10-16
Probably removeing ~/.xsession-errors file would solve this problem.

---

### Post by Hiroshima on 2006-10-16
I was just about to say "I did search" then I realized, I only searched the Ubuntu forums, which didn't have my specific error.

When I searched google "session lasted less than 10 seconds no space left on device" I got 
[http://arun-prabha.com/wdpress/?p=301](http://arun-prabha.com/wdpress/?p=301)

Which was pretty helpful.  He ran into the same problem after using automatix that I did.  I didn't know which files to delete, but I made a little space, and can at least startup now.

If someone is reading this, and follows his advice, please note you need a double dash -- in front of max-depth=1 (he has -max-depth=1 should be --max-depth=1)

I'll paste his page here so that it is in the forums for future use.

 September 19, 2006
Fixing No space left on device error in Ubuntu Linux

> September 19th 2006 Posted to Technology

I&#8217;m using Ubuntu as my main OS in both my desktop and laptop. I was getting the following error when I tried to login to Ubuntu couple of days back:

Your session lasted less than 10 seconds blah blah blah&#8230;&#8230;

When I clicked the box to see the Xserver error, I got the following error message:
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp.
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x &#8220;/var/lib/gdm/:0.Xservers&#8221; -h &#8221; &#8221; -l &#8220;:0&#8243; &#8220;username&#8221;
/etc/gdm/PreSession/Default: Beginning session setup mkdtemp: private socket dir: No space left on device.

It didn&#8217;t allow me to login. I then Googled to find a solution and also checked Ubuntu Forums, which is a great place to get help. This is what I did to fix the problem. It&#8217;s pretty simple.

I selected Failsafe Terminal under sessions in the GNOME login screen. I was then presented with the terminal screen. I issued the following command to find out the disk space used and space left in my system.

df -l

This showed that my root partition (/) was 100% full. I had no idea how it got full. I had allocated 10 GB for the root partition and there&#8217;s no way I would have filled that with installing programs. I thought may be the .deb files that Ubuntu uses to install programs filled up the space. I tried to clean up the .deb files with the following command:

sudo apt-get clean

It didn&#8217;t free up any space. The root partition was still 100% full. I wanted to find out the space used by each directory under the root partition. This is what I did in the terminal.

cd /   &#8212; to go to the root folder

sudo du -hc &#8211;max-depth=1    &#8212; to find out the space used by each directory under the root folder.

I found out that /var/backup was using 6.5 GB. I tried to check what was in there under /var/backup, but I was denied permission to enter that directory. I wasn&#8217;t sure how to enter since 

sudo cd /var/backup didn&#8217;t work. I had to enable the root password with the following command to enter that directory.

sudo passwd root

su

When I checked /var/backup there were 3 files created by some program to backup the files in the system. I have no idea which program created those. I installed some backup software earlier, but then I reformatted the hard drive and reinstalled Ubuntu 2 weeks back. I didn&#8217;t install the backup software again. The only program I used was Automatix to install common programs in Ubuntu. I&#8217;m not sure if Automatix created those backup files. I then deleted those 3 backup files and regained the 6.5 GB back. I then logged out of the Failsafe terminal mode and logged in back using the regular GNOME session and it worked. :-) 

Thanks for the ideas,

Hiroshima

---

### Post by PriceChild on 2006-10-16
Ubuntu/Linux needs space on the drive in order to swap "permissions" files around.

You have no space left... if you want to get back in the system, press ctrl+alt+F1 at log in to enter a terminal.
```
sudo rm -R /var/cache/apt/archives
exit
```ctrl+alt+F7 to get back to log in and try again.

---

### Post by dannyboy79 on 2006-10-16
another main reason for x shutting down is that automatix may have screwed up your xorg.conf file since you said automatix gave tons of errors. did you try to install nvidia drivers using automatix? if so, I am guessing this is why. when you are at the terminal line, type in sudo nano /etc/X11/xorg.conf and make sure the drive is "VESA". like this

Section "Device"
	Identifier	"VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video"
	Driver		"VESA" (NOTE: or maybe "vesa" not sure)
	BusID		"PCI:1:0:0"
	Option		"DisableIRQ"		"true"
	Option		"EnableAGPDMA"		"true"
EndSection

or you could try 
sudo dpkg-reconfigure xserver-xorg

I am not at home so I am totally sure if VESA needs to be capital or not. sorry. good luck

---

### Post by Hiroshima on 2006-10-16
After having followed the instructions I posted above, I was able to get back in.  I think the real problem ended up being that I didn't leave enough space when I set up the drives, thus automatix ran out of room, and that's where the errors came from.

I'm going to look through all the applications I have, and remove any that aren't necessary, and try to trim down /usr that way.  If I can, I'd like to move my whole /usr to another drive.  After getting back in, I realized that my file system drive is smaller than I thought I'd set it up to be.

I've asked for some advice on moving /usr here:
[http://ubuntuforums.org/showthread.php?t=278387](http://ubuntuforums.org/showthread.php?t=278387)
I started a new thread because I thought the problem was a little different than the one here.  My file system is still 95% full, but there seems to be enough space to loggin.

Thanks for the ideas, and if you have any more about moving /usr, can you put them on the other thread?

Thanks again,
Hiroshima

---

### Post by sumanta on 2007-07-02
I have installed Ubunru 7.04. I had been running it smoothly for 10 or 15 days. But currently facing the same problem i.e., "session lasted less than 10 seconds". I tried so many things to get rid of things but failed :(. 
Currently I am working in failsef gnome. Any help? 
The .xsession-errors is giving the following errors:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "sumanta"
/etc/gdm/Xsession: Beginning session setup...
/etc/bash.bashrc: 11: shopt: not found
/etc/bash.bashrc: 54: Syntax error: "}" unexpected (expecting "fi")

---

### Post by Hiroshima on 2007-07-05
Since my problem was limited disk space, I don't think that the solution that worked for me is necessarily going to work for you.  

First, maybe check if it is a disk space problem... can you check how full your disks are?  This might let you know if this really is the problem.
Next, if it isn't a disk problem, I would start a new thread, probably not too many people are looking at this one because it is old.  Your problem might be with bash scripts, since .xsession-errors mentions two lines with bash, but this is only a wild guess, you'll need help from someone who knows a lot more than me.

Good luck.

Hiroshima

---

### Post by sumanta on 2007-07-06
Thanks Hiroshima. I check my disk space and it's fine.


Filesystem           1K-blocks      Used                  Available      Use%          Mounted on
/dev/sda7            123071896      26017884        90802320        23%              /
varrun                  513800            112                  513688            1%               /var/run
varlock                 513800             0                     513800            0%               /var/lock
procbususb          513800           116                   513684           1%               /proc/bus/usb
udev                     513800            116                  513684            1%              /dev
devshm                513800              0                    513800            0%              /dev/shm
lrm                        513800            33788              480012            7%             /lib/modules/2.6.20-16-generic/volatile
/dev/sda1             14651244      2768440           11882804        19%             /media/sda1
/dev/sda5             14636928         40                  14636888         1%              /windows
/dev/sdb1              2006720        930368            1076352           47%           /media/disk

Please try some solution. 

Sumanta

---

### Post by Hiroshima on 2007-07-07
Sumanat, just in case you haven't already, I would start a new thread.  I don't know enough to help you.  Good luck, and keep trying.  Someone who does know enough will help.  I have always gotten help, sometimes with some wrong turns on the way, but people have always helped.

Good luck.

Hiroshima

---

### Post by lahdo on 2007-09-24
I have very similar problem but in my case /dev/sda7 is 100 % full and when I used this:

cd / — to go to the root folder

sudo du -hc -–max-depth=1 

I found that ./usr is using 1.9 GB and ./media is using 15 GB. Folder /sbin in /usr is using 6.9 GB !! What I can delete from this folder?

I am linux newbie, thanks in advance for reply

---

### Post by lahdo on 2007-09-24
I am able to use my system error disappear-> miracle!

But what I am suppost to delete right now, not to have this kind of problem in the future ? How can I check which folders contain lot's of unuseful data?

Thanks in advance!

---

