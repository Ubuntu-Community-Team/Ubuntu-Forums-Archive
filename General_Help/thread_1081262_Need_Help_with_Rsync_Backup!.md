---
title: "Need Help with Rsync Backup!"
date: 2009-02-26
forum: General Help
---

### Post by utherpendragonfly on 2009-02-26
I have a new external HD and I'm using rsync to back up /home. The problem is I thought the path to external drive is /media/Back-up. I made 2 partitions, Back-up and Storage, which both appear with those names on my desktop. I entered terminal command: <rsync -av /home/davey /media/Back-up> and now it is copying /home to my internal HD instead of external HD. 
In /media there is a folder <sdb1> as well as <Back-up> & <Storage>. I'm confused because there is no </media/sdb1/Back-up>. What should I have entered to backup to? And how do you stop terminal from executing a command? I don't want backup on sda1!

---

### Post by utherpendragonfly on 2009-02-26
OK, I just closed terminal window and stopped the backup.
When I open the Back-up drive icon on the desktop, it is empty, shows 0 of 55 Gb. available. And in Filesystem/media/Back-up is where my home folder was being copied. This doesn't make sense to me. Shouldn't Back-up be in the /media/sdb1 folder instead of /media/Back-up?

---

### Post by binbash on 2009-02-26
Stop messing with rsync command.Install Grsync, you can browse the output directory etc  :)

---

### Post by Cybie257 on 2009-02-26
> **utherpendragonfly said:**
> I have a new external HD and I'm using rsync to back up /home. The problem is I thought the path to external drive is /media/Back-up. I made 2 partitions, Back-up and Storage, which both appear with those names on my desktop. I entered terminal command: <rsync -av /home/davey /media/Back-up> and now it is copying /home to my internal HD instead of external HD. 
In /media there is a folder <sdb1> as well as <Back-up> & <Storage>. I'm confused because there is no </media/sdb1/Back-up>. What should I have entered to backup to? And how do you stop terminal from executing a command? I don't want backup on sda1!


My first suggestion is to go into a terminal windows and type "df". Where you see the names "Back-up & Storage", see what file-system they are mounting to.. Post the output to that so others can see what's going on.

As for the rsync command you are typing, that should be correct, but all depends on the first part of my reply as to why it's not working.

to stop RSync from copying, type "ps -ef | grep rsync" this will give you the PID of the rsync command. be careful to not confuse the rsync PID that you entered. When you type "ps -ef | grep rsync", you will likely see a process called grep rsync. disregard that one and do a "kill 'PID#'", where PID# is the PID listed. If it doesn't let you kill it that way, do "kill -9 PID#". The -9 forces a kill process. Also, you may need to sudo that, but not sure. I usually 'sudo -i' to get a root prompt before doing any administration on my system to avoid permission issues.

-Cybie

---

### Post by utherpendragonfly on 2009-02-26
davey@davey-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            715107812 157824272 520958168  24% /
tmpfs                  1036428         0   1036428   0% /lib/init/rw
varrun                 1036428       124   1036304   1% /var/run
varlock                1036428         0   1036428   0% /var/lock
udev                   1036428      2772   1033656   1% /dev
tmpfs                  1036428      1172   1035256   1% /dev/shm
lrm                    1036428      2004   1034424   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sdb1             61535944    184264  58225836   1% /media/Backup
/dev/sdb2            419183140    203080 397686708   1% /media/Storage

Now I'm more confused. The Label I gave the partition in GParted is "Back-up", but this shows "Backup". And the Desktop icon is "Back-up". 
Here are a couple of screenshots:

---

### Post by taurus on 2009-02-26
Label and mount point are two different things.  You mount your /dev/sdb1 to /media/Backup from /etc/fstab.

---

### Post by utherpendragonfly on 2009-02-26
Maybe I should also check ou Grsync. I've seen it, but thought this would be easy.
I'd just like to understand what exactly the mount point is to access these partitions.

---

### Post by utherpendragonfly on 2009-02-26
Thanks taurus. I thought I was done with this.
I looked in fstab and changed Backup to Back-up. So If I do rsync again would I copy to /media/Back-up and it should work?

---

### Post by taurus on 2009-02-26
After you edited /etc/fstab, did you remount your /dev/sdb1?  Otherwise, it is still being mounted to /media/Backup.

```
sudo umount /dev/sdb1
sudo mount -a
df -h
```

---

### Post by utherpendragonfly on 2009-02-26
But I'm still confused why there is a "sdb1" folder in "/" and why it is empty. Can I delete it? and delete "/media/Backup"?

---

### Post by taurus on 2009-02-26
What's the output of this command from a terminal?

```
ls -la /
```

---

### Post by utherpendragonfly on 2009-02-26
> **taurus said:**
> After you edited /etc/fstab, did you remount your /dev/sdb1?  Otherwise, it is still being mounted to /media/Backup.

```
sudo umount /dev/sdb1
sudo mount -a
df -h
```

I just did that. Now I'll retry the backup with rysnc from /davey/home to /media/Back-up.

---

### Post by utherpendragonfly on 2009-02-26
> **taurus said:**
> What's the output of this command from a terminal?

```
ls -la /
```

davey@davey-desktop:~$ ls -la /
total 100
drwxr-xr-x  21 root root  4096 2009-02-15 19:02 .
drwxr-xr-x  21 root root  4096 2009-02-15 19:02 ..
drwxr-xr-x   2 root root  4096 2009-01-11 18:47 bin
drwxr-xr-x   3 root root  4096 2009-01-30 02:49 boot
lrwxrwxrwx   1 root root    11 2008-10-21 10:53 cdrom -> media/cdrom
drwxr-xr-x  14 root root 14220 2009-02-26 07:15 dev
drwxr-xr-x 152 root root 12288 2009-02-26 11:07 etc
drwxr-xr-x   4 root root  4096 2009-01-17 18:33 home
lrwxrwxrwx   1 root root    33 2009-01-28 08:56 initrd.img -> boot/initrd.img-2.6.27-11-generic
lrwxrwxrwx   1 root root    32 2008-11-30 09:32 initrd.img.old -> boot/initrd.img-2.6.27-9-generic
drwxr-xr-x  17 root root 12288 2009-02-11 08:44 lib
drwx------   2 root root 16384 2008-10-21 10:53 lost+found
drwxr-xr-x   8 root root  4096 2009-02-26 09:40 media
drwxr-xr-x   3 root root  4096 2008-12-02 18:19 mnt
drwxr-xr-x   5 root root  4096 2009-01-15 15:44 opt
dr-xr-xr-x 184 root root     0 2009-02-25 17:13 proc
drwxr-xr-x  23 root root  4096 2009-02-26 11:03 root
drwxr-xr-x   2 root root  4096 2009-02-15 10:06 sbin
drwxr-xr-x   2 root root  4096 2008-10-01 15:57 srv
drwxr-xr-x   2 root root  4096 2009-02-15 19:02 storage
drwxr-xr-x  12 root root     0 2009-02-25 17:13 sys
drwxrwxrwt  22 root root  4096 2009-02-26 11:03 tmp
drwxr-xr-x  13 root root  4096 2008-12-11 19:46 usr
drwxr-xr-x  16 root root  4096 2008-12-05 08:26 var
lrwxrwxrwx   1 root root    30 2009-01-28 08:56 vmlinuz -> boot/vmlinuz-2.6.27-11-generic
lrwxrwxrwx   1 root root    29 2008-11-30 09:32 vmlinuz.old -> boot/vmlinuz-2.6.27-9-generic
davey@davey-desktop:~$

---

### Post by taurus on 2009-02-26
> **utherpendragonfly said:**
> davey@davey-desktop:~$ ls -la /
total 100
drwxr-xr-x  21 root root  4096 2009-02-15 19:02 .
drwxr-xr-x  21 root root  4096 2009-02-15 19:02 ..
drwxr-xr-x   2 root root  4096 2009-01-11 18:47 bin
drwxr-xr-x   3 root root  4096 2009-01-30 02:49 boot
lrwxrwxrwx   1 root root    11 2008-10-21 10:53 cdrom -> media/cdrom
drwxr-xr-x  14 root root 14220 2009-02-26 07:15 dev
drwxr-xr-x 152 root root 12288 2009-02-26 11:07 etc
drwxr-xr-x   4 root root  4096 2009-01-17 18:33 home
lrwxrwxrwx   1 root root    33 2009-01-28 08:56 initrd.img -> boot/initrd.img-2.6.27-11-generic
lrwxrwxrwx   1 root root    32 2008-11-30 09:32 initrd.img.old -> boot/initrd.img-2.6.27-9-generic
drwxr-xr-x  17 root root 12288 2009-02-11 08:44 lib
drwx------   2 root root 16384 2008-10-21 10:53 lost+found
drwxr-xr-x   8 root root  4096 2009-02-26 09:40 media
drwxr-xr-x   3 root root  4096 2008-12-02 18:19 mnt
drwxr-xr-x   5 root root  4096 2009-01-15 15:44 opt
dr-xr-xr-x 184 root root     0 2009-02-25 17:13 proc
drwxr-xr-x  23 root root  4096 2009-02-26 11:03 root
drwxr-xr-x   2 root root  4096 2009-02-15 10:06 sbin
drwxr-xr-x   2 root root  4096 2008-10-01 15:57 srv
drwxr-xr-x   2 root root  4096 2009-02-15 19:02 storage
drwxr-xr-x  12 root root     0 2009-02-25 17:13 sys
drwxrwxrwt  22 root root  4096 2009-02-26 11:03 tmp
drwxr-xr-x  13 root root  4096 2008-12-11 19:46 usr
drwxr-xr-x  16 root root  4096 2008-12-05 08:26 var
lrwxrwxrwx   1 root root    30 2009-01-28 08:56 vmlinuz -> boot/vmlinuz-2.6.27-11-generic
lrwxrwxrwx   1 root root    29 2008-11-30 09:32 vmlinuz.old -> boot/vmlinuz-2.6.27-9-generic
davey@davey-desktop:~$

I don't see any sdb1 in / as you described in post #10.

---

### Post by utherpendragonfly on 2009-02-26
> **taurus said:**
> I don't see any sdb1 in / as you described in post #10.

No, it is in /media

---

### Post by utherpendragonfly on 2009-02-26
> **utherpendragonfly said:**
> No, it is in /media

See post #5

---

### Post by taurus on 2009-02-26
> **utherpendragonfly said:**
> No, it is in /media

I believe that was the one you created before you split your WD into two partitions.  If you don't want it anymore, you can remove it.

```
sudo rmdir /media/sdb1
ls -la /media
```

---

### Post by utherpendragonfly on 2009-02-26
> **taurus said:**
> I believe that was the one you created before you split your WD into two partitions.  If you don't want it anymore, you can remove it.

```
sudo rmdir /media/sdb1
ls -la /media
```

Aaahhh. Thanks. So I'll try rsync again and see what happens.

---

### Post by Cybie257 on 2009-02-26
> **utherpendragonfly said:**
> davey@davey-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            715107812 157824272 520958168  24% /
tmpfs                  1036428         0   1036428   0% /lib/init/rw
varrun                 1036428       124   1036304   1% /var/run
varlock                1036428         0   1036428   0% /var/lock
udev                   1036428      2772   1033656   1% /dev
tmpfs                  1036428      1172   1035256   1% /dev/shm
lrm                    1036428      2004   1034424   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sdb1             61535944    184264  58225836   1% /media/Backup
/dev/sdb2            419183140    203080 397686708   1% /media/Storage

Now I'm more confused. The Label I gave the partition in GParted is "Back-up", but this shows "Backup". And the Desktop icon is "Back-up". 
Here are a couple of screenshots:


Based on what I see here, if you selected your destination to be /media/Backup, it 'should' copy to your External drive (sdb1). Not sure where the Back-up folder is coming from, but it's not from sdb1. 

Also, have you unmounted those folders from your desktop? Right-Click Unmount? Plus, try unmounting your external drive and unplugging it then plug it back in. See what shows up on your desktop. Generally, you should see the folders show up on the desktop. Not sure waht else to say since your 'df' output shows that you have a Backup (not Back-up) folder/partition on the sdb device.

-Cybie

---

### Post by utherpendragonfly on 2009-02-26
> **Cybie257 said:**
> Based on what I see here, if you selected your destination to be /media/Backup, it 'should' copy to your External drive (sdb1). Not sure where the Back-up folder is coming from, but it's not from sdb1. 

Also, have you unmounted those folders from your desktop? Right-Click Unmount? Plus, try unmounting your external drive and unplugging it then plug it back in. See what shows up on your desktop. Generally, you should see the folders show up on the desktop. Not sure waht else to say since your 'df' output shows that you have a Backup (not Back-up) folder/partition on the sdb device.

-Cybie

But I named it "Back-up" and not "Backup". I actually just removed "Backup".
Does that make sense?

---

### Post by utherpendragonfly on 2009-02-26
Under Places>  I have Back-up and Storage partitions.

---

### Post by Cybie257 on 2009-02-26
> **utherpendragonfly said:**
> But I named it "Back-up" and not "Backup". I actually just removed "Backup".
Does that make sense?

By removed, do you mean rmdir /media/Backup?

Here's the next step I'd do. shutdown the computer, unplug the drive (usb cable). boot up, check the /media folder. remove any of the form of Backup(or Back-up), and Storage, if there. Then, plug in the USB cable and allow it to mount. it should bring up folder icon to the desktop. regardless of than, re-run the 'df' command and see what shows up again. if it's /media/Backup and /media/Storage, then you will access sdb1 and sdb2 via those folders.
How did you 'name' the partition "back-up"? Did you just rename the folder that appeard on the desktop? or was that via the partitioner? 

-Cybie

---

### Post by utherpendragonfly on 2009-02-26
> **Cybie257 said:**
> By removed, do you mean rmdir /media/Backup?

Here's the next step I'd do. shutdown the computer, unplug the drive (usb cable). boot up, check the /media folder. remove any of the form of Backup(or Back-up), and Storage, if there. Then, plug in the USB cable and allow it to mount. it should bring up folder icon to the desktop. regardless of than, re-run the 'df' command and see what shows up again. if it's /media/Backup and /media/Storage, then you will access sdb1 and sdb2 via those folders.
How did you 'name' the partition "back-up"? Did you just rename the folder that appeard on the desktop? or was that via the partitioner? 

-Cybie

Yes, I removed /media/Backup using rmdir. I created the partition labels with Gparted

---

### Post by taurus on 2009-02-26
> **Cybie257 said:**
> By removed, do you mean rmdir /media/Backup?

Here's the next step I'd do. shutdown the computer, unplug the drive (usb cable). boot up, check the /media folder. remove any of the form of Backup(or Back-up), and Storage, if there. Then, plug in the USB cable and allow it to mount. it should bring up folder icon to the desktop. regardless of than, re-run the 'df' command and see what shows up again. if it's /media/Backup and /media/Storage, then **you will access sdb1 and sdb2 via those folders**.
How did you 'name' the partition "back-up"? Did you just rename the folder that appeard on the desktop? or was that via the partitioner? 

-Cybie

Don't mean to cut in here but they are not folders; they are directories.

---

### Post by utherpendragonfly on 2009-02-26
> **taurus said:**
> Don't mean to cut in here but they are not folders; they are directories.

Sorry... I'm used to Mac lingo.
I just tried rsync again without making any changes and it's backing up to external drive! Thank you everyone for assistance.

---

### Post by utherpendragonfly on 2009-02-26
One thing that just occured to me: My wife has a user account. Should I have backed up /home instead of /home/davey? Or could I do a separate backup of her user account when this finishes? I'm not sure how that works.

---

### Post by Roasted on 2009-02-26
> **utherpendragonfly said:**
> One thing that just occured to me: My wife has a user account. Should I have backed up /home instead of /home/davey? Or could I do a separate backup of her user account when this finishes? I'm not sure how that works.

Try rsyncing "home" only. After the rsync is done, check the external drive. Did it bring both folders? Davey + Wifey? If it brought /home with /davey + /wifey inside, you're golden. If not, post back and we'll help ya out.

Also, are you using a script? I have an rsync script set up that I run anytime I want to run a backup. I simply named it "backup"... so if I "sudo backup" in terminal, type in my PW, bam... script runs with my full rsync command without having to type it each time.

---

### Post by utherpendragonfly on 2009-02-26
> **Roasted said:**
> Try rsyncing "home" only. After the rsync is done, check the external drive. Did it bring both folders? Davey + Wifey? If it did, you're golden. If not, post back and we'll help ya out.

Darn! It's already copying away on /home/davey. Should I cancel or do a separate backup of wife's account?

---

### Post by utherpendragonfly on 2009-02-26
Or... should I let this finish and then do rsync again for /home and rewrite the whole thing. Or would rsync only write what has changed?

---

### Post by Cybie257 on 2009-02-26
> **taurus said:**
> Don't mean to cut in here but they are not folders; they are directories.

True, but some people refer to folders and directories the same. Good to call them what they are to keep the details accurate. :)

-Cybie

---

### Post by utherpendragonfly on 2009-02-26
Can anyone tell me what command I need so that I can always auto mount these partitions. I unmounted them and it says I don't have permissions to mount again. I used the chown command before, but I can't find how to always make them auto mount.

---

### Post by Roasted on 2009-02-26
I've got a couple ideas in my head here.

For one, you're using an external drive, so setting up the external drive in fstab doesn't seem like a viable option unless you have the external drive plugged in 247. 

What I would do is this... and I can help you more later cause I'm at work now but here's the jist of what I used to do in the past and what seems like it may work for you now.

Create a directory in /media... name it anything... "backup" is a decent one. 

Then that folder is always there for backup purposes.

Then I would make a bin/bash script for rsync backups. The scripts work line by line and won't continue to line 2 till line 1 is completed. So you'd simply have the mount command as line 1, and the rsync command as line 2.

sudo mount /dev/sdb1 /media/backup
sudo rsync /home/davey /media/backup
sudo rsync /home/wifey /media/backup

That's assuming /dev/sdb1 is your external drive, and that backup is what you name the folder.

So if you'd save the text file the same way I did and name it "backup", you'd have to assign proper executable rights to it, which I believe is sudo chmod +x /wherever/your/script/is, then presto.

Terminal - sudo backup - type password - and your script runs line by line.

Line 1 - Mount.
Line 2 - Davey's home directory gets backed up.
Line 3 - Wifey's home directory gets backed up.

Note - the only thing to be aware of is your drive ID. If for some reason your hard drive ID would change (which only occurs if you mess around with internal drives, normally) then you'd have to change your script. You would do this by plugging in your external drive, sudo fdisk -l to see all drives, find the new ID to your external, and put it in place of your old drive ID (/dev/sdb1 in my example) with the new one.

Save. Backup. Done.

I can help you more later on tonight. I'll be glad to assist in any way possible.


EDIT - I just got an idea in my head with the mounting question above. If you mount a drive to a directory, in the example I gave above /media/backup, wouldn't it "remember" to auto-mount there next time? Maybe you can get away from having the mount line in the script idea I have above if this is true. Maybe an Ubuntu Guru can chime in here and help me out on the gray area I just got in my head over this.

---

### Post by taurus on 2009-02-26
> **utherpendragonfly said:**
> Can anyone tell me what command I need so that I can always auto mount these partitions. I unmounted them and it says I don't have permissions to mount again. I used the chown command before, but I can't find how to always make them auto mount.

Didn't you already have two entries in /etc/fstab for /dev/sdb1 & /dev/sdb2?

```
sudo mount -a
df -h
```

---

### Post by Cybie257 on 2009-02-26
> **Roasted said:**
> 

EDIT - I just got an idea in my head with the mounting question above. If you mount a drive to a directory, in the example I gave above /media/backup, wouldn't it "remember" to auto-mount there next time? Maybe you can get away from having the mount line in the script idea I have above if this is true. Maybe an Ubuntu Guru can chime in here and help me out on the gray area I just got in my head over this.


BY experience, Ubuntu has always automounted my USB drives/removable media. I'm not sure if you have done so, but unplug the drive, maybe even reboot. after Ubuntu is up and runnning, plug the drive in. If that doesn't work, reboot with the drive plugged in. 

I'm just throwing this out there as a try since you haven't received a reply since your last post. Try to do a search on auto-mount USB storage and see what you can find. 

-Cybie

---

