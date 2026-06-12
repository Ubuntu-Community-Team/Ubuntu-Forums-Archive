---
title: "sudo: 3 incorrect password attempts"
date: 2010-02-07
forum: Desktop Environments
---

### Post by JavaBeanHead on 2010-02-07
Hello gurus . . . 

My root filesystem recently filled up. I finally established why - that my /media directory had filled up due to the USB-attached device having been unmounted for whatever reason, and SimpleBackup tried backing up without the mount in place - thereby filling up the filesystem.

I discovered that the root directory was full when the machine tried to get updates, and couldn't.  So, I went into /media and tried to delete the backup directory and file(s) that were in that directory, but it tells me that permission is denied.  So I try to SUDO the same command, and it tells me 3 times in a row, "Sorry, try again", followed by "sudo: 3 incorrect password attempts".

So, how to I get root privileges back again?

```
name@machine:/media$ sudo rm -R FreeAgent
Sorry, try again.
Sorry, try again.
Sorry, try again.
sudo: 3 incorrect password attempts
name@machine:/media$ sudo -k
name@machine:/media$ sudo -i
Sorry, try again.
Sorry, try again.
Sorry, try again.
sudo: 3 incorrect password attempts
name@machine:/media$
```

Thanks in advance,
Bryan

---

### Post by mushwars on 2010-02-07
what does it say when you type 

```
groups <username>
```

if you did set a root password now would be the time to use it

```
su root
```
^ this time dont enter your user password unless its the same as root

---

### Post by JavaBeanHead on 2010-02-07
When I type groups <username> I get:

```
name@machine:/media$ groups username
name adm dialout cdrom plugdev lpadmin admin sambashare
```

I don't know if I explicity set a root password. I'd assume I didn't (as this is not within my immediate knowledgeset).

---

### Post by mushwars on 2010-02-07
:) there is the problem some how you are out of the group wheel.

you need to get root, you can boot the livecd and chroot into your system this will give you root then you need to 

```
gpasswd -a <username> wheel
passwd root
(this will be your new root password)
```

---

### Post by JavaBeanHead on 2010-02-07
Yikes, heavy duty, it sounds. Let me break out a manual on how to get to a root prompt with an install CD . . . I'm not even sure what the result I last gave you meant. How were you able to tell a 'problem' based on what I gave you?  What was the issue?  (Not even sure what the heck a wheel is!  

I'll run these commands and report back. Hopefully.

---

### Post by JavaBeanHead on 2010-02-07
Wait, I'm not sure what 'chroot' is.  Why can't I just do this from within another busybox (i.e. ALT+CTRL+F1)?

---

### Post by mushwars on 2010-02-07
no you must boot the live cd.

```
sudo mkdir /mnt/ubuntu
sudo mount /dev/sda1 /mnt/ubuntu
sudo chroot /mnt/ubuntu
```

now add your user to wheel and make a root password

---

### Post by amac777 on 2010-02-07
Your user appears to be a member of the "admin" group so you should be able to use sudo commands if you are using a default install of ubuntu. 

When you try to use a sudo command, sudo will ask you for a password. You should enter your user's password (the same one you use to login). Did you do that and it still says "Sorry, try again?" Are you sure you don't have Capslock on?

---

### Post by JavaBeanHead on 2010-02-08
> **amac777 said:**
> Your user appears to be a member of the "admin" group so you should be able to use sudo commands if you are using a default install of ubuntu. 

When you try to use a sudo command, sudo will ask you for a password. You should enter your user's password (the same one you use to login). Did you do that and it still says "Sorry, try again?" Are you sure you don't have Capslock on?

Nope - you've misunderstood - when I type "sudo" anything, I don't even get prompted for the password - it simply tells me three times that the incorrect password was supplied.

---

### Post by JavaBeanHead on 2010-02-08
> **mushwars said:**
> no you must boot the live cd.

```
sudo mkdir /mnt/ubuntu
sudo mount /dev/sda1 /mnt/ubuntu
sudo chroot /mnt/ubuntu
```now add your user to wheel and make a root password

Okay, the first 2 commands run fine, but when I attempt [FONT=Courier New][SIZE=1]sudo chroot /mnt/ubuntu[/SIZE][/FONT] I get a message stating '[FONT=Courier New][SIZE=1]chroot: cannot run command `/bin/bash': No such file or directory[/SIZE][/FONT]'.

I wonder . . . you're advising me to mount /dev/sda1 . . . could it be that /dev/sda1 is not what we're looking for?  I have 2 physical hard drives (internally) configured in a RAID array. Furthermore, when I installed the system, I manually configured my partitions, and used LVM.  Could that affect the 'sda1' part of this equation?

---

### Post by amac777 on 2010-02-08
> **JavaBeanHead said:**
> Nope - you've misunderstood - when I type "sudo" anything, I don't even get prompted for the password - it simply tells me three times that the incorrect password was supplied.

Hmmmm. That's strange. I did a google search and saw this [link]("http://forums.pcper.com/showthread.php?t=456953") that seems to indicate you can get locked out of sudo by trying to change your password but typing it incorrectly three times in a row? Did this all start happing after you changed your password? If not, did sudo used to work? Have you edited your sudoers file before?

---

### Post by JavaBeanHead on 2010-02-08
Nope - I haven't done anything with my password or otherwise with my profile since the install (~8 months ago).  Yes, sudo used to work.  Never edited the sudoers file before.

---

### Post by amac777 on 2010-02-08
sorry to double post, I just re-read your initial description of the problem. I forgot your hard drive was full. Maybe that is why you can't use sudo. (don't know this for sure but perhaps)

Do you have any large file in your home directory that you know you have backed up so can temporarily delete it and get some some space back? I'd recommend using the "rm" command from the command line so you really delete the file (don't put it in the trash). Make sure you have some space on / again after you delete the file and thn try using sudo again.

Edit: another way to get your space back would be to reboot and use the recovery mode and then delete the unwanted directory that way.

---

### Post by JavaBeanHead on 2010-02-08
I think that mushwars was onto something . . . I'd like to try to implement his solution, but running into problems.

However . . . to answer your questions, my /home directory is in a separate partition. Deleting files from /home (which is not full) will not help with space on the root partition.  Unfortunately, I'm not brainy enough to know what I can and cannot delete from /root to help clear up space.  A backup file filled the root partition, and I cannot cd to it (i.e. cd /media/FreeAgent Drive) because that requires elevated privileges, which I cannot get.  The problem is, I know what I need to delete, but cannot delete it.  Is it possible that the super user is hosed because root is full? Hmmmmm . . . I hope.

I think your idea of using the recovery mode from an install disc is an option. I will try that. (Though, I am inexperienced at using this, too - never tried it).

---

### Post by amac777 on 2010-02-08
I'm pretty sure that there is no wheel group in Ubuntu. My sudo works perfectly and I am not in any "wheel" group.

Using recovery mode should be pretty easy for you. Assuming you haven't set a root password, it should land you in a command prompt and you can cd to the directory you want to delete. You will have full privledges - No need to use sudo in recovery mode.

Edit: you don't need to use an install CD to get to recovery mode. Just select it from the grub menu (you may need to press ESC to make that menu visible on bootup).

---

### Post by JavaBeanHead on 2010-02-08
Okay . . . this got me somewhere; albeit, still not fixed.  I booted into recovery mode and removed the backup. Root is now 86% free. Trouble is, I still can't get any love for sudo. :\

Interesting - I never thought that the wheel group might not exist in Ubuntu.

---

### Post by amac777 on 2010-02-08
After you try to use sudo and get the "3 incorrect password attempts" error message, do you see any helpful error messages in /var/log/syslog? Try:
```

tail /var/log/syslog
```

---

### Post by mushwars on 2010-02-09
For the love of God, I told you the solution. I have done the same thing before.

```
sudo mkdir /mnt/ubuntu
sudo mount /dev/sda1 /mnt/ubuntu
sudo chroot /mnt/ubuntu
passwd <username here>
```

chrooting gives you root, you now are able to reset your password!

---

### Post by JavaBeanHead on 2010-02-09
Mushwars,
 
FOR THE LOVE OF GOD maybe you should read my reply to your brilliant idea. I tried it.
 
[http://ubuntuforums.org/showpost.php?p=8797019&postcount=10](http://ubuntuforums.org/showpost.php?p=8797019&postcount=10)
 
Thanks for leaving the attitude out of the forum.

---

### Post by amac777 on 2010-02-09
Mushwars: I'm pretty sure there is no wheel group on Ubuntu. Can you check your system by seeing what groups your user belongs to? Also, which version of Ubuntu are you using? In my understanding, users who belong to the "admin" group are by default given access to sudo commands. Also, the password should be your own user's password (not root's) and there is no reason to enable the root account. Also, I think this forum has a policy to not allow people to give advice to enable root's password.

JavabeanHead: Did you see any interesting error messages in the syslog? If not, perhaps just for fun you could change your user's password and see if that gives you sudo access back. At the command prompt type:

```
passwd
```

And then setup a new password. Once it's in, try sudo again. Feel free to change your password back to the original value after this test.

---

### Post by mushwars on 2010-02-09
Java, that is the only way to fix it, if its not working for you then you partitioned your hard drive differently than the installer automatically does, and therefor you would know what your / partition is, and would change /dev/sda1 to what its supposed to be.

---

### Post by dE_logics on 2010-02-09
I think now you need to rememerge aaaa....sorry reconfigure sudo.

> dpkg-configure sudo

If that does not help, try deleting /etc/sudoers (as root) after backing it up then dpkg-configure sudo

I'm not sure of the package name in ubuntu. Can someone confirm it?

---

### Post by JavaBeanHead on 2010-02-09
Sorry - you're missing one salient point to this whole thing - I cannot gain root access - no way, no how. Anytime I try to 'sudo' something, I get no opportunity to enter a password, it simply tells me (times 3) that an invalid password was supplied.
 
I'll have to attempt a few more of your (collective) suggestions when I get home from work in a few hours; I'll report back.

---

### Post by dE_logics on 2010-02-09
> **JavaBeanHead said:**
> Sorry - you're missing one salient point to this whole thing - I cannot gain root access - no way, no how. Anytime I try to 'sudo' something, I get no opportunity to enter a password, it simply tells me (times 3) that an invalid password was supplied.
 
I'll have to attempt a few more of your (collective) suggestions when I get home from work in a few hours; I'll report back.

Oh yes, sorry about that.


You need to chroot into your Ubuntu environment (as mushwars has been saying) thorough a live CD.

Boot a live CD.

Mount your root partition (where you have installed Ubuntu)...for e.g. in /media/disk.

Then open terminal - 

```
sudo chroot /media/disk
```

now ```
passwd
```

then ```
exit
```

And finally - 
```
sudo reboot
```

and reboot into your installed ubuntu.

Now if you ```
su
``` and type in the password that you previously set in the chrooted environment, you will have root access.

---

### Post by amac777 on 2010-02-09
> **dE_logics said:**
> 
Now if you ```
su
``` and type in the password that you previously set in the chrooted environment, you will have root access.

I still don't understand why you guys keep suggesting and explaining ways to enable the root account. Maybe it's me, but there is definitely some misunderstandings in this thread.

---

### Post by JavaBeanHead on 2010-02-09
dE_logics - thank you for your detailed explanation - I'm still fairly new to this. I did as you stated, and attempted this before:
 
**sudo chroot /mnt/ubuntu **and I get a message stating **'chroot: cannot run command `/bin/bash': No such file or directory'**.
 
I have a hunch that I'm doing something wrong when I'm mounting my root partition (where I have installed Ubuntu).
 
I don't know if it's /dev/sda1 or what -- or, as you said -- /media/disk. I did not let Ubuntu automatically partition my drives. I created manual partitions and used LVM. I created a volume group called 'mainvg'. I'm guessing that the partition 'root' is mounted on is /dev/mainvg/root or dev/mapper/mainvg-root . . . but I really don't know how to tell. I couldn't seem to find these when I was in the live mode cd. Are they encrypted in some way? Or could it be that because I'm running a RAID array that it is unable to find the RAID (instead maybe sees the drives individually, rather than as a whole?)??

---

### Post by JavaBeanHead on 2010-02-09
> **amac777 said:**
> JavabeanHead: Did you see any interesting error messages in the syslog? If not, perhaps just for fun you could change your user's password and see if that gives you sudo access back. At the command prompt type:

```
passwd
```And then setup a new password. Once it's in, try sudo again. Feel free to change your password back to the original value after this test.

/var/log/auth.log displays a message whenever I type 'sudo' anything: sudo: [FONT=Courier New][SIZE=2]PAM no modules loaded for `sudo' service

[/SIZE][/FONT]Changing my password did not help (I even rebooted).

---

### Post by amac777 on 2010-02-09
What is the output of these commands:

```
ls /etc/pam.d
cat /etc/pam.d/sudo
```

---

### Post by skai2701 on 2010-02-10
Hello, thanks for the solution, it works just as prescribed by You, ( I have followed your threads because I had the same problem)
But what I still do not understand why my sudo did not work any more - I have checked the md5sum and date of "sudoers", but it had not changed since installation, I am positive of that. sudo had worked over 2 month without problem and all of a sudden I am no sudoer any more.
Where can I look in my system for the answer?

Thanks in every case,

Siegfried




#

> **dE_logics said:**
> Oh yes, sorry about that.


You need to chroot into your Ubuntu environment (as mushwars has been saying) thorough a live CD.

Boot a live CD.

Mount your root partition (where you have installed Ubuntu)...for e.g. in /media/disk.

Then open terminal - 

```
sudo chroot /media/disk
```now ```
passwd
```then ```
exit
```And finally - 
```
sudo reboot
```and reboot into your installed ubuntu.

Now if you ```
su
``` and type in the password that you previously set in the chrooted environment, you will have root access.

---

### Post by dE_logics on 2010-02-10
> **JavaBeanHead said:**
> dE_logics - thank you for your detailed explanation - I'm still fairly new to this. I did as you stated, and attempted this before:
 
**sudo chroot /mnt/ubuntu **and I get a message stating **'chroot: cannot run command `/bin/bash': No such file or directory'**.
 
I have a hunch that I'm doing something wrong when I'm mounting my root partition (where I have installed Ubuntu).
 
I don't know if it's /dev/sda1 or what -- or, as you said -- /media/disk. I did not let Ubuntu automatically partition my drives. I created manual partitions and used LVM. I created a volume group called 'mainvg'. I'm guessing that the partition 'root' is mounted on is /dev/mainvg/root or dev/mapper/mainvg-root . . . but I really don't know how to tell. I couldn't seem to find these when I was in the live mode cd. Are they encrypted in some way? Or could it be that because I'm running a RAID array that it is unable to find the RAID (instead maybe sees the drives individually, rather than as a whole?)??

Oh no. Again sorry.

The chroot command was - 

```
sudo chroot /media/disk /bin/bash
```

Anyway, are you sure it's /dev/sda1?...if not check the output of ```
sudo fdisk -l
```...it should be marked as boot - 

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         293     2353491    7  HPFS/NTFS

Or in that case whichever partition is marked as boot is most probably your root partition (most probably cause you might have made a separate boot partition).

Another way is, to mount that device (which you think is root) and see it's contents...there should be the sbin and tmp folders there...

After you've confirmed that it's the root partion, chroot with (assuming you've mounted it in /media/disk) - 

```
sudo chroot /media/disk /bin/bash
```

and do the following (again posting) - 

> **dE_logics said:**
> now ```
passwd
``` then ```
exit
``` And finally - ```
sudo reboot
``` and reboot into your installed ubuntu. Now if you ```
su
``` and type in the password that you previously set in the chrooted environment, you will have root access.

---

### Post by dE_logics on 2010-02-10
> **amac777 said:**
> I still don't understand why you guys keep suggesting and explaining ways to enable the root account. Maybe it's me, but there is definitely some misunderstandings in this thread.

I know it's optional, but it's the easiest way out here...


The other option we have is chrooting into the installed Ubuntu and reconfiguring sudo after deleting (and taking backup) of /etc/sudoers.

---

### Post by JavaBeanHead on 2010-02-10
> **amac777 said:**
> What is the output of these commands:

```
ls /etc/pam.d
```

[FONT=Courier New][SIZE=2]name@machine:~$ **ls /etc/pam.d**
atd  chfn  chsh  common-account  common-auth  common-password  common-session  cron  cups  gdm  gdm-autologin  gnome-screensaver  login  other  passwd  polkit  ppp  samba  su  sudo[/SIZE][/FONT]

> **amac777 said:**
> What is the output of these commands:
```
cat /etc/pam.d/sudo
```

[FONT=Courier New][SIZE=2]name@machine:~$ **cat /etc/pam.d/sudo**
#%PAM-1.0

@include common-auth
@include common-account

session required pam_permit.so
session required pam_limits.so[/SIZE][/FONT]

---

### Post by JavaBeanHead on 2010-02-10
> **dE_logics said:**
> Oh no. Again sorry.

The chroot command was - 

```
sudo chroot /media/disk /bin/bash
```Anyway, are you sure it's /dev/sda1?...if not check the output of ```
**sudo** fdisk -l
```...it should be marked as boot - 

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         293     2353491    7  HPFS/NTFS


I hate to say it again - it's the perverbial chicken and the egg - you asked me to run a **sudo** command. You know I can't do this :lolflag:

```
name@machine:~$ sudo fdisk -l
Sorry, try again.
Sorry, try again.
Sorry, try again.
sudo: 3 incorrect password attempts
name@machine:~$ fdisk -l
Cannot open /dev/sda
Cannot open /dev/sdb
Cannot open /dev/sdc
```

Gentlemen . . . I gotta tell ya - all this mounting is making me crazy.  I think the reason I can't mount the proper device is because a LIVECD will not detect the idea that my 2 hard disk drives are configured in a RAID 0.  Agree? I'm thinking that it will only see each disk individually, and hence may not be seeing my LVM Partitions correctly.  Can anyone refute this?

All things aside - while I appreciate your help, I will continue to try each and every one of your solutions until this weekend, at which point I throw in the towel, and reinstall Linux from scratch, and restore my backed up files to where they were.

Warmly,
Bryan

---

### Post by amac777 on 2010-02-10
It seems like your PAM modules for sudo are OK.... I'm wondering if perhaps when you tried to update with the full hard drive if something got half updated and left you with a messed up sudo or PAM configuration. If you still have time to try things, perhaps reboot and select the "recovery mode" in grub again, and get yourself to the command prompt to attempt to finish the update process manually:

```
apt-get update
apt-get upgrade

```

And in the event that apt-get reports some broken packages, try to fix it by removing the broken package and then running the above commands to update and upgrade again.

```
apt-get remove broken-package-name
```

Edit: Assuming it works, you can reinstall the broken package again:

```
apt-get install broken-package-name
```

---

### Post by JavaBeanHead on 2010-02-10
Wow! Such an easy fix to a very complex problem.  Sir, you're quite amazing and I commend you.  It is fixed, and what you told me to do, fixed it.  Well, it wasn't 'exactly that', but it lead me to the place where I found my solution.

In fact, there was an option in the recovery mode menu to fix or repair broken packages (I think something to that effect - which I never even noticed before).  It ran for a little bit, and said the following:

*One or more of the files /etc/pam.d/common{auth, account, password, session} have been locally modified. Please indicate whether these local changes should be overridden using system-provided configuration. If yhou decline this option you will need to manage your system's authentication configuration by hand.*  (Naturally, I accepted)

Indeed the disk (root) had been full (as described earlier in this thread) due to a backup gone awry . . . and an update was attempted and I kept receiving messages about broken packages and 'crash reports' in my upper right-hand side of the screen.  I simply dismissed these as side effects of the 'sudo' issue.  

I am so pleased that you stuck with me to help me out amac777 (and the rest of you, too)!  I hope to find you around the forums again.

---

### Post by Satoru-san on 2010-02-10
> **JavaBeanHead said:**
> reinstall Linux from scratch
You are lucky you didn't have to do that :)

If you could mark this post as [COLOR=Red]*[SIZE=5]solved.[/SIZE]*[/COLOR]

By the way: this is the reason why that quote is funny:
[[IMG]http://www.linuxfromscratch.org/images/lfs-logo.png[/IMG]<--link]("http://www.linuxfromscratch.org/")

---

### Post by amac777 on 2010-02-10
Glad it's fixed, and good to learn there is a "repair broken packages" option in the recovery mode too. I didn't know that.

---

### Post by LSB-LastBoyScout on 2010-07-10
I had the same problem and it started after setting up Active Directory authentication in PAM.  The idea was to allow domain users to SSH into the machine and have their own seperate accounts created (mapped actually) automatically.

Anyway, the long and short of it, my [FONT="Courier New"]/etc/pam.d/system-auth[/FONT] file was missing the following entry:

```
auth        sufficient    pam_unix.so nullok try_first_pass
```

This caused attempts to [FONT="Courier New"]su[/FONT] to fail with 3 consecutive password failures, even though I was never given chance to enter a password!

Hope this helps someone else out in the future :)

---

