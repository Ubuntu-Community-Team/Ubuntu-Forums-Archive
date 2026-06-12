---
title: "sudo is messed up"
date: 2006-02-05
forum: Desktop Environments
---

### Post by philosophia on 2006-02-05
i might have messed my box up.  i have root login disabled, and i was trying to add another user to the sudoers group.  first i 'export EDITOR=gedit && sudo visudo'  then i added to the file 'system_usernameALL=(ALL) ALL'.  now none of my users can sudo.  

my grub menu is also disabled according to ubuntuguide.org, so i can't boot into rescue mode.

i can't even back everything up and reinstall.  /var/lib/mysql is owned by another user.

any way to fix this? or at least a way to backup mysql so i can reinstall?

---

### Post by codejunkie on 2006-02-05
[QUOTE=philosophia]i might have messed my box up.  i have root login disabled, and i was trying to add another user to the sudoers group.  first i 'export EDITOR=gedit && sudo visudo'  then i added to the file 'system_usernameALL=(ALL) ALL'.  now none of my users can sudo.  

my grub menu is also disabled according to ubuntuguide.org, so i can't boot into rescue mode.

i can't even back everything up and reinstall.  /var/lib/mysql is owned by another user.

any way to fix this? or at least a way to backup mysql so i can reinstall?[/QUOTE]
if you have a live cd handy put it in and boot to up when you reach the desktop open a terminal and enter ```
sudo fdisk -l
``` to list your partitons find your ubuntu partition and mount it like this ```
sudo mkdir /ubuntu
```
then ```
sudo mount /dev/hdxx
``` where xx would be your drive location and number then ```
sudo chroot /ubuntu
``` now you can run 
export EDITOR=gedit && sudo visudo and this will edit your sudoers file as root undo the changes you made and this should get sudo back up and running.
edit: you can also do this with the ubuntu install cd by typing rescue as the boot option but it's all done via command line for the command export EDITOR=gedit && sudo visudo you have to change "gedit" to "nano"
like this ```
export EDITOR=nano && sudo visudo
```

---

### Post by philosophia on 2006-02-05
do i need to know root password to boot into rescue mode?  i'm not at my machine right now - it's remote - but i can probably go there tomorrow.

---

### Post by codejunkie on 2006-02-05
[QUOTE=philosophia]do i need to know root password to boot into rescue mode?  i'm not at my machine right now - it's remote - but i can probably go there tomorrow.[/QUOTE]
if you set the root password previously then yes even though you have disabled the root account you will still need the old root password when using the rescue mode if you never enabled the root account with 
```
sudo passwd root
``` then you wouldn't need it.

---

### Post by philosophia on 2006-02-05
will i be able to do this if i previously set the root password to -1 to disable root logins?

---

### Post by codejunkie on 2006-02-05
[QUOTE=philosophia]will i be able to do this if i previously set the root password to -1 to disable root logins?[/QUOTE]
if you disable the root account with ```
sudo passwd root -l
```you should be able to enter the old root password and still login using the rescue mode. if by chance it won't let you login, as a failsafe you could still use either of the chroot methods i posted earlier to fix it.

---

### Post by philosophia on 2006-02-06
i am trying the chroot method.  i'm stuck here

```
sudo mount /dev/hdxx
```


i look in /etc/fstab and see that / is /dev/mapper/Ubuntu-root ext3

so i have tried

```
sudo mount -t ext3 /dev/mapper/Ubuntu-root /ubuntu
```


and many variations thereof.  i get error msgs that say 'wrong fs type'

what am i doing wrong?

---

### Post by philosophia on 2006-02-06
i've gotten past my last post


i only have the install cd, so i boot up to that

i'm booted to the install cd, then i try

sudo fdisk -l

-i get fdisk not found

then i mkdir /ubuntu, then
i do mount -t ext3 /dev/mapper/Ubuntu-root /ubuntu
if i chroot /ubuntu it seems to unmount everything and i have to reboot, so i skip chrooting /ubuntu

i try to visudo, but i get visudo not found, so instead i go into /ubuntu/etc and i nano sudoers, and remove the bad line

unfortunately, when i reboot to my desktop, i still cannot sudo su as a regular user.  i have confirmed that the bad line is gone from /etc/sudoers and that the file is owned by root.

i don't want to move on because i may screw something else up.

any advice?

---

### Post by Hallavej on 2006-02-06
I dont understand why you cant boot into rescue mode. Did try to hit Esc when you boot. That should give you the grup menu even if it is disabled as explained in ubuntuguide.org. So, hit Esc, boot in rescue mode and type visudo. That was all I had to do when I had the same problem.

---

### Post by philosophia on 2006-02-06
i *can* boot into rescue mode by holding esc down

however, when it boots to rescue mode, it asks for my root password

my root password was initially set to -1 so there was no *previous* root password.

i therefore cannot login as root in rescue mode, i have to try the chroot method he outlined in the second post

---

### Post by codejunkie on 2006-02-07
philosophia, 
since you mentioned /dev/mapper, im guessing your using drives were partitioned using lvm. i haven't used the chroot method on drives partitioned with lvm in ubuntu, i've only done it on standard partitions this might be the reason you were having trouble mounting yoor drive but there has to be a way, start a new thread about chrooting a drive partitioned with lvm would most likely provide a better answer than i could sorry i couldn't be more help.

---

