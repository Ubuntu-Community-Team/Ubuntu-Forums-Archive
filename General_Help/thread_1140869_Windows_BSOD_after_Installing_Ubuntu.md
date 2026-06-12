---
title: "Windows BSOD after Installing Ubuntu"
date: 2009-04-28
forum: General Help
---

### Post by sL8 on 2009-04-28
I have looked, googling for hours.
First it was getting windows to actually show up in GRUB.
Now that it shows up, I try to start it and it starts loading then it gives me a BSOD.
I can't read what it says, I can't even get into windows with safe mode.

I try to mount it using sudo and it gives me this error:
> Failed to read last sector (207656126): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
When I try to view it from Places it tells me: > You are not privileged to mount this volumeCan anyone help?

I also took off some ntfs thing for Ubuntu, i got a different message box this time:
> **Unable to mount 53.7 GB Media**
DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending"

---

### Post by f37u5g0d on 2009-04-28
Run 
> 
sudo fdisk -l

In a terminal.  This will list all of the partitions on all of your harddrives.  Make sure that /dev/sda1 is a windows NTFS partition.

---

### Post by sL8 on 2009-04-28
>    Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6528    52436128+   7  HPFS/NTFS
/dev/sda2            6529       13823    58597087+  83  Linux
/dev/sda3           13824       14593     6185025    f  W95 Ext'd (LBA)
/dev/sda5           13824       14593     6184993+  82  Linux swap / Solaris
It is. and judging by the *, its the active one, thats what it even says in partitionlogic 0.7 i believe is the latest. could it be using a pre-release is messing up my hard drive?

---

### Post by f37u5g0d on 2009-04-28
The * is signifying that that partition has the boot flag.  Meaning that the system looks for it when looking for boot files.  I am not positive but I believe that the boot flag should be on the linux partition.  Grub is there.  The windows boot loader doesn't support dual booting (or booting anything but windows).

When you start your computer does grub come up?

P.S. you are correct /dev/sda1 is the windows partition.  Also I strongly suspect that your windows partition has an error on it.  I have seen few windows systems that don't boot for any other reason.

---

### Post by Saghaulor on 2009-04-28
Windows = BSOD

Sorry, I had to. :)

---

### Post by egalvan on 2009-04-28
> **f37u5g0d said:**
> **The * is signifying that that partition has the boot flag.**  Meaning that the system looks for it when looking for boot files.  **I am not positive but I believe that the boot flag should be on the linux partition.  **Grub is there.  The windows boot loader doesn't support dual booting (or booting anything but windows).


```

   Device Boot      Start         End      Blocks   Id  System
**/dev/sda1   *           1        1019     8185086    7  HPFS/NTFS**
/dev/sda2            1020        9726    69938977+   5  Extended
/dev/sda5            1020        8090    56797776   83  Linux
/dev/sda6            8091        9365    10241406   83  Linux
/dev/sda7            9366        9726     2899701   82  Linux swap / Solaris
```


As you can see from my system, the Windows XP partition is marked with the *.

Everything works fine this way...

---

### Post by free-radical on 2009-04-28
> **f37u5g0d said:**
> The * is signifying that that partition has the boot flag.  Meaning that the system looks for it when looking for boot files.  I am not positive but I believe that the boot flag should be on the linux partition.  Grub is there.  The windows boot loader doesn't support dual booting (or booting anything but windows).

When you start your computer does grub come up?

P.S. you are correct /dev/sda1 is the windows partition.  Also I strongly suspect that your windows partition has an error on it.  I have seen few windows systems that don't boot for any other reason.

When i install GRUB into the MBR of the harddisk, it will come up at boot time & which partition is activated is irrelevant imho. or am i off the track?

---

### Post by Monotoko on 2009-04-28
Right, this is what you need to do.

Grab a Windows disk, Windows XP SP3 or Windows Vista SP1 depending on which your running, Install Windows to a differant folder, when it asks for a product key, just click next, you will only be using it briefly, therefore dont need a product key.

Now go into the registry of the original installation (thats got the BSOD's) and go to the entry: HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl

set that to 0

then reboot, now try and boot up the original one with the BSOD, the BSOD will stay there, record what it says, and go post it on a windows forum somewhere ;)

---

### Post by sL8 on 2009-04-28
GRUB does show up. And now windows XP does too.
I had to edit the menu.lst to have windows xp show.

I don't have a windows XP sp3 or vista sp1 disk, only the restore cd's that geek squad made for the laptop.

I know, im stupid for not backing up my files.

---

### Post by f37u5g0d on 2009-04-29
If you can boot linux you should boot it (usually a good idea) mount your windows drive and grab all you files.  Save them to the ubuntu partition, or an external hard drive, or a CD / DVD or a bunch of jump drives or something but the point is you can access 100% of your files through ubuntu.

---

### Post by Kareeser on 2009-04-29
> **f37u5g0d said:**
> If you can boot linux you should boot it (usually a good idea) mount your windows drive and grab all you files.  Save them to the ubuntu partition, or an external hard drive, or a CD / DVD or a bunch of jump drives or something but the point is you can access 100% of your files through ubuntu.

He's already tried. Ubuntu won't mount his NTFS partition.

It sounds like you did a resize of your Windows drive to install Ubuntu, is that correct?

---

### Post by sL8 on 2009-04-29
This is what happened:
There was 3 partitions on it.
Windows
HP Recovery
and this last one which I believed went to the Tune-Up Backup. 
Anyway, to my knowledge, I deleted the HP Recovery and the Tune-Up Backup.

---

### Post by sL8 on 2009-05-01
I know doing this is wrong, but it was getting a little back there in the threads.
[bump]

---

### Post by egalvan on 2009-05-01
Download PartedMagic LiveCD

I prefer it over the Ubuntu LiveCD,
or Knoppix

[http://partedmagic.com/](http://partedmagic.com/)

this is a fairly complete distro,
it runs from the CD...
Full network (internet using FireFox)

And it sees NTFS...

I use it to set up partitions prior to loading Linux,
and to check Windows boxes...

And, yes, I have donated to the author...
it is well worth the $10 "tip" I sent... :)

ErnestTG

---

