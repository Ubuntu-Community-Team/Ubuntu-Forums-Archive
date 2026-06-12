---
title: "Disks not mounted on startup but in /etc/fstab"
date: 2006-10-06
forum: Desktop Environments
---

### Post by Yv12345vY on 2006-10-06
Hello all,

A couple of days ago my partitions (other than root) stopped being mounted on startup.  I'm stumped as to why!  /etc/fstab looks absolutely fine and nothing has changed that I noticed overnight.

When the machine boots the drives appear to be mounted but nothing exists in the directories where they mount to.  I can unmount and re-mount and everything works (command line or using the disk manager).

Any idea as to why?????  Or how to fix it??? :confused:

---

### Post by dannyboy79 on 2006-10-06
if it's a sata drive i had that same issue, it's has something to do with the mounting of the disks occuring prior to the sata module being loaded. i had to add something to my /etc/modules file and now my sata drive gets mounted upon boot up just like all my other drives. i gogled it for ya, heres the explaination, you can recompile your kernel to include sata support or you can add the right module to /etc/modules, I think you almost always need to add 'libata' to get things started, but for most chipsets you also need to add an appropriate low-level driver from the list below. Please post if you have corrections as I made best guesses and used google searches to find out which chipsets each driver supports.

sata_via - VIA chipsets (KT600, KT800, etc)
sata_nv - Nforce 3 (and 2?) chipsets
ahci - Intel ? and other ahci conforming chipsets
ata_adma - Pacific Digital and other adma conforming chipsets
ata_piix - Dell Poweredge and others.
sata_promise - Most Promise chipsets
sata_sil - Silicone Image chipsets (Nforce 2?)
sata_sx4 - Promise FastTrak S150 SX4
sata_svw - PowerPC G5
sata_vsc - Vitesse VSC7174 ? (Some Dells)

So to summarize, to get your SATA drives mounted on boot you'll need two lines added to /etc/modules: libata and the driver from the list above that corresponds to your SATA controller.

Hopefully this list helps a few people as it took me a while to get my VIA chipset working.

here is what i added to my /etc/modules file

libata
sata_sx4

---

### Post by dannyboy79 on 2006-10-06
PS, gogle has every answer for all your questions, i admit sometimes it'll take you 4 hours to get and a lot of times it can be quicker getting it in forums but as you can see with this example. if you had gogled "sata drive automounting, linux" you wouldn't of had to wait half a day or however long you have waited for this answer.

don't get me wrong, i am not at all trying to discourage you from coming here but i have to admit that i have posted a lot of questions and hardly anyone provides the kind of help like i do. i am not trying to be cocky, but I actually come on these forums and read thru various sections and if I see something that i know the answer to, i'll go in the thread and help people and for some reason i haven't been lucky enough to have people do that for me regarding my questions.

---

### Post by Yv12345vY on 2006-10-06
Thanks for the reply.  My problem is not sata related.  It happens on a Dell D810 laptop.

I have Googled (and Yahoo-ed, and MSN-ed) but only results I found explained how /etc/fstab works, which I already knew.  I was hoping somebody would point me in the right direction as to why /etc/fstab drives aren't mounted correctly.

---

### Post by pjbgravely on 2006-10-06
Post your /etc/fstab,

There may be clues in there.

Paul

---

### Post by Yv12345vY on 2006-10-06
First thing Monday am I'll post it.

---

### Post by ColDebug on 2006-10-06
did u recompile your kernel?

Try this: try mounting those "invisible" discs via evms by putting "evms/" in the dev path of those discs. Example:

fstab says: 

/dev/sda1            /        reiserfs    notail   0  1
/dev/sda4            /mp3     reiserfs    notail   0  1

Try mounting "mp3" like this:

sudo mount -t reiserfs /dev/evms/sda4 /mp3

if that works, the what you are experiencing is evms locking out the /dev/mapper mounts. 

The fix:

disable evms in your machine and reboot. Evms mounts those discs early in the boot process and will lock out other attempts at mounting later in the process. It's installed by default in ubuntu despite there being no real use for it at all to the average user. If you really, really must keep it then to get any real benefit from it you need to edit all your physical fstab devices (yes, even root) to mount through it.

---

### Post by Yv12345vY on 2006-10-09
ColDebug - I'll give disabling evms a go.  Thanks for the suggestion.

For reference, here's my /etc/fstab

```

proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda4	/media/work	ext3	defaults,errors=remount-ro	0	1		
/dev/sda2       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by dannyboy79 on 2006-10-09
what i find very strange is that ALL your hard drives are sda, normally sda is for scsi emulation of usb or for sata drives. what kind of hard drive is iin your laptop? anyway, this is weird. if i have my usb drive hooked up before i start ubuntu, it automatically shows up with an icon on my desktop and i don't even have an entry in my fstab for it! it is formated as ext3. what is tyhe drive formatted. i gogled and found this, it's either a session problem or a priviledges problem. You say that a USB harddrive is mounted successfully, which filesystem does the HD use? 
Anyway, for the moment i rule out insufficient priviledges. Thus remains a session problem. Please open the gnome-volume-manager and check if in the first tab the first three checkboxes are marked. If they are and the problem remains, could you create a new user and switch to the new user and plug in the USB stick. What happens?

Occasional mounting is a good indicator for a wonky stick or a wonky port. Did you try the stick on other systems and what do they do?

---

### Post by Yv12345vY on 2006-10-09
I don't have a USB hard drive.  What I have is one hard drive partitioned up.  Everything was working fine just the way it is until last week.  Now I'm forced to umount and mount after starting up.

---

### Post by dannyboy79 on 2006-10-10
> **Yv12345vY said:**
> I don't have a USB hard drive.  What I have is one hard drive partitioned up.  Everything was working fine just the way it is until last week.  Now I'm forced to umount and mount after starting up.

you forgot to tell us what kind of hdd you have in your laptop. let us see what lspci -v states. this issue has something to do with the mounting of the disks occuring BEFORE the module for it is loaded. so we need to figure out what module we need to add to /etc/modules

---

### Post by Yv12345vY on 2006-10-10
Disabling evms didn't fix anything.

Here's what lspci -v says for IDE:

```

0000:00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03) (prog-if 80 [Master])
        Subsystem: Dell: Unknown device 0186
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 209
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at bfa0 [size=16]
        Capabilities: [70] Power Management version 2


```

---

### Post by dannyboy79 on 2006-10-10
> **Yv12345vY said:**
> Disabling evms didn't fix anything.

Here's what lspci -v says for IDE:

```

0000:00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03) (prog-if 80 [Master])
        Subsystem: Dell: Unknown device 0186
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 209
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at bfa0 [size=16]
        Capabilities: [70] Power Management version 2


```
AHA, i told you. No just kidding. I kind of thought it was a sata issue. So now we just need to do what I sugested earlier.

or i also found this, I am not sure if hotplug is your problem. But if it is and you need to load it earlier, run the following command:

mv /etc/rcS.d/S40hotplug /etc/rc5.d/S34hotplug 

This will execute hotplug before mountall. Not tested so I can't be sure.

---

### Post by Yv12345vY on 2006-10-10
Adding the two lines to /etc/modules didn't do the trick and I don't have the hotplug link in rcS.d.  Back to Googling/putting up with it.

Thanks for you help dannyboy.

---

### Post by dannyboy79 on 2006-10-10
> **Yv12345vY said:**
> Adding the two lines to /etc/modules didn't do the trick and I don't have the hotplug link in rcS.d.  Back to Googling/putting up with it.

Thanks for you help dannyboy.


well are you sure that you added the correct 2 lines in your modules file? i am pretty sure that's it because it worked for my sata drive that I have. if not it's to bad, i was really hoping to chalk up another issue I've help out with.

this is where I got the adding the modules to the file and it looks like i forgot to mention something about the ramdisk, check it out. [http://ubuntuforums.org/showthread.php?t=30233](http://ubuntuforums.org/showthread.php?t=30233)

---

### Post by Yv12345vY on 2006-10-10
Yeah, I added the Intel SATA stuff.  Oh well...

I'm sure eventually I'll figure it out.  I had a problem with another laptop that was running Ubuntu painfully slow that took me months to figure out (on and off).

---

