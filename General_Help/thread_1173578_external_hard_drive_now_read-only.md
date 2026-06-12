---
title: "external hard drive now read-only"
date: 2009-05-29
forum: General Help
---

### Post by MeanStreak on 2009-05-29
Hi,

I went to do my usual backup to my external hard drive and received a failure message. My external hard drive is now read-only. Could someone please post a fix? 

Cheers

meanstreak

---

### Post by salvachn on 2009-05-29
Maybe it has overheated and so become unstable. It has happened to me twice. Let it cool down for a while. If you want it quick, put it in the freezer. After that it'll become alright. I did the same when this situation arose. If it is a software problem then you can use become root and edit it.

---

### Post by MeanStreak on 2009-05-29
Thanks - this is a software problem. I need instructions on how to modify the permissions on the drive so I can write to it.

---

### Post by MeanStreak on 2009-05-30
Still no answers? Could someone please provide me with a fix - I need to urgently backup my files.:(

---

### Post by jowilkin on 2009-05-30
How do you mount the drive?  Do you just plug it in and let it automount?  Or have you put a line in your fstab to mount it for you?

I would think manually mounting the drive as read-write should fix things.

First figure out what the drive is recognized as by the OS.  My external drive is /dev/sdb1.  If it's mounted now you should be able to check in the terminal with the command ```
df
```

If it's not mounted you can see all drives on the system with ```
sudo fdisk -l
```

If that goes ok, you know its being recognized properly and we can tell you what to do next.

Easiest way is probably to unmount it with ```
sudo umount /path/to/disk
```

Then remount it forcing it be read-write with something like ```
sudo mount -w /dev/sdb1 /where/you/want/it/mounted
```
If your disk is not /dev/sdb1, replace that with what it is on your system.

If that doesn't solve things, then you may need to modify the permissions of the directories on the drive.  Something like ```
sudo chmod -R +rw /path/to/drive
``` will make all files on the drive read-write for all users.  This may not be what you want.  With a more detailed description of what you want, you can get more precise help.

---

### Post by MeanStreak on 2009-05-30
Hi thanks very much for the post. Okay, I unmounted the drive (/dev/sdc1) and then re-mounted it then changed the permissions using the chmod command. Still no joy.

---

### Post by MeanStreak on 2009-05-30
It gets better - now when I turn the HDD on again - I cannot mount it at all.

---

### Post by jowilkin on 2009-05-30
Never had that happen, here is another thread on that issue [http://ubuntuforums.org/showthread.php?t=1048101](http://ubuntuforums.org/showthread.php?t=1048101)

---

### Post by rumplestilts on 2009-05-30
I used this command after I first connected a drive that had been intialized:

chown -R username:username /media/drivelabel

(where "username" is my login username and "drivelabel" is the actual name of the volume)

This made the drive "mine" so I could write to it.

---

### Post by MeanStreak on 2009-05-31
> **rumplestilts said:**
> I used this command after I first connected a drive that had been intialized:

chown -R username:username /media/drivelabel

(where "username" is my login username and "drivelabel" is the actual name of the volume)

This made the drive "mine" so I could write to it.

Thanks. On another post I found this command

```
sudo mv /media/.hal-mtab /media/.hal-mtab.anything
``` which enabled me to mount the drive. Then I ran 
```
chown -R charles:charles /media/disk
```. However I still cannot write to the external drive. This is beginning to boil my blood.

---

### Post by rcmx on 2009-05-31
ive the EXACT same problem..
i dont know what to do

just curious, did you install ubuntu or are you on a live cd?

---

### Post by rumplestilts on 2009-05-31
> **MeanStreak said:**
> Thanks. On another post I found this command

```
sudo mv /media/.hal-mtab /media/.hal-mtab.anything
``` which enabled me to mount the drive. Then I ran 
```
chown -R charles:charles /media/disk
```. However I still cannot write to the external drive. This is beginning to boil my blood.

Did you substitute the name of your drive for "disk"?

---

### Post by MrWES on 2009-05-31
> **MeanStreak said:**
> Thanks - this is a software problem. I need instructions on how to modify the permissions on the drive so I can write to it.

Can you please open an terminal and post back to the forums the results of this command? We need to see where the mount point of the drive is:
```
df
```

~Bill

Damn...chimed in late on this one....

---

### Post by drs305 on 2009-05-31
I spent an hour or more via a thread, PM and IM last night working on a very similar issue, which is still unresolved.
[http://ubuntuforums.org/showthread.php?t=1174176]("http://ubuntuforums.org/showthread.php?t=1174176")

What is the format of the device? Using chown won't work on non-linux file systems as the permissions/ownership is set at the time the device is mounted. 

In the thread I linked, it is a FAT32 My Book. After much searching, it appears that these devices get corrupted, especially with unclean unmounting. In almost every post I found, the only way to resolve the issue was to back up the data somewhere and then reformat the drive.

A better solution would be most welcome as there are a lot of posts of this nature throughout the internet support groups.

---

### Post by rumplestilts on 2009-05-31
> **drs305 said:**
> {snip}...Using chown won't work on non-linux file systems as the permissions/ownership is set at the time the device is mounted...{snip}

I used it for an HFS+ hard drive connected via USB. However, this does classify it as a "Linux-type" filesystem, I guess.

---

### Post by MeanStreak on 2009-06-06
> **MrWES said:**
> Can you please open an terminal and post back to the forums the results of this command? We need to see where the mount point of the drive is:
```
df
```

~Bill

Damn...chimed in late on this one....

Hi Bill,

Result of ```
df
``` command is as follows:

```
charles@charles-desktop:~$ df
Filesystem           1K-blocks Used Available Use% Mounted on
/dev/sda2             68025748  46869892  18391392  72% /
tmpfs                   513308         0    513308   0% /lib/init/rw
varrun                  513308       128    513180   1% /var/run
varlock                 513308         0    513308   0% /var/lock
udev                    513308       164    513144   1% /dev
tmpfs                   513308       120    513188   1% /dev/shm
lrm                     513308      2392    510916   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sdb1            106095516  67547804  33158308  68% /home
/dev/sda1             46082416  45471588    610828  99% /media/sda1

```

---

### Post by MeanStreak on 2009-06-06
> **drs305 said:**
> I spent an hour or more via a thread, PM and IM last night working on a very similar issue, which is still unresolved.
[http://ubuntuforums.org/showthread.php?t=1174176]("http://ubuntuforums.org/showthread.php?t=1174176")

What is the format of the device? Using chown won't work on non-linux file systems as the permissions/ownership is set at the time the device is mounted. 

In the thread I linked, it is a FAT32 My Book. After much searching, it appears that these devices get corrupted, especially with unclean unmounting. In almost every post I found, the only way to resolve the issue was to back up the data somewhere and then reformat the drive.

A better solution would be most welcome as there are a lot of posts of this nature throughout the internet support groups.

Mine is also a Western Digital MyBook as it happens - FAT32 format. Looks like I'll have to reformat the drive.

---

### Post by bjaz on 2009-09-17
i'm getting the same issue, on all my external drives in any format.
wasn't like this before, it just "happened", maybe after the media was badly disconnected.

i hate to call for attention but i've been stuck for days now, and not getting any answers, here or elsewhere

[http://ubuntuforums.org/showthread.php?t=1268043](http://ubuntuforums.org/showthread.php?t=1268043)

help

---

### Post by scouser73 on 2009-09-17
Go to **Terminal**, copy & paste this command: **gksudo nautilus**

That will open Terminal as root, navigate to your new drive, **Right Click**, select the **Permissions** tab change the **Owner** drop-down menu to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write**, **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your drive.

---

### Post by bjaz on 2009-09-18
thanks for your help, but it didn't work.

i get the following error when trying to change the owner, from the window which pops up after gksudo nautilus

Désolé, impossible de changer le propriétaire de « pocket_ » : Erreur lors de la définition du propriétaire : Système de fichiers accessible en lecture seulement

which translates as "impossible to the change the owner of "pocket" : error in the owner definition : file system is accessible as read-only only.

in the terminal, i get the following weirdness after typing gksudo nautilus :

-------------------------------------------------

kayo@kayogoro:~$ gksudo nautilus

--- Hash table keys for warning below:
--> file:///root
--> file:///media/pocket_

(nautilus:7767): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 2 elements at quit time (keys above)

(nautilus:7767): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 2 elements at quit time
SSSSSSSSSSSSSSSkayo@kayogoro:~$ gksudo nautilus

** (nautilus:7799): WARNING **: Unable to add monitor: Opération non prise en charge
^C
kayo@kayogoro:~$

---

### Post by bjaz on 2009-09-20
bump ?

---

### Post by bjaz on 2009-09-26
bump bump ?

can anyone help ? please

---

### Post by scouser73 on 2009-09-26
Double Post, sorry

---

### Post by CoolDreamZ on 2009-10-07
I had similar problems which were due to the drive being unsafely removed on my Windows system - if you just unplug a drive on Windows it can be marked as "in use" - when Linux automounts the drive it sees this and mounts it as read-only for safety. A quick solution (if you have access to Windows) is to plug the drive into a windows box and remove it properly it should then mount ok on Linux. If you are still having problems then please post the output of the "mount" command here...

---

### Post by tyk on 2009-11-13
> **CoolDreamZ said:**
> I had similar problems which were due to the drive being unsafely removed on my Windows system - if you just unplug a drive on Windows it can be marked as "in use" - when Linux automounts the drive it sees this and mounts it as read-only for safety. A quick solution (if you have access to Windows) is to plug the drive into a windows box and remove it properly it should then mount ok on Linux. If you are still having problems then please post the output of the "mount" command here...

That did the trick. Thanks.

---

