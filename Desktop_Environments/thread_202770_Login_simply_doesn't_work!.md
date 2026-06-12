---
title: "Login simply doesn't work!"
date: 2006-06-24
forum: Desktop Environments
---

### Post by Gorbachev on 2006-06-24
Alright, so I installed Ubuntu tonight and love it :o but there are a few problems getting in my way.

First of all, after deciding to settle in and change my username and all that, I ran this:

sudo oem-config-prepare

rebooted and set a few options as it asked me to.

Get to the login screen.. bam! It wouldn't let me use the username i had specified during the setup. Upon boot, I had chosen Gorbachev to be my new username, with an all lowercase text only password. I entered Gorbachev (cap G) and an all lowercase password at *least* 20 times.

I eventually tried my full name, since i had entered that also during the setup.
then I tried oem and the password i had used originally, which used to work, but not now.


Seriously, I can't get into Ubuntu **at all**. It's killing me.

I'm sensing some anti-communist feelings from Ubuntu. :p :( 

Any help is great.


***edit**: I was also hoping someone could send me in the right direction to have full read/write access to my NTFS harddrive, as I have Ubuntu installed to a different drive than Windows on a trial basis.

Another "problem" I have is, that in GRUB boot loader, I have two entries of Ubuntu, and two entries of Ubuntu (recovery). Where can the loader list be found to be edited from within linux to correct this?

---

### Post by Gorbachev on 2006-06-24
Sorry to post again, here is the name of the ISO I downloaded: ubuntu-6.06-alternate-i386.iso

Hope that helps.

---

### Post by halfvolle melk on 2006-06-24
You could try to boot into recovery mode and run 'sudo adduser <name>'. This new user won't have sudo rights, for that it needs to be added to /etc/sudoers (not exactly sure how to properly do that). You may want to set up root with 'sudo passwd su' to be able to do admin stuff in regular log-in until you fixed sudoers.

> ***edit**: I was also hoping someone could send me in the right direction to have full read/write access to my NTFS harddrive, as I have Ubuntu installed to a different drive than Windows on a trial basis.
[https://help.ubuntu.com/community/NTFSReadWrite](https://help.ubuntu.com/community/NTFSReadWrite)
> Note: writing to NTFS partitions is considered experimental and at least some people think it very risky (see for example [WWW] thread and [WWW] thread). Once again, if you are going to use the software below to write to an NTFS partition, make sure you have backups first. 

> Another "problem" I have is, that in GRUB boot loader, I have two entries of Ubuntu, and two entries of Ubuntu (recovery). Where can the loader list be found to be edited from within linux to correct this?
You can find it in /boot/grub/menu.lst but there's no need to remove them. If your kernel ever gets messed up for any reason, you'll have your old kernel to fall back to.

Hope this helps.

---

### Post by Gorbachev on 2006-06-24
Hey thanks.

Having used linx for a day, I was kind of frustrated with not being able to login at all.

Also, the second entries appear to be the same version?

---

### Post by Gorbachev on 2006-06-24
> You could try to boot into recovery mode and run 'sudo adduser <name>'. This new user won't have sudo rights, for that it needs to be added to /etc/sudoers (not exactly sure how to properly do that). You may want to set up root with 'sudo passwd su' to be able to do admin stuff in regular log-in until you fixed sudoers.

Sorry to post again, what I really need now is to fix the problem (er.. sudoers). I simply don't know how. :(

---

### Post by bulldog on 2006-06-24
[QUOTE=Gorbachev]Alright, so I installed Ubuntu tonight and love it :o but there are a few problems getting in my way.

First of all, after deciding to settle in and change my username and all that, I ran this:

sudo oem-config-prepare

rebooted and set a few options as it asked me to.

Get to the login screen.. bam! It wouldn't let me use the username i had specified during the setup. Upon boot, I had chosen Gorbachev to be my new username, with an all lowercase text only password. I entered Gorbachev (cap G) and an all lowercase password at *least* 20 times.

I eventually tried my full name, since i had entered that also during the setup.
then I tried oem and the password i had used originally, which used to work, but not now.


Seriously, I can't get into Ubuntu **at all**. It's killing me.

I'm sensing some anti-communist feelings from Ubuntu. :p :( 

Any help is great.


***edit**: I was also hoping someone could send me in the right direction to have full read/write access to my NTFS harddrive, as I have Ubuntu installed to a different drive than Windows on a trial basis.

Another "problem" I have is, that in GRUB boot loader, I have two entries of Ubuntu, and two entries of Ubuntu (recovery). Where can the loader list be found to be edited from within linux to correct this?[/QUOTE]

Try gorbachev instead of Gorbachev.
By my knowing you can't use the Cap in your name.

NTFS writing is not something I would recommend to do.
Leave GRUB as it is,till you know what you're doing,messing it up is not hard to do.

---

### Post by Gorbachev on 2006-06-24
Ah, so the problem was simply that I cannot create a username with a capital G? 

I'll try it :o thanks.


It works!

---

### Post by bulldog on 2006-06-24
You should have seen a warning when you choosed a capital G in your username.
How you managed to get it trough I don't know however.
Hope that it resolved your problem, otherwise try a fresh install.

---

### Post by Gorbachev on 2006-06-27
It fixed it right up, thanks.

---

