---
title: "Unable to mount volume - thumb drive"
date: 2008-06-28
forum: Desktop Environments
---

### Post by mrman_421 on 2008-06-28
The error message says 'cannot obtain lock on /media/.hal-mtab'

I had no problems with this drive a few days ago. I've tried other devices through the same usb port with similar results.

I have searched google and these forums pretty thoroughly, and everyone who had the same problem ended up figuring it out themselves before any useful reply came =P

Which is no help to me, totally new to Linux entirely here. Running Ubuntu... something Heron. I had a friend set it up for me, and I've been loving it, but feel so far impotent to solve my own problems as right now time is limited to study command line stuff as I'm in the final stretches of a hideously intense Chinese course, the final test of which I have but one chance to pass. So, if it is necessary to go into command prompt to solve this problem, please lead me explicitly through every step.  Though I'm no tech moron, I'm almost as noob as noob can be on this command line stuff.  

Thanks in advance for your help!

P.S. All 4 of my USB ports are giving me the same problem...

---

### Post by p_quarles on 2008-06-28
I remember having a similar (nb: not the same, though) issue some time back. It was fixed by restarted hal and dbus:
```
sudo /etc/init.d/hal restart && sudo /etc/init.d/dbus restart
```
Worth a try.

---

### Post by mrman_421 on 2008-06-28
Nope, didn't work... just froze my computer for a moment, kicked me offline, and my computer didn't recognize any volume plugged in.  After restarting the computer, I am back to square one. Thanks, though. Any other ideas, anyone?

---

### Post by benerivo on 2008-06-28
NOTE - This suggestion involves deleting a file outside the user's home folder.

I think the file you mention (/media/.hal-mtab) is created on a computer the very first time you plug a usb storage device in. Also whenever you plug one in, a temporary file is created called something like /media/.hal-mtab.lock, that disappears when you unplug the device.

If i were in your situation, i would look in the /media folder and see what files are there -- they two mentioned above are hidden files, so you may have to go to select View > Show Hidden Files in the file manager to see them. I would then delete the /media/.hal-mtab.lock file if it is there and then restart the pc and see if the problem is fixed. If it isn't, then i would delete the /media/.hal-mtab file and reboot. To delete these files, you need root permission. I would do this by opening a terminal and typing```
gksudo nautilus
```which should open a window from which you have root permissions.

A word of warning. I have not attempted this myself, and it may cause further and more serious problems. My guess is that it will work and i see no reason why it would cause any problem at all.

---

### Post by mrman_421 on 2008-06-28
cannot seem to find the media folder.... I'm an idiot, please take my hand and guide me step by step =P

---

### Post by benerivo on 2008-06-28
Open a terminal window and type
nautilus /media
and hit return

---

### Post by mrman_421 on 2008-06-28
Well that.... failed spectacularly =P

It said it couldn't find /media and then my hard drive freaked out for about 15 minutes while I tried to shut down =/

---

### Post by benerivo on 2008-06-29
> **mrman_421 said:**
> Well that.... failed spectacularly =P

It said it couldn't find /media and then my hard drive freaked out for about 15 minutes while I tried to shut down =/

That's bad. Go back  in and open a file manager window. Click on the up button until you've gone up as much as you can. You should be able to see all the system folders, and there should be called one called media. Try to open that one up and remember to show hidden files.

---

### Post by mrman_421 on 2008-06-29
There is no such folder... going up as far as I could would put me in the root folder right? because I looked in root and file system. both don't contain a folder named media.

---

### Post by vanadium on 2008-06-29
That is the first time I would see an Ubuntu system that does not have a media directory. To convince us, open a terminal and post here the output of ```
ls /
```

---

### Post by mrman_421 on 2008-06-29
bin    dev   initrd          lib    lost+found  proc  srv  usr      vmlinuz.old
boot   etc   initrd.img      lib32  mnt         root  sys  var
cdrom  home  initrd.img.old  lib64  opt         sbin  tmp  vmlinuz

---

### Post by benerivo on 2008-06-29
So you don't have a /media folder. This is something that is definitely going to cause problems with storage devices, such as the one you have with the usb drive. It really needs to be fixed, and i would suggest making a new one by running```
gksudo nautilus
```and making a new folder called media. I'd also reboot, and hopefully this will work for you. There may be problems to do with permissions. When you create the new folder, right click on it and go to Properties > Permissions. It should have...

Owner = root
with 'create and delete files' for the folder acces

Group = root
with 'access files'

Others
'access files'

---

### Post by mrman_421 on 2008-06-29
done, and done.

still the same problem. I actually tried this once before without results, but tried it again and reassured that the permissions were as you stated.

any other ideas guys?

---

### Post by kumarnarain on 2008-06-29
Just to rule out bad hardware...have u tried to plug  in any other media and still getting the same result...also try plugging your hard drive to an other linux system and keep us posted. Also it might be useful to inspect your /etc/fstab entries

---

### Post by mrman_421 on 2008-06-29
Yeah, I plugged in a memory card reader and got the same thing.  I also plugged my thumb drive into my xbox360 with no problem.  I don't think it's the usb ports because I tried all four of them with the same result. Plus, the port is communicating, because ubuntu sees that there is a 4 gb thumb drive plugged in, it just refuses to mount it.  More specific instructions on how to inspect my /etc/fstab entries please?

---

### Post by kumarnarain on 2008-06-29
Hello
Please post a copy of the /etc/fstab file (by doing sudo vi /etc/fstab)before plugging in the drive and after plugging the drive..basically...
1.cd /etc
2.vi fstab
3.Copy the contents and save as a text file say without.txt
4.Press Esc key followed by q! to exit without committing accidental changes
5.Plug the drive
6.Repeat steps 1 to 3 and save as say with.txt
7.Upload both files

Let me see how I can help?

Also would like to know if it is a laptop or desktop......would appreciate if you can also post the output of lspci

---

### Post by mrman_421 on 2008-06-30
well, it gave me one output, then I think I accidentally caused some changes to the file because I got a message saying that I may have unintentionally altered the file.
now, when I try to do the same thing, it gives me this -

~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
"etc/fstab" [New DIRECTORY]

what the hell did I just do?!??!

---

### Post by kumarnarain on 2008-06-30
Hai
How did you get out of the vi mode...as long as you used Esc+q+! you could not have altered....ok please go to /etc folder by using cd /etc and then type ls and see if you have fstab listed as a file or folder...a folder is blue in color whereas if it was a file it would be in your regular black colour...anyway the contents of fstab FILE is more important...dont worry..u dont have write permissions to /etc folder by default (unless of course u had used sudo)

---

### Post by mrman_421 on 2008-06-30
i believe i did alter the file. I did use sudo, I misread your directions. When I pressed esc+q+1 it didn't do anything, so I just xed out. let me look to see if i have the folder

---

### Post by mrman_421 on 2008-06-30
i found it. it's a file.

---

### Post by kumarnarain on 2008-06-30
So what does it contain?

---

### Post by smo0th on 2008-06-30
you don't have a /media directory that is SO DAMN WEIRD, I think something went wrong with the installation, if your installation is new or you can backup files and are in the mood of reinstalling I would recommend to check the CD integrity and make a fresh install.

---

### Post by mrman_421 on 2008-06-30
the file now contains:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=468cc0d2-6ae8-4ed7-9a73-4c7ac1dcc4c8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=ff9b0da5-2bca-45b3-ae4a-d4af0a0abda5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
"fstab" [readonly] 9 lines, 480 characters

to smooth:
at one point, the port was working swimmingly. then I had a little issue with my video drivers and ever since then it's been this way.

oh, btw, it's an HP laptop, Athlon Turion64x2, Nvidia graphics, if that helps at all

---

### Post by smo0th on 2008-06-30
okay,

please post results from:

```
sudo fdisk -l
df -h
lsmod | grep usb
lsusb
sudo tail -f /var/log/messages
dmesg|grep scsi

```

so we get a better picture

---

### Post by mrman_421 on 2008-06-30
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69afd9f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         182     1461883+  82  Linux swap / Solaris
/dev/sda2   *         183       14593   115756357+  83  Linux
richard@ubuntu-laptop:/etc$ lsmod | grep usb
usb_storage            82496  0 
libusual               23520  1 usb_storage
usbcore               169904  6 usb_storage,libusual,uvcvideo,ehci_hcd,ohci_hcd
scsi_mod              178488  6 usb_storage,sbp2,sg,sr_mod,sd_mod,libata
richard@ubuntu-laptop:/etc$ lsusb
Bus 002 Device 002: ID 0c45:62c0 Microdia 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
richard@ubuntu-laptop:/etc$ sudo tail -f /var/log/messages
Jun 29 21:14:27 ubuntu-laptop kernel: [  468.307682] usb 2-2: USB disconnect, address 3
Jun 29 21:44:05 ubuntu-laptop -- MARK --
Jun 29 22:04:05 ubuntu-laptop -- MARK --
Jun 29 22:24:05 ubuntu-laptop -- MARK --
Jun 29 22:44:05 ubuntu-laptop -- MARK --
Jun 29 23:04:05 ubuntu-laptop -- MARK --
Jun 29 23:24:05 ubuntu-laptop -- MARK --
Jun 29 23:44:06 ubuntu-laptop -- MARK --
Jun 30 00:01:58 ubuntu-laptop pulseaudio[5964]: protocol-native.c: Failed to push data into queue
Jun 30 00:01:59 ubuntu-laptop pulseaudio[5964]: protocol-native.c: Failed to push data into queue
dmesg|grep scsi

---

### Post by mrman_421 on 2008-06-30
richard@ubuntu-laptop:/etc$ dmesg|grep scsi
[   17.821421] scsi0 : ata_generic
[   17.821499] scsi1 : ata_generic
[   18.299824] scsi 0:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-851S  1.50 PQ: 0 ANSI: 5
[   18.300504] scsi2 : ata_generic
[   18.300584] scsi3 : ata_generic
[   18.628773] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1200BEVS-6 01.0 PQ: 0 ANSI: 5
[   21.336170] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   21.336224] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   21.379633] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   21.379658] sd 2:0:0:0: Attached scsi generic sg1 type 0
[  460.616397] scsi4 : SCSI emulation for USB Mass Storage devices
[  463.438392] scsi 4:0:0:0: Direct-Access     Ut165    USB2FlashStorage 0.00 PQ: 0 ANSI: 2
[  463.483487] sd 4:0:0:0: Attached scsi generic sg2 type 0

---

### Post by mrman_421 on 2008-06-30
BTW, this so-called esc+q+! command ain't working for jack. am I doing it wrong??

---

### Post by smo0th on 2008-06-30
it is recognizing a Microdia device and it tries to emulate USB mass storage so it seems the hardware is being detected but some controllers are missing

looks like you don't have some modules running, try installing these:
```

sudo modprobe usbhid
sudo modprobe hid

```

wait 10 seconds, go to Places>>Computer, do a refresh to see if something mounts, try removing and insterting the drive again and post back what happens o.o

---

### Post by mrman_421 on 2008-06-30
same thing as before. the drive appears and is recognized as 4gb removable media, but refuses to mount

---

### Post by Bubba64 on 2008-06-30
I didn't read through the whole thread but if you don't have anything on the thumb drive that you need gparted will repartition it and it should be recognized if your computer is running correctly. That is what I used when I borked a 2 gig thumbdrive. :)

---

### Post by kumarnarain on 2008-06-30
hai
Inspite of reinstalling the modules if you are unable to mount then...as I see it you seem to be heading for a re-install. back up your stuff and do a clean reinstall after checking the cd/dvd for errors

---

### Post by smo0th on 2008-06-30
> **mrman_421 said:**
> same thing as before. the drive appears and is recognized as 4gb removable media, but refuses to mount

it refuses to mount because it is not recognized by the system, per your fdisk, we got ```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69afd9f3

Device Boot Start End Blocks Id System
/dev/sda1 1 182 1461883+ 82 Linux swap / Solaris
/dev/sda2 * 183 14593 115756357+ 83 Linux
``` so you have your linux ext3 and swap partitions but you don't have any other partition to mount, although the system partially recognizes the hardware, but there's something else failing, I had a similar problem a month ago, when I performed an update and rebooted the problem was solved, make sure you have your system up-to-date, just for reference, I'm using gutsy.

---

### Post by mrman_421 on 2008-07-01
so far... no good
I have been unsuccessful in all attempts, including constant updating. however, there has been an interesting development.

Today, for the first time in a long time, I used my dvd+rw drive. I used it to burn a cd full of mp3's, with absolutely no problem. then, just for kicks, I tried to play the music I just burned using the dvd+rw drive, using that same drive. guess what. "cannot mount volume"
WTF!?!?

---

### Post by kumarnarain on 2008-07-01
if u have backed up everything may be you should go in for a reinstall with acpi turned off at the bios settings.

---

### Post by smo0th on 2008-07-01
ran out of ideas here, my vote is for a reinstall too, best of luck man.

---

