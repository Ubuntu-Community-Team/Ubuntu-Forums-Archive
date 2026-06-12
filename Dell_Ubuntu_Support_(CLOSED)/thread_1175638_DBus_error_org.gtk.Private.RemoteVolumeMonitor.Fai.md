---
title: "DBus error org.gtk.Private.RemoteVolumeMonitor.Failed:An operation is already pending"
date: 2009-06-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ThirdBias on 2009-06-01
I'm new to ubuntu so i have little to no experience dealing with this problem

>  *-cdrom
                description: DVD reader
                product: CDRW/DVD SN-324S
                vendor: SAMSUNG
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /media/cdrom0
                version: U303
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /media/cdrom0
                   configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted

---

### Post by darkultra on 2009-06-02
Maybe this works

[I]Ok, I found the solution right after I posted this.
I deleted /media/.hal-mtab now everything is working properly.[/I]
[http://ubuntuforums.org/showthread.php?p=7298991](http://ubuntuforums.org/showthread.php?p=7298991)

go to that dir
you can to ls -a to see the hidden files
type sudo rm .hal-mtab

---

### Post by oneiric on 2009-11-08
One solution to this problem is to simply open Gparted (also called partition editor, under System -> Administration)

That caused the usb drive and its files to re-appear in Nautilus.  

deleting /media/.hal-mtab didnt' work for me

---

### Post by Mash909 on 2010-01-28
I had a similar issue with a USB pen drive.

I deleted the /media/.hal-mtab.lock file but it had no effect.

However, this is what I did to resolve it:

1. Launched 'gconf-editor' and browsed to 'apps / nautilus / preferences'
   - unchecked 'media_automount'
   - unchecked 'media_automount_open'  

2. Launched GParted to find the id of the location of the device (/dev/sdf1)

3. ran ```
sudo mount -t ext3 -o rw,users /dev/sdf1 /media/usb-backup
```

nb this took up to one hour to complete

After that the device was available as normal.  I unmounted with:
```
sudo umount /media/usb-backup 
```
and removed the device

Then re-enabled the Nautilus preferences unset in step 1.

Plugged in the device again and it was found as normal.

---

### Post by allmyfingersandtoes on 2010-06-15
Happened to me on lucid with a cd drive. Drive wouldn't mount unless there was a disk in it at boot. I disabled those two options in gconf-editor, restarted with the drive bay empty (didn't test with the bay full) and reenabled them; success. Thanks, Mash909!

---

### Post by iansane on 2010-08-23
I just had that error on a signature mini usb hard drive and thought it might have to do with the updates I installed last night. (first time I plugged it in since the updates). 

I opened gconf-editor while the drive was still plugged in and it mounted on it's own before I could browse to apps/nautilus/preferences.

So it had something to do with just starting the gconf-editor in my case.

Strange

---

### Post by iansane on 2010-08-23
OK that didn't completely fix it. the drive mounted but it takes for ever to load all the files in the window and then the cursor keeps spinning and the light on my drive flashing like it does in Windows when indexing is turned on. You know how windows has to index all the files and takes forever while Ubunutu usually just opens the window and shows the files fast? Now my Ubuntu is acting like windows which is very frusterating. There should be nothing writing or reading from the drive if I'm not opening or saving something on it which has been a main gripe of mine about windows.

Also my cpu's go to 100% when I open a folder. It's as if some process is running scanning my drive and slowing it down to a crawl every time I open a folder or try to back up a directory.

---

### Post by Bernard_ivo on 2010-08-24
The same with me. I have updated to the latest kernel, samba, gparted and few more and after restart all was fine. Fresh start today lead to: USB mouse worked for a while and now it doesn't work at all. External USB HDD is not loaded either. At the moment all my USB ports seems to be dead. Haven't tried the suggestions above.

Update: I have moved back to 2.6.32-22 kernel and everything works. No time to make checks and debugging :(

---

### Post by iansane on 2010-10-15
The only thing on my system affected was usb drives but what ever happened caused indexes on the drive to get all messed up. 

The next day I put it in a windows xp machine and did a disk check which repaired thousands of orphaned files and messed up indexes and took about an hour. Since then everything has been fine.

---

### Post by frederik.nnaji on 2010-11-02
i have the same error message when trying to mount my recently unbootable system partition.

i have seperate partitions for windows, linux, linux swap and linux home on my computer.

for the past couple of days i was forced to boot from pendrives, since my system partition is inaccessible.

e2fsck asks me if perhaps the filesystem might be in use by another application exlusively, or whether the partition is mounted, i.e. fsck fails also.

no way to mount this partition?

---

### Post by herrison on 2010-11-06
I have exactly the same problem as of two days ago (Nov 4th). Can't boot from usual volume, can't mount my boot drive. Desperately looking for a solution. Not sure what happened, the system seemed to spontaneously reboot during the night and died. Ubuntu 10.10, fully patched.

---

### Post by marjo on 2010-11-13
> **frederik.nnaji said:**
> i have the same error message when trying to mount my recently unbootable system partition.

i have seperate partitions for windows, linux, linux swap and linux home on my computer.

for the past couple of days i was forced to boot from pendrives, since my system partition is inaccessible.

e2fsck asks me if perhaps the filesystem might be in use by another application exlusively, or whether the partition is mounted, i.e. fsck fails also.

no way to mount this partition?

Same problem here.  Also the bootable flag of my Linux partition seems to be gone when I "fdisk -l"
I'm on ubuntu 10.10, packard bell EasyNote LM laptop.
Also Windows doesn't start normally; I get the repair modus there.

---

### Post by Juanchis on 2011-02-11
I'm from Costa Rica, my first language is spanish, please correct my mistakes. I'm a new user too, so...
I  have the same problem. Ubuntu was working well, someday i turned on my  computer and it doesn't work anymore. My grub shows all the version of  the kernel but when i select one doesn't boot a terminal or something  like that. When i use a liveCD, i can't mount my file system, when i  try, it shows just the same message from the title. Please help me, I  really want the information in my hard disc and i don't wanto to use  PhotoRec because it's very annoying to select one by one each file,  including the ones from google crhome cache...

---

### Post by dwasifar on 2011-08-06
I had this problem the other night and found this thread.  Plug the flash drive in and nautilus knows it's there, but won't open it.  Gparted couldn't see it either; in fact, gparted wouldn't complete its devices scan with the flash drive installed.

My situation might be a little different because the flash drive was formatted to ext4, but here's how I solved it:
[LIST]
[*]Open gconf-editor, go to apps>nautilus>preferences and uncheck media_automount and media_automount_open

[*]Plug in flash drive

[*]In terminal, *sudo lshw* to identify the device (in this case it showed up as /dev/sdb)

[*]In terminal, *e2fsck -f /dev/sdb1*
[/LIST]

This recovered the journal on the flash drive's ext4 filesystem and rendered it properly readable again.  You'll want to undo your gconf-editor changes when you're finished.

---

### Post by sallymc on 2011-12-14
I figured out how to stop ubuntu from  thinking the kindle is a digital audio device by default. Instead, it  will just think it's a removable disk drive. .

Here's what I did:

    * open a terminal window (applications/accessories/terminal)
    * type: cd /lib/udev/rules.d <press enter>
    * cp 40-usb-media-players.rules 40-usb-media-players.save <press enter>
    * sudo gedit 40-usb-media-players.rules <press enter>
    * search for "kindle" - you should get a line that looks like this:

ATTRS{idVendor}=="1949" , ATTRS{idProduct}=="0001|0002|0003|0004" , ENV{ID_MEDIA_PLAYER}="amazon_kindle"

    * just go to the beginning of that line and insert # and a space, so the line is:

# ATTRS{idVendor}=="1949" , ATTRS{idProduct}=="0001|0002|0003|0004" , ENV{ID_MEDIA_PLAYER}="amazon_kindle"

    * save the file
    * exit the editor
    * exit the terminal
    * reboot

Now when you plug in your Kindle it should mount it so it looks like a disk drive.

---

### Post by Mururohay on 2012-01-25
> **Mash909 said:**
> 

3. ran ```
sudo mount -t ext3 -o rw,users /dev/sdf1 /media/usb-backup
```


Hello,

After the same error (as the first post), I have seen  your message and done this command : sudo mount -t ext3 -o rw,users  /dev/sdf1 /media/<harddiskName>
Without verify what the command do.
I've seen that the disk have been mounted, but withou anything inside.
So  I umounted it by "right click, safety remove drive" and mounted it on  my Macbook and yes it was confirmed, everything have gone (it asked me  to use the disk for time machine, as a Mac do for all the new empty  plugged disks)

Then I mounted back on my linux machine, to try a "sudo **u**mount  -t ext3 -o rw,users /dev/sdf1 /media/<harddiskName>" but the HDD  was not detected anymor, even by disk utility (on linux and mac).

Have you got an idea about what happend ?

Thank you.

ps: it seems not that I am very disappointed, but I am...

---

### Post by Zackreffil on 2012-06-23
I recently happened this to me but with my entire hard disk someone can tell me how can i do to fix it, i see the thing about the usb but i not sure what commands i have to use to fix it

I wait the early  answer 
Thank you

---

### Post by ka55o5 on 2012-06-24
Hi, lots of results and many SOLVED for (other than just the Ubuntu results):
```
dbus error org.gtk.private.remotevolumemonitor.failed an operation is already pending
```
.. I get the same on 12.04 Precise, but only sometimes and my (Primary) Windows partitions can mount regardless. Perhaps a Google query for the string can provide a quick fix for those who can't mount theirs. :)

P.S.
In Xfce 4.8, since I'm on Xubuntu, Alt+F4 will behave differently than going through the menu Shut down. The dialog looks different, too. I believe that currently only restarting with Alt+F4 actually respects the setting to **not** save the session, so rebooting that way should clear any mount errors (check whether your session is being saved on restart).

---

### Post by Ian Clark on 2013-01-14
> **ka55o5 said:**
> Hi, lots of results and many SOLVED for (other than just the Ubuntu results):
```
dbus error org.gtk.private.remotevolumemonitor.failed an operation is already pending
```
.. I get the same on 12.04 Precise, but only sometimes and my (Primary) Windows partitions can mount regardless. Perhaps a Google query for the string can provide a quick fix for those who can't mount theirs. :)

P.S.
In Xfce 4.8, since I'm on Xubuntu, Alt+F4 will behave differently than going through the menu Shut down. The dialog looks different, too. I believe that currently only restarting with Alt+F4 actually respects the setting to **not** save the session, so rebooting that way should clear any mount errors (check whether your session is being saved on restart).
So what did you do to fix it? I'm running 12.04 xubuntu and i get that same string the first time i mount any of my partitions, including my home folder. i don't understand what the difference is between saving session or not, other than that saving the session seems to hold my keyboard settings.

I found this idea on archlinux forums, and it's specifically for xfce 12.04 and thunar:
[https://bbs.archlinux.org/viewtopic.php?pid=1183483#p1183483](https://bbs.archlinux.org/viewtopic.php?pid=1183483#p1183483)

---

### Post by thesyco on 2013-01-17
I just ran into this problem. I found a quick solution by accident. To find out where it was mounted by using:

dmesg | egrep hd.\|sd.

I then ended up being able to open the usb drive without a problem.

---

