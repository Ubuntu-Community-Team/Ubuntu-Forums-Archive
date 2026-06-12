---
title: "can't access to encrypted files"
date: 2009-05-21
forum: General Help
---

### Post by fduppa on 2009-05-21
Hi. Few days ago, I was using 9.04 with home folder encrypted.. then I decided to try 9.10 Alpha 1... annd then decided to go back to 9.04

To do this, I installed *buntu again without formatting my /home partition, and created a new username (lets say BuserB).

Then I created a username with the same name as the old account (AuserA).

When I login with AuserA I have the default skeleton, and the 2 files, README.TXT and the "Acces-your-private-data".

So, after reading the README, i opened the ACCESS YOUR PRIV....
and nothing.

So went to console, and typed

> $ ecryptfs-mount-private
receiving this output
> ERROR: Encrypted Private is not setup properly

If i look at the size of the folders.. I can tell that my files are still there, thou i dunno how to access to them.

If it helps, I DO have the passphrase, and I also DO have the unwrapped passhfrase (the long thing like b243b5b2b2f3d5e22d3f2d2a43b1b4) but I really don't know what should I do next.

Any suggestions? thanks in advance.. ):P

PS: I promise to back-up everything next time ;)

---

### Post by Soul-Sing on 2009-05-21
give this a try...fingers crossed here...

example sda1 partition is your homepartition with private map:

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount -o bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount -o bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# su - yourname
keyctl_search: Required key not available
Perhaps try the interactive 'ecryptfs-mount-private'
name@ubuntu:~$ ecryptfs-mount-private 
Enter your login passphrase

---

### Post by fduppa on 2009-05-21
nope.. it didn't work..

I have noticed that I DO NOT have the .ecryptfs folder.. I guess I'm pretty much screwed up.

The files are not big deal, so I'll wait a few days before deleting the folder.. just in case someone comes with a magic solution haha.

Thanks for trying anyway :-)

---

### Post by Soul-Sing on 2009-05-21
'./ecryptfs private' is missing?

---

### Post by jsenlai on 2009-06-09
I think my problem is kind of the same. I did clean install and too bad I didn't do any backup. 

I did set the old /home folder as new /home and didn't do format on the partition but did change the Ext3 to Ext4. 

Now I"m running 9.04 but I can't find my old /home anywhere.

Tried the tips above but no result.

Rgrds,

---

### Post by JanHolbo on 2009-09-28
I have a similar situation. I tried lequant's solution but it dies when I try to chroot with "chroot: cannot run command '/bin/bash': No such file or directory'

I do have the .Private directory though.

I know that I installed the original installation from an alternate CD and that ecryptfs is standard there. The new 9.04 installation was done with the live DVD thus I had to install ecryptfs-utils manually which might be my problem. Will get back to you when I have had a chance to re-install with alternate cd.

Jan

---

### Post by unutbu on 2009-09-28
JanHolbo, I think if you ran
```

sudo mount /dev/sda1 /mnt
...
sudo chroot /mnt
```

and receive the error
```

chroot: cannot run command '/bin/bash
```

it means that /dev/sda1 does not contain /bin/bash. Are you sure /dev/sda1 is your root partition?
If not, you can perhaps find out which is your root partition by typing
```

sudo fdisk -l     # reports your partition table


```

---

### Post by JanHolbo on 2009-09-29
> **unutbu said:**
> JanHolbo, I think if you ran
```

sudo mount /dev/sda1 /mnt
...
sudo chroot /mnt
```

and receive the error
```

chroot: cannot run command '/bin/bash
```

it means that /dev/sda1 does not contain /bin/bash. Are you sure /dev/sda1 is your root partition?
If not, you can perhaps find out which is your root partition by typing
```

sudo fdisk -l     # reports your partition table


```
It was the root dir, so I am not sure why it did not work.

I have since reinstalled but have the same problem ....

---

### Post by JanHolbo on 2009-09-29
> **JanHolbo said:**
> I have a similar situation. I tried lequant's solution but it dies when I try to chroot with "chroot: cannot run command '/bin/bash': No such file or directory'

I do have the .Private directory though.

I know that I installed the original installation from an alternate CD and that ecryptfs is standard there. The new 9.04 installation was done with the live DVD thus I had to install ecryptfs-utils manually which might be my problem. Will get back to you when I have had a chance to re-install with alternate cd.

Jan
I reinstalled using the Ubuntu alternate CD, formatting the root dir and creating a new user (UserB), setting up his /home as encrypted.

Logging into this user(UserB) I made a second user resembling the original by using the same username (UserA) but with a different /home dir (/home/UserA1)as this is the only way to create this user (as the original /home/user dir (/home/UserA) still exists. Then I logged into a text console (<CTRL><SHIFT><F1>), logged in as the super user (UserB) and did a

```
$ sudo chown -R UserA.UserA /home/UserA
```I did this, as the original dir (/home/UserA) had UID=1000,GID=1000 the same as the new super user (UserB)

I then modified the /home directory entry in the GUI User admin tool (menu: System -> Administration -> Users and Groups from /home/UserA1 to /home/UserA

Logging into this user in the gdm just gived the usual blank screen. Logging into a text console reveals the following files (ls -la)

```
lrwxrwxrwx  1 UserA UserA 56 2009-07-13 18:39 Access-Your-Private-Data.desktop -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.desktop
drwxr-xr-x  2 UserA UserA 4096 2009-09-25 22:05 .cache
lrwxrwxrwx  1 UserA UserA 21 2009-07-13 18:39 .ecryptfs -> /var/lib/ecryptfs/UserA
drwx------ 73 UserA UserA 24576 2009-09-25 22:02 .Private
lrwxrwxrwx  1 UserA UserA 52 2009-07-13 18:39 README.txt -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.txt
```Now something starts to hit me .... as I did a reinstall using a new user as the superuser UserB /var/lib/ecryptfs/UserA does not exist. How and with what do i populate this dir? Or is it easier to reinstall again just using UserA as the super user during the install?

Jan

---

### Post by unutbu on 2009-09-29
Are you trying to recover your home dir data, or is it already backed up?

If your encrypted files are in ~/.Private, have you tried
```

sudo mount -t ecryptfs ~/.Private ~/Private
```

Note that sudo might ask for the superuser password first. This may or may not be the same as your ecryptfs passphrase. You'll then be asked a few questions. The defaults are to select 1 (passphrase), enter your passphrase and then just hit Enter for the other questions.

---

### Post by JanHolbo on 2009-09-29
Hi!

```
$ sudo mount -t ecryptfs ~/.Private ~/Private
[sudo] password for UserA: 
Passphrase: 
Select cipher: 
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 2) blowfish: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24 (not loaded)
 4) twofish: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 5) cast6: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 6) cast5: blocksize = 8; min keysize = 5; max keysize = 16 (not loaded)
Selection [aes]: 
Select key bytes: 
 1) 16
 2) 32
 3) 24
Selection [16]: 
Enable plaintext passthrough (y/n) [n]: 
Enable filename encryption (y/n) [n]: 
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=0123456789abcdef
WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt],
it looks like you have never mounted with this key 
before. This could mean that you have typed your 
passphrase wrong.

Would you like to proceed with the mount (yes/no)?
```

I decided not to continue. What are the default settings for the above?

Jan

---

### Post by unutbu on 2009-09-29
My understanding of how ecryptfs works is slim-to-none here.
I believe /root/.ecryptfs/sig-cache.txt usually contains a hash of your passphrase.
Since you reinstalled, this might have wiped out your old /root/.ecryptfs/sig-cache.txt.
That would make your current /root/.ecryptfs/sig-cache.txt empty, or perhaps it only contains a different hash, unrelated to your old hash/passphrase.

I would not give up hope yet, however. I think if you say yes to the question
```

Would you like to proceed with the mount (yes/no)?
```

then a hash of your passphrase will be added to /root/.ecryptfs/sig-cache.txt 
and if it is the correct passphrase for your data, then the data will be decrypted properly.

---

### Post by JanHolbo on 2009-09-30
> **unutbu said:**
> My understanding of how ecryptfs works is slim-to-none here.
I believe /root/.ecryptfs/sig-cache.txt usually contains a hash of your passphrase.
Since you reinstalled, this might have wiped out your old /root/.ecryptfs/sig-cache.txt.
That would make your current /root/.ecryptfs/sig-cache.txt empty, or perhaps it only contains a different hash, unrelated to your old hash/passphrase.

I would not give up hope yet, however. I think if you say yes to the question
```

Would you like to proceed with the mount (yes/no)?
```

then a hash of your passphrase will be added to /root/.ecryptfs/sig-cache.txt 
and if it is the correct passphrase for your data, then the data will be decrypted properly.
The reason I am hesitating to continue is: will it crash my current set of files? Right now I am in moving boxes and cannot offload the content to a bigger drive, so I am living with running on a temporary solution, unless I stumble upon a safe and easy fix. And I do not have a lot of time to do the research at the moment, again related to my living situation.

But Thank You to anybody and everybody that works on this! :-)

Jan

---

### Post by unutbu on 2009-09-30
JanHolbo, there is danger when running a system without backups.
Even more so when the data is encrypted. The safest thing to do is wait until you can backup your data so nothing that you try can ruin you completely.

Edit: According to [https://help.ubuntu.com/community/EncryptedPrivateDirectory#Setup](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Setup) if you see
> ```

WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt],
it looks like you have never mounted with this key
before. This could mean that you have typed your
passphrase wrong.
```

It is safe to ignore this warning.

---

### Post by serpantman on 2009-11-21
I am actually going through the the same problem. The last advice using the mount command with the -t ecryptfs is working! It's mounting the data but its still encrypted. I know i have the right passphrase cause i used it to when mounting /. That and i remember it. Im guessing i must have the cypher or cypher strength wrong. I'm going to be looking for where this information is stored, i was wasn't prompted the first time when mounting /, so i know its stored somewhere. If anyone knows where, or another way to get this info please tell. I thought i went with defaults but i tried all the aes options.

Also, any other options that might work? For example, do a reinstall on a seperate partition, then copying the .Private i want to access over top of the new one? This will only work if i used the default options. Maybe if i reinstall grub if i configure it correctly? Sadly i never looked at how it was configured. Overwriting it is why im in this situation in the first place.

---

### Post by unutbu on 2009-11-21
serpantman, perhaps this will help: [http://www.kaijanmaki.net/blog/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/](http://www.kaijanmaki.net/blog/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/)

---

