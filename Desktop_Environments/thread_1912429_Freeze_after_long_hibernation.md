---
title: "Freeze after long hibernation"
date: 2012-01-20
forum: Desktop Environments
---

### Post by a-web on 2012-01-20
I am running ubuntu 11.10, and hibernation has worked fine for a while.  Recently if I come out of hibernation after a long period (over night, for example) I only get a black screen.  I am not sure if this corresponded with an upgrade.  When it freezes, I notice that the hard disc light is not on at all.  I end up pressing and holding the power button until the computer shuts down, then rebooting.

Thanks for the help!

---

### Post by a-web on 2012-01-21
Update...  Ctrl+Alt+F1 (or 2...) doesn't bring up a virtual terminal when I have my black screen.

---

### Post by varunendra on 2012-01-23
See if this helps: [http://savio2010.blogspot.com/](http://savio2010.blogspot.com/)

I'm not sure if an update can modify /etc/fstab file, but it does get modified sometimes for some reasons unknown to me, resulting in similar problems.

And ctrl+alt+F1/F2.... etc. would work only when the OS is loaded, while in this case, it won't even start loading.

---

### Post by a-web on 2012-01-25
Thanks varunendra!

I went through all the diagnostics they had listed and nothing was awry.  The only change I did was> **Step 8**
Regenerate your initrd. 
[COLOR=red] *sudo update-initramfs -u* [/COLOR]
 Reboot now.And my computer was hibernating over night and came back up fine this morning.  So that seems to have worked.  I am going to wait a day before I marked the thread as solved, just to make sure.

---

### Post by a-web on 2012-01-25
Nope, the problem persists.
Happened again today after a day of hibernating.

---

### Post by Cookieh on 2012-01-25
Same thing happens to me...

---

### Post by varunendra on 2012-01-26
*@a-web,*
Please post outputs of:
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
cat /etc/initramfs-tools/conf.d/resume
free -m
swapon -s
```*@Cookieh,*
Please go through the link I posted in my first post. If that doesn't help, please post the outputs of the same above commands.
[Please make sure your issue is same as *a-web's*, that is - no hard disk activity at resume. Else your problem may be different.]

---

### Post by a-web on 2012-01-26
My Outputs...
```
a-web@__:~$ sudo fdisk -l
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000297d9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   300704669   150352303+  83  Linux
/dev/sda2       300704670   312576704     5936017+   5  Extended
/dev/sda5       300704733   312576704     5935986   82  Linux swap / Solaris

Disk /dev/sdb: 1014 MB, 1014497280 bytes
32 heads, 61 sectors/track, 1015 cylinders, total 1981440 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System


a-web@__:~$ sudo blkid
/dev/sda1: UUID="fd2c31de-e31e-41e4-91d5-9bd33aa239e2" TYPE="ext4" 
/dev/sda5: UUID="7f49065d-75c6-4c19-8eed-ad1395ae3fd0" TYPE="swap" 
/dev/sdb: LABEL="A WEBER" UUID="4D73-35C9" TYPE="vfat" 


a-web@__:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=fd2c31de-e31e-41e4-91d5-9bd33aa239e2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=7f49065d-75c6-4c19-8eed-ad1395ae3fd0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


a-web@__:~$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=7f49065d-75c6-4c19-8eed-ad1395ae3fd0


a-web@__:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1979        942       1037          0         77        475
-/+ buffers/cache:        389       1590
Swap:         5796          0       5796


a-web@__:~$ swapon -s
Filename                Type        Size    Used    Priority
/dev/sda5                               partition    5935980    0    -1

```

---

### Post by varunendra on 2012-01-26
Sorry, couldn't get time to reply. But I am getting out of ideas anyway. The outputs contain nothing suspicious except one thing-

What's that 1GB drive in your system (/dev/sdb)? It doesn't seem like you are using it or booting from it, since it doesn't have any partitions on it as per fdisk or blkid. So I'm wondering if it could be some corrupt memory card or flash drive interfering with the resume process! Can you identify it? See if the resume works without it being plugged-in.

Apart from that, the only thing I can suggest is to try reformatting the swap partition to eliminate any chances of bad clusters in it.


**_PS_:**
As a side note, you have 2GB of physical RAM, while the swap is more than 5GB. IMHO, that's a wastage of space unless you are planning to increase the RAM to that much amount. As per current setup, a 2 GB swap (or slightly bigger, say- 2.2GB) would be sufficient.

---

### Post by a-web on 2012-01-27
The 1G drive (/dev/sdb) is a usb drive.  I will try without that plugged in to see if there are any changes.

And I would gladly take you up on the P.S. advice.  How do I go about changing the size of my swap?
           --Aw

---

### Post by varunendra on 2012-01-27
> **a-web said:**
> The 1G drive (/dev/sdb) is a usb drive.  I will try without that plugged in to see if there are any changes.
..and I'd wait... with the fingers crossed! ;)

> **a-web said:**
> How do I go about changing the size of my swap?
 By using gparted in a live session. You would have to "right-click --> swapoff" the swap partition to be able to resize it.

As another side note, it (the swap part.) seems to be the only partition besides sda1. As such, it is absolutely unnecessary to create it inside an 'extended' partition.

If these two are the only partitions you are going to have (and there is nothing wrong with it), I'd recommend to delete the swap and the extended partition containing it, and recreate the swap as a 'Primary partition'. You can then add the obtained empty space to the existing sda1 partition (using the 'Resize' option in gparted).

_Please note that if you do so, you would have to re-edit your fstab file to change the existing UUID of the swap with that of the new one_. (which can be determined with *sudo blkid*)

---

### Post by a-web on 2012-02-06
Looks like removing the USB drive has aided in hibernation.  I will mark the thread as "solved" after a few more days without problems.

---

### Post by a-web on 2012-03-08
So I was premature in marking this as "solved".  My computer is still freezing when coming back from hibernating.  It also freezes when I turn it on from being off.  Standby works perfectly.

Are there any new insights??

And let me know if it is more appropriate to make a new thread, I am not sure about all the nuances of posting etiquette.

Thanks.

---

### Post by varunendra on 2012-03-12
> **a-web said:**
> And let me know if it is more appropriate to make a new thread
I think it is okay to continue this one since it'll more clearly present the attempts we have already made.

I wish and hope there's something significant in the logs, but not sure where to start. So lets first start with an output of:
```
lsmod
```

IIRC, there are a few certain driver modules that cause problems after a sleep/hibernate -> wake up cycle, although none of those problems was a complete freeze up. If something appears in the output that is known for similar problems, we may try to create a script that manually unloads/loads it during each cycle.

Also, if you can, please go through the various log files in the /var/log directory to see if something relevant is logged there.

---

### Post by a-web on 2012-03-21
I did the following (from the computer manufacture) and it seemed to help.  As the problem is sporadic, it is hard to tell if the problem is fixed completely.
> remove all usb, esata, video, etc devices from the computer, remove the battery, and remove the ac adapter.  With the computer disconnected, hold down the power button about 10 seconds. Reattach the battery, then the ac adapter, and power the system back up. Try hibernating the system and let me know if anything's changed.
Aaron
ZaReason Tech Support
[www.zareason.com]("http://www.zareason.com/")Here's the output:
```
:~$ lsmod
Module                  Size  Used by
usbhid                 41905  0 
hid                    77367  1 usbhid
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_realtek   254163  1 
snd_hda_intel          24262  2 
snd_hda_codec          91859  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
arc4                   12473  2 
uvcvideo               67271  0 
snd_seq_midi           13132  0 
videodev               85626  1 uvcvideo
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
binfmt_misc            17292  1 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
i915                  509519  3 
iwlagn                273980  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              393421  1 iwlagn
psmouse                73673  0 
serio_raw              12990  0 
drm_kms_helper         32889  1 i915
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   192194  4 i915,drm_kms_helper
cfg80211              172427  2 iwlagn,mac80211
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
wmi                    18744  0 
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ums_realtek            13096  0 
usb_storage            44173  1 ums_realtek
uas                    17699  0 
ahci                   21634  2 
libahci                25727  1 ahci
r8169                  43104  0 

```

---

### Post by varunendra on 2012-03-21
If not, you may try this: [http://ubuntuforums.org/showthread.php?p=11613057](http://ubuntuforums.org/showthread.php?p=11613057)

This was a suggestion for wireless related problem, but may help yours too (i.e., if required).

---

