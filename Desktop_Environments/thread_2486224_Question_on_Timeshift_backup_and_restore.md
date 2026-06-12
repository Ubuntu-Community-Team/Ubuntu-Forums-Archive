---
title: "Question on Timeshift backup and restore"
date: 2023-04-23
forum: Desktop Environments
---

### Post by John_Carver on 2023-04-23
[SIZE=3]I understand the application.  However, If the hard drive itself fails so goes the backup.  The key here is to place the backup on an outside source.  Now the question.,  How to install the backup file?  I assume a new hard drive and a Ubuntu install would be required.  This seems to be the only way to access the backup with Timeshift.  Will appreciate thoughts.[/SIZE]

---

### Post by #&amp;thj^% on 2023-04-23
I'm a bit confused on your info given, could use a wee bit more info.
First my practice with Timeshift is move the back-ups to another Drive in the beginning, or on first run. 
And this>>way to access the backup with Timeshift, You can with your Live-Installer>> install Timeshift and find your back-ups to restore.

So i guess it would be best to follow that first, after all if the Drive fails, how will you restore from your back-ups from a failed Drive.
I hope I'm close to what your asking.

---

### Post by John_Carver on 2023-04-23
[B][SIZE=3]Thanks
This is what I meant
Yes on the outside drive.  Accordingly, the Live-installer takes over.
Just wasn't familiar with that part.  [/SIZE][/B]

---

### Post by #&amp;thj^% on 2023-04-23
I have had a spinning drive fail, and was lucky enough to pull my back-ups off that drive with Timeshift installed in my Live-installer
 to a new drive, but I consider that as luck and not the Norm.
EDIT: Just to help in clarity, I first boot with the live-installer and then run:
```
sudo apt update
sudo apt install timeshift
```
Navigate to the stored back-ups with the newly installed Timeshift and run the restore.

---

### Post by ne29914 on 2023-04-23
I understand the question, and the whole issue is a bit "hairy".
I use Timeshift for taking snapshots of my system to my /home partition _and_ to an external disk.

The local /home backup is for when I'm playing around with settings, new installations etc. It'll restore the last state within minutes when I've mucked up.

The external disk backup is for serious situations, where my / is corrupted (bad HDD/SSD, my own incompetence/fiddling etc.). This always requires a new install followed by a Timeshift Restore.
This is where the fun begins. A new install will result in new UUIDs on the new drive. When you then do a Timeshift restore, you'll have a mismatch between new and old UUIDs.

Until now, I've only found two solutions to this:
1: modify the new HDD/SSD to have the old UUIDs using gparted (recommended). You'll need to do this from a live boot.
2: modify the relevant system files in the Timeshift backup (not recommended, dangerous).

Apart from that, Timeshift has _never_ let me down. :)

---

### Post by John_Carver on 2023-04-25
[SIZE=3]Thanks
I've covered a lot of ground since starting this
e.g.my thumb drive was fat32 not good
reset to ext4 good
My goal is an external backup for a hard drive failure (bound to append due to age)
Got too much invested to start over.  Years ago I started from real scratch with Red Hat (no experience)
Still, most of this I don't know but enjoy the challenge of exploring.
At what point do I do this: [/SIZE]1: modify the new HDD/SSD to have the old UUIDs using [SIZE=3]gparted[/SIZE]
I'ii be on the edge again when this happens

---

### Post by ne29914 on 2023-04-25
> **John_Carver said:**
> Thanks
At what point do I do this: 1: modify the new HDD/SSD to have the old UUIDs using gparted

Live boot + install with format (I strongly suggest separate ext4 partitions for / and /home). Install ends in a reboot to new system.
Live boot again and unmount the newly created partitions on the HDD/SSD.
Run:
```
e2fsck -f 'partition'
tune2fs -U 'UUID' 'partition'
```
Mount the new / partition and edit /etc/fstab to reflect the changed UUIDs.
Reboot from the new HDD/SSD.
Install Timeshift.
Run the Timeshift restore. The machine should reboot automatically after restore.

Now it should run. I've mulled a simpler recipe for this, but have found no good solution until now. You'll need to sudo all the steps above.

---

### Post by John_Carver on 2023-04-25
Thanks

---

