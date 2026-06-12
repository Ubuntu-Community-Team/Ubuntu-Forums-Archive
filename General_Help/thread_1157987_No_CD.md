---
title: "No CD?"
date: 2009-05-13
forum: General Help
---

### Post by MichaelDance on 2009-05-13
Hey all, Im just wondering how to solve this problem in the new version of ubuntu linux 9.04 i believe , i been told in the help that when you insert a cd it loads on the desktop, well nothing happens for me. It sounds like its loading but nothing comes up and no options to do nothing, DVD do not load either or Music Cds, im just wondering if anyone else has this problem? Thanks for your time.

---

### Post by prem1er on 2009-05-13
After you put in the cd open a terminal and post the results of this.

```
fstab
```

Also, on the desktop select 'places' and see if the mounted cd shows up in there.

---

### Post by muteXe on 2009-05-13
did you check the cd for errors? (md5 checksum)
did you make sure you're set to boot from the cd drive?

---

### Post by prem1er on 2009-05-13
> **muteXe said:**
> did you check the cd for errors? (md5 checksum)
did you make sure you're set to boot from the cd drive?

I think you misread the post.  He isn't having a problem with booting a live cd.

---

### Post by muteXe on 2009-05-13
On a re-read it actually sounds like his cd drive aint reading *anything* (dvds, cds, music cds).

---

### Post by MichaelDance on 2009-05-15
> **muteXe said:**
> On a re-read it actually sounds like his cd drive aint reading *anything* (dvds, cds, music cds).
 Hey MuteXe ):P my Drive worked on Vista before.

---

### Post by MichaelDance on 2009-05-15
> **prem1er said:**
> After you put in the cd open a terminal and post the results of this.
 
```
fstab
```
 
Also, on the desktop select 'places' and see if the mounted cd shows up in there.
 
Hey prem1er):P Thanks ill check that tonight :)

---

### Post by MichaelDance on 2009-05-20
Na didn't work in terminal

---

### Post by b@sh_n3rd on 2009-05-20
I have this prob on ONE computer...it's quite strange coz it worked before and on another PC it does...I have to just manually mount the cd...did it twice...This is the first time I've had such trouble on Ubuntu anyway...I was wondering if any settings got changed...

Oh yeah, I temporarily removed my writer to use on another PC that doesn't have a CD-ROM...Until I replaced it, I was running ubuntu without this..after that I added it and for the first time booted Jaunty with my writer (about an hr after installing Jaunty)...it WAS there when installing but removed it to install Jaunty on the other PC...This hasn't happened previously though...but then, I *had* run ubuntu with the cdrom at least once...could this be the problem in my case? Not having the drive upon booting Jaunty from the hdd for the first time?

---

### Post by prem1er on 2009-05-20
> **MichaelDance said:**
> Na didn't work in terminal

What do you mean it didn't work?  Just type that in the terminal and post the results back here.

---

### Post by MichaelDance on 2009-05-20
> **prem1er said:**
> What do you mean it didn't work? Just type that in the terminal and post the results back here.
 fstab in the terminal didn't work its still not reading the cds/dvds

---

### Post by b@sh_n3rd on 2009-05-20
ok, just tried a CD after a long time...it works...wonder why your's doesn't...can you access a CD when you mount it manually?```
# sudo mount /dev/scd0 /media/cdrom0
```

---

### Post by bacardiandwatermelon on 2009-05-20
I think he meant paste the results of this command..
```
gedit /etc/fstab
```

---

### Post by mf205 on 2009-05-25
I'm having similar trouble to MichaelDance, although less serious - some of my DVDs fail to mount, but not all.  And sometimes if I eject and then close again, they'll mount.  I'm running 64-bit Jaunty.

In response to the suggestions people made earlier in the thread: no, the drive doesn't appear in Places,

```
fstab
```gives me

bash: fstab: command not found,

```
sudo mount /dev/scd0 /media/cdrom0
```gives me

mount: /dev/sr0: unknown device

and

```
gedit /etc/fstab
```gives

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=feab4232-b205-4ba0-9e58-ac6cd3991d18 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a3adfb20-1068-46b0-a83d-6ee846b75bec none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by MichaelDance on 2009-06-01
> **mf205 said:**
> I'm having similar trouble to MichaelDance, although less serious - some of my DVDs fail to mount, but not all. And sometimes if I eject and then close again, they'll mount. I'm running 64-bit Jaunty.
 
In response to the suggestions people made earlier in the thread: no, the drive doesn't appear in Places,
 
```
fstab
```gives me
 
bash: fstab: command not found,
 
```
sudo mount /dev/scd0 /media/cdrom0
```gives me
 
mount: /dev/sr0: unknown device
 
and
 
```
gedit /etc/fstab
```gives
 
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# / was on /dev/sda1 during installation
UUID=feab4232-b205-4ba0-9e58-ac6cd3991d18 / ext3 relatime,errors=remount-ro 0 1
# swap was on /dev/sda5 during installation
UUID=a3adfb20-1068-46b0-a83d-6ee846b75bec none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
 
 
Exactly like me m8 we are in the same boat but im on 32 bit laptop :I

---

### Post by VMC on 2009-06-01
With a known non empty cd(music, data, etc) in the drive, type the following from a terminal and inspect what the output says:

```
wodim -checkdrive
```

---

### Post by MatMan on 2009-06-03
> **VMC said:**
> With a known non empty cd(music, data, etc) in the drive, type the following from a terminal and inspect what the output says:

```
wodim -checkdrive
```

I have the same problem with my cd drive, and have followed the thread. after wodim -checkdrive i get

device was not specified. Trying to find an appropriate drive...
Detected CD-R drive; /dev/cdrw
Using /dev/cdrom of unknown capabilities
Device type         : Removable CD-ROM
Version             :5
Response format     :2
Capabilities        :
Vendor_info         : 'Slimtype'
Identification      : 'DVD A  DS8A1H   '
Revision            : 'WH66'
Device seems to be: Generic mmc2 DVD-R/DVD-RW

Using generic SCSI-3/mmc    CD-R/CD-RW driver  (mmc_cdr).
Driver flags        : MMC-3 SWABAUDIO BURNFREE FORCESPEED
Supported modes     : TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R

that's all.... still no CD visible. 

thanks

---

### Post by mf205 on 2009-06-22
I get almost exactly the same thing:

Device was not specified. Trying to find an appropriate drive...
Detected CD-R drive: /dev/cdrw
Using /dev/cdrom of unknown capabilities
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'DVD+-RW GT10N   '
Revision       : 'A104'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R

---

### Post by mf205 on 2009-09-17
I'm still having this problem with my drive.  Can anyone help?

---

### Post by mf205 on 2009-10-17
Please help!!!!

---

### Post by 3rdalbum on 2009-10-17
I'll try to help, although I've never had your problem before.

It looks like Ubuntu identified your drive as "/dev/scd0" incorrectly; the output from the "wodim" command says that your device is at "/dev/cdrom" or possibly "/dev/cdrw". So what you'll need to do is open the /etc/fstab file as root:

```
gksudo gedit /etc/fstab
```

And in the bottom line where it says "/dev/scd0", change it to "/dev/cdrom". And make a note of your modification.

Save your changes and reboot; if my presumption is correct, CDs should mount now.

---

### Post by mf205 on 2009-10-18
Many thanks for trying to help.  Unfortunately, no joy; it's just the same as before.

---

### Post by mf205 on 2009-11-08
Update: I updated to Karmic, and still no joy.  But then: I had a period of about a week when it all worked: every DVD I tried would mount with no problems.  But that didn't last: some of my DVDs now won't mount.  There were some updates from Update Manager in the meantime, and possibly it was one of these that f*cked things up.  But I now have no idea what these were.

If you've ever claimed that Ubuntu "just works", then help me right now.

---

### Post by MichaelDance on 2009-12-18
> **b@sh_n3rd said:**
> ok, just tried a CD after a long time...it works...wonder why your's doesn't...can you access a CD when you mount it manually?```
# sudo mount /dev/scd0 /media/cdrom0
```

RESULTS:
```
michael@michael-laptop:~$ sudo mount /dev/scd0 /media/cdrom0
[sudo] password for michael: 
mount: special device /dev/scd0 does not exist

```

---

### Post by MichaelDance on 2009-12-18
> **3rdalbum said:**
> I'll try to help, although I've never had your problem before.

It looks like Ubuntu identified your drive as "/dev/scd0" incorrectly; the output from the "wodim" command says that your device is at "/dev/cdrom" or possibly "/dev/cdrw". So what you'll need to do is open the /etc/fstab file as root:

```
gksudo gedit /etc/fstab
```And in the bottom line where it says "/dev/scd0", change it to "/dev/cdrom". And make a note of your modification.

Save your changes and reboot; if my presumption is correct, CDs should mount now.
  
When clicking on the cdrom0 in the computer i got this:
```
mount: special device /dev/cdrom does not exist
```

---

### Post by MichaelDance on 2009-12-18
> **mf205 said:**
> I'm having similar trouble to MichaelDance, although less serious - some of my DVDs fail to mount, but not all.  And sometimes if I eject and then close again, they'll mount.  I'm running 64-bit Jaunty.

In response to the suggestions people made earlier in the thread: no, the drive doesn't appear in Places,

```
fstab
```gives me

bash: fstab: command not found,

```
sudo mount /dev/scd0 /media/cdrom0
```gives me

mount: /dev/sr0: unknown device

and

```
gedit /etc/fstab
```gives

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=feab4232-b205-4ba0-9e58-ac6cd3991d18 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a3adfb20-1068-46b0-a83d-6ee846b75bec none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

> **MichaelDance said:**
> When clicking on the cdrom0 in the computer i got this:
```
mount: special device /dev/cdrom does not exist
```

I done the gedit /etc/fstab i got this after i modified from a post
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=1918661f-b8be-49dd-92e8-ad88c3c51d39 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b5ad2529-c623-4c26-9fd7-b3a89cd338d9 none            swap    sw              0       0
/dev/cdrom       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by MichaelDance on 2009-12-18
> **VMC said:**
> With a known non empty cd(music, data, etc) in the drive, type the following from a terminal and inspect what the output says:

```
wodim -checkdrive
```

After puting in wodim -checkdrive i got:
```
michael@michael-laptop:~$ wodim -checkdrive
Device was not specified. Trying to find an appropriate drive...
wodim: No such file or directory. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.
michael@michael-laptop:~$ 

```

---

### Post by MichaelDance on 2009-12-20
Also when opening gxine The wizzard reported:
```
**Health check results**
Failed - Could not access cdrom: /dev/cdrom

Either create a symbolic link /dev/cdrom pointing to your cdrom device in the preferences dialog.

```
Also got this error with it:
```
[B]Health check results
[/B]Failed - could not access dvdrom: /dev/dvd

Either create a symbolic link /dev/dvd pointing to your cdrom device or set your cdrom device in the preferences dialog.
```

Also got ths with it:
```

[B]Health Check results
[/B]Failed - could not read stats for /dev/dvd.

If you are using the ide-cd module ensure that you have the following entry in etc/modules.conf:
options ide-cd dma=1
Reload ide-cd module.
Otherwise run hdparm -d 1 on your dvd device.

```

Any ideas??

---

### Post by utopyr on 2009-12-29
I did this:
[http://ubuntuforums.org/showthread.php?t=1359907&highlight=sr0]("http://ubuntuforums.org/showthread.php?t=1359907&highlight=sr0")

Still working, a week on, so I haven't changed it. However, I noticed that the file I created should be a block node, which these steps do not create. If I do it again, I will create the device node with mknod.

Another however--I asked about this on my local Linux users' list, & one of the folks there usefully wrote:
> You can check the differences between the output of dmesg with the
livecd and from the system with the problems.  In the kernel messages
there, you should see a driver announcing the presence of the drive.

And another on that list:
> The udev system should be creating the device node for you.  So
something is probably wrong with the udev configuration.  The kernel
notices a new device, tells userland about the event, the userland udev
daemon gets the event notice and follows the rules in /etc/udev.d (or
whatever) to do something about it.

But yes, to make the device node yourself, you'd use mknod.  It has
a weird syntax that is summarized when you run "mknod --help".  You
need to know the correct major and minor device numbers for your
CDROM device.  They're in sysfs, though, in the "dev" file for your device.

 /sys/block/{devicename}/dev

... with a colon between the major and minor numbers.

If my blunt object fix stops working, I'll take a closer look at udev.

---

### Post by mf205 on 2010-01-15
No success for me.

---

