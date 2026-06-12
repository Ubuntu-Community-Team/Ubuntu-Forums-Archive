---
title: "Screwed up Root permissions, cannot log-in"
date: 2009-04-11
forum: General Help
---

### Post by sarthorks on 2009-04-11
Help!

I ran 
```

sudo chmod o+u /

```
 by a BIG mistake, and then, by a BIGGER one, ran
```

sudo chmod o-u /

```

SO i ended up not being able to access anything or any command.

Then i went to recovery mode, and ran something from this forum which i dont remember, but after that i could run SUDO command.

BUt i still cudnt do anything else.

So i decided to re-installed.
I had separate /root and /home partitions.
So i deleted /root partition and made a newer one where i installed a (32bit this time) hardy heron.
But, this new install had its own /home.
my /home directry (which had two users) was coming as a mount device in /media.

So i followed this and got my old home to be the new home.

```
sudo mkdir /mnt/newhome 
sudo mount -t ext3 /dev/sda3 /mnt/newhome 
find . -depth -print0 | cpio --null --sparse -pvd
sudo mv /home /old_home 
sudo mkdir /home 
sudo umount /mnt/newhome 
sudo mount /dev/sda4 /home 

```
Then i edited my fstab file, by adding this line at the end
```

/dev/sda3 /home ext3 nodev,nosuid,relatime 0 2 

```
(i tried without relatime and with relatime, and i tried by writing the UUID instead of sda3, but nothing worked).

When i rebooted,
and tried logging in, i got these error messages:
"Your home directory is listed as: '/media/disk' but it does not appear to exist. Do you want to log in with the /(root) directory as your home directory?
It is unlikely anything will work unless you use a failsafe session"
after pushing yes i was prompted with this error
" User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. Users $HOME directory must be owned by user and not writable by other users."
And the next one is about something i cant remember, but they say that "anyway, you can't log in."
and i am taken back to the login screen.

PLEASE HELP!

my 11GB /root folder appears as /media/disk and 140GB /home folder (which contains two users - one of them being sarthak which i am trying to activate again) - as /media/disk-1 when i use the LiveCD, which i am doin right now.

---

### Post by sarthorks on 2009-04-11
Yes, the last message i get (after the message "Your home directory is list..." & "User's $HOME/.dmrc file is bein...") is :

"GDM could not write to your authorisation file. This could mean that you are out of disk space or that your home directory could not be opened for writing. In any case, it is not possible to log in. Please contact your system administrator."

Please, somebody, please help! I am at my wits end! :mad:

---

### Post by Diabolis on 2009-04-11
You could try to fix it and just make it mount your second partition to /home, but as shown the risk of messing it up more is high. *Your fstab file might be incorrect, depending on the numbering of your partitions, using UUID numbers would avoid this.*

So for a straight forward solution, just reinstall Ubuntu in your 11GB partition and DURING installation tell it to use the 140GB partition as /home. It will take care of everything.

---

### Post by sarthorks on 2009-04-11
oh i see...when i installed ubuntu again, i did not specify the 140GB partition as /home, fearing editing it might format it.

Which is apparently not the case. So i will re-install ubuntu and this time specify the 140GB partition as /home.

Pheww, life can be easier after all!

Thanks!

---

### Post by sarthorks on 2009-04-12
yess! it worked! :guitar:

---

