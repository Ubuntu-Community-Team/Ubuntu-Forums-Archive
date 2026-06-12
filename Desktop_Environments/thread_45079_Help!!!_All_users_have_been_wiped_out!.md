---
title: "Help!!! All users have been wiped out!"
date: 2005-06-28
forum: Desktop Environments
---

### Post by foxy123 on 2005-06-28
Have no idea what has happened. I have removed a package I compiled from source before and installed. Synaptic complained about something related to users and then sudo stopped working. I logged out and saw that there was no single user on the gdm login screen. I have rebooted and now I have not got anything.

The boot sequence has a lot of errors and than I am left with a black screen to login and no user name works so I cannot logon and check anything.

What should I do! It is so frustrating!

---

### Post by tread on 2005-06-28
Did you try to boot into recovery mode?

---

### Post by foxy123 on 2005-06-28
[QUOTE=tread]Did you try to boot into recovery mode?[/QUOTE]
yes, i did... no luck.. the problem is that all the info about existing users just disappeared so I cannot login... Is there a sort of master password? I even do not know what is wrong. If i knew I could boot from a live CD and fix it...

---

### Post by cwaldbieser on 2005-06-28
You can boot from a LiveCD, manually edit the /etc/password file to reactivate a user (probably root until you get your sudo powers back), and then boot back into the system.

---

### Post by foxy123 on 2005-06-28
[QUOTE=cwaldbieser]You can boot from a LiveCD, manually edit the /etc/password file to reactivate a user (probably root until you get your sudo powers back), and then boot back into the system.[/QUOTE]

I tried live CD few minutes ago. It did not mount any of my partitions. One thing, I do not remember which is which ( I have / and /home partitions and they are not just hda3 and hda4 but due to some manipulations like hada6 and hda8). Ok, I can try to mount all available ones, but how to create a mount point with live CD?

---

### Post by foxy123 on 2005-06-28
I booted from knoppix and found out that passwd file is missing from /etc There is only  passwd.lock, which I cannot open.

---

### Post by cwaldbieser on 2005-06-28
Basic steps for recovery:
1) mount your root partition with read and write permission.
2) Run the passwd command with chroot.

It looks like you managed to accomplish step 1.  Step 2 might be tricky-- it looks like your system got borked in the middle of setting a lock file for the passwd file.  You may have to remove this file (knoppix should let you do this with a combination of sudo, chmod, and rm).  I don't know if passwd will complain if /etc/passwd is missing or not.  If it won't automatically create the /etc/passwd file for you, from a root shell you could try "touch /etc/passwd" to create the empty file first.

Good luck!

---

### Post by foxy123 on 2005-06-29
[QUOTE=cwaldbieser]Basic steps for recovery:
1) mount your root partition with read and write permission.
2) Run the passwd command with chroot.

It looks like you managed to accomplish step 1.  Step 2 might be tricky-- it looks like your system got borked in the middle of setting a lock file for the passwd file.  You may have to remove this file (knoppix should let you do this with a combination of sudo, chmod, and rm).  I don't know if passwd will complain if /etc/passwd is missing or not.  If it won't automatically create the /etc/passwd file for you, from a root shell you could try "touch /etc/passwd" to create the empty file first.

Good luck![/QUOTE]
I cannot run any command without loging in, its the problem, and I cannot log in because there is no a single user in the system and root is not activated. 

I tried to use installation CD to add user, but it does not do it wiothout installing a base configuration, which fails... 
basically I have the following error:

> gdm user does not exists, please correct gdm configuration 

googling brought only one result in English describing two ways (it was not for Ubuntu). First was recovery mode - does not work for me... Another was to boot from CD1 and use 'linux -s', but I have no idea how to use it with Ubuntu...

---

### Post by foxy123 on 2005-06-29
I was thinking. If I lost all my users and groups config files because of this freaky accident, what if I install Ubuntu to another HD, using the /home partition from my dead installation and than just copy those config files from my new intall into my old one? The trouble is I do not know what files to copy if anyy and if it would work. Could anyone comment on that?

---

### Post by foxy123 on 2005-06-29
Well I have done what I mentioned above:

1. Installed Ubuntu on my second HD
2. Set up users as they were on my main installation
3. Copied the following files from a new /etc to an old /etc:
group
gshadow
passwd
shadow
sudoers
4. Edited menu.lst to add option to boot my old installation

And pretty much that's it. I had to change ownership of users homes, because they were messed up.

Now it works. Hopefully it will be fine.

The only question left is how to point grub to my old menu.list again, because it now uses menu.list from a second HD?

---

### Post by cwaldbieser on 2005-06-29
[QUOTE=foxy123]I cannot run any command without loging in, its the problem, and I cannot log in because there is no a single user in the system and root is not activated. 
[/QUOTE]

Sorry, maybe I am having trouble explaining this clearly.  The idea is that you boot the LiveCD (the one that runs off your CD ROM instead of the hard disk).  When the LiveCD boots, you are essentially in a mode like single-user mode. If you do a

```
$ sudo bash
```
You will get yourself a root shell, and effectively you will be root.  As root, you mount the hard disk.
```
# mount /dev/hda0 /mnt/hda0
```
You should be able to execute the passwd command at that point with chroot so that you are executing as the root user, but chroot fools the system into thinking that the directory you specify is the root of the filesystem.

I would have thought creating a new partition should have also let you chroot to fix the problem, but copying your /etc/passwd and /etc/shadow files should do the trick (as long as your users have the same user IDs).

---

### Post by foxy123 on 2005-06-30
[QUOTE=cwaldbieser]Sorry, maybe I am having trouble explaining this clearly.  The idea is that you boot the LiveCD (the one that runs off your CD ROM instead of the hard disk).  When the LiveCD boots, you are essentially in a mode like single-user mode. If you do a

```
$ sudo bash
```
You will get yourself a root shell, and effectively you will be root.  As root, you mount the hard disk.
```
# mount /dev/hda0 /mnt/hda0
```
You should be able to execute the passwd command at that point with chroot so that you are executing as the root user, but chroot fools the system into thinking that the directory you specify is the root of the filesystem.

I would have thought creating a new partition should have also let you chroot to fix the problem, but copying your /etc/passwd and /etc/shadow files should do the trick (as long as your users have the same user IDs).[/QUOTE]

yes, I got it. The trouble was that I could not do anything, because I did not have a single user in the system so it did not allow me to create a user after I chrooted into it. That's why I went in trouble to install another copy of Ububuntu. Thanks anyway.

---

