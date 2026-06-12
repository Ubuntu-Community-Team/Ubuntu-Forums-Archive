---
title: "Backing Up To Network Computer"
date: 2009-05-13
forum: General Help
---

### Post by snorbens on 2009-05-13
Hi,
I have created a folder on my Desktop Computer (vista) in another room in the house, to enable me to backup this one.

I can see the folder ok. It does not seem that sbackup can backup to that computer. Is there an easy program that a newbie like me can use to easily backup?

Although I have enabled the C: drive share option, I get the unable to mount message, but was able to create the folder and then enable share so that I can now access and read/write to it,although everyone on my network can access it, as I was unable to work out how to restrict access to just my computer.

Any help would be appreciated to enable me to backup to that folder.

Thanks

---

### Post by exutable on 2009-05-13
There is a really good app called rsync that will basically back everything you have up through a command line.  It's tough for a beginner but here is a really good guide:

[http://lifehacker.com/246324/how-to-automatically-back-up-your-computers-with-rsync]("http://lifehacker.com/246324/how-to-automatically-back-up-your-computers-with-rsync")

If this is too hard for you try grsync, which is a graphical interface to help you and can be found through synaptic.

---

### Post by snorbens on 2009-05-13
> **exutable said:**
> There is a really good app called rsync that will basically back everything you have up through a command line.  It's tough for a beginner but here is a really good guide:

[http://lifehacker.com/246324/how-to-automatically-back-up-your-computers-with-rsync]("http://lifehacker.com/246324/how-to-automatically-back-up-your-computers-with-rsync")

If this is too hard for you try grsync, which is a graphical interface to help you and can be found through synaptic.

Hi,
Thanks for the info will give both of them a go.

---

### Post by kaptengu on 2009-05-13
I'm sorry to say, there are no good ways to do remote backups under Windows. Rsync is by far the best solution for this but for Windows you need to run it under cygwin. If this sounds too much for you, maybe have a look at robocopy or Microsoft SyncToy instead.

---

### Post by snorbens on 2009-05-13
> **kaptengu said:**
> I'm sorry to say, there are no good ways to do remote backups under Windows. Rsync is by far the best solution for this but for Windows you need to run it under cygwin. If this sounds too much for you, maybe have a look at robocopy or Microsoft SyncToy instead.

So I cannot backup my Ubuntu Laptop System to a Folder on my Windows Vista Desktop in one of my other rooms using Grsync or something similar??

It would not surprise me knowing Windows but I did create a folder on my Windows system and using either sbackup or grsync I can see every other folder apart from my Laptop Backup folder...strange and confusing to me.

Thanks for the input

---

### Post by gamblor01 on 2009-05-13
If you have mounted the directory and you can write to do then a simple cp command should do the trick.  Let's say you want to copy over the contents of your home directory every night.  You can just write a script that does this:

```

#!/bin/bash

cp -R ~ /your/path/to/windows/mount

```

Then you can schedule it to run at 12:05am for example by editing your crontab and putting in an entry like:

5 * * * * ~/scripts/backupToWindows.sh

---

### Post by snorbens on 2009-05-13
> **gamblor01 said:**
> If you have mounted the directory and you can write to do then a simple cp command should do the trick.  Let's say you want to copy over the contents of your home directory every night.  You can just write a script that does this:

```

#!/bin/bash

cp -R ~ /your/path/to/windows/mount

```

Then you can schedule it to run at 12:05am for example by editing your crontab and putting in an entry like:

5 * * * * ~/scripts/backupToWindows.sh

Hi, Thanks for your reply..Now you will realize how much of a newbie I am.

I do not know what crontab is. I know that I probably should but have only been using Ubuntu for a very short time, sorry.

Thanks

---

### Post by kanikilu on 2009-05-13
Instead of using "cp -R", why not mount the smb share from vista, and then point rsync (or grsync) to that local mountpoint?

That way you can backup only what has been changed since the last backup, rather than doing a full backup each time.

Check out this page for information to mount the share permanently:

[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

---

### Post by snorbens on 2009-05-13
Hi,
Thanks to all for your help.

I will try all proposals but I seem to be getting confused with it all so will take a little time to look at it all. I am getting the feeling that I may be too old for all of this:confused:

I am trying very hard to understand all of this and I will get there but I fear that it is going to take me some time. I just hope that you all do not get annoyed with me for appearing a little stupid.(or very stupid for that matter)

Thanks

---

### Post by snorbens on 2009-05-13
Hi,
I think I am confusing myself and everyone else here,let me try and explain what I have done and what is happening.

I have created a folder within Vista on my Desktop PC,which is in another room, and wish to backup my Ubuntu system on my laptop computer to that folder.

I can open the said folder from my Ubuntu system via Network, and can copy paste etc from within my Ubuntu system to the folder on my other computer.

I can even see the mounted folders in the Ubuntu Places/Computer.
But I cannot seem to be able to find the path to the shared folder,if that is indeed possible. I have tried both grsync and sbackup but cannot seem to be able to "point" to the networked folder.

Hope I have not confused people any more. But I hope that I am being a complete dummy about this and someone can put me right.

Thanks for your indulgence.

Snorbens

---

### Post by gamblor01 on 2009-05-13
> 
Hi, Thanks for your reply..Now you will realize how much of a newbie I am.

I do not know what crontab is. I know that I probably should but have only been using Ubuntu for a very short time, sorry.

Your crontab is basically the configuration file that cron uses.  Cron is a program that runs as a daemon process and will execute the commands that you tell it to on whatever schedule you specify.  In my example I specified the script "backupToWindows.sh" to run at 12:05 every morning.  Google for examples of cron entries and you will see what all of the 5 fields mean.

You're not usually supposed to edit the cron file manually, instead you should use the command "crontab -e" to edit it.

> 
I can even see the mounted folders in the Ubuntu Places/Computer.
But I cannot seem to be able to find the path to the shared folder,if that is indeed possible. I have tried both grsync and sbackup but cannot seem to be able to "point" to the networked folder.

If you run the command:

```

sudo mount

```

It should show you all of the currently mounted devices, so you should be able to pull the name of the "folder" out of the output of that command.

---

### Post by snorbens on 2009-05-14
> **gamblor01 said:**
> Your crontab is basically the configuration file that cron uses.  Cron is a program that runs as a daemon process and will execute the commands that you tell it to on whatever schedule you specify.  In my example I specified the script "backupToWindows.sh" to run at 12:05 every morning.  Google for examples of cron entries and you will see what all of the 5 fields mean.

You're not usually supposed to edit the cron file manually, instead you should use the command "crontab -e" to edit it.


If you run the command:

```

sudo mount

```

It should show you all of the currently mounted devices, so you should be able to pull the name of the "folder" out of the output of that command.

Hi,
It does not appear to show anything mounted on my other computer...not that I understand the output anyway:confused:
This is the output of sudo mount
```

mervyn@mervyn-laptop:~$ sudo mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mervyn/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mervyn)
mervyn@mervyn-laptop:~$  
```

This networking is really getting to me and I really think that it may be too much for my addled/aged brain.

As I can copy and paste into the folder on my other computer, it may be easier for me to just make a backup file on this computer, and then copy and paste into the folder on the other computer.

If the wife would let me install Ubuntu on the other computer it may make it easier for me.

I do like Ubuntu, but as I am finding it difficult to grasp the ins and outs of this system, not just backing up, I feel alas, that it may be time to swallow my pride and go back to that other OS,as I just feel I may never understand it.

Thanks for all your help

Snorbens

---

### Post by gamblor01 on 2009-05-15
> 
I do like Ubuntu, but as I am finding it difficult to grasp the ins and outs of this system, not just backing up, I feel alas, that it may be time to swallow my pride and go back to that other OS,as I just feel I may never understand it.

Having the ability to go back to a "trusty" OS must be a luxury!  :p

Keep in mind that when you first started out with Windows you were no expert either.  It takes time to learn these things and while you may never know all of the ins and outs (I seriously doubt anyone does), you will eventually get to the point where you know enough -- if you stick with it.

I looked at your mount output however and it doesn't look like you have a drive mounted on your Windows system.  Gnome must be doing something sneaky in the background when you to go Places -> Network and I'm not quite sure what that is.  What you could try to do is manually mount the folder as an SMB filesystem.  For example, let's suppose you are sharing the folder "MyFiles" on your Windows box (for this example I'll just suppose that it's on IP address 192.168.0.2 with a hostname of "windozebox").  You could try this:

```

sudo mkdir /media/myfiles

```
Or whatever path you want to use (I'll stick with /media/myfiles for this example).  Then whenever you want to "mount" this remote directory to copy files into it you can use this command:

```

mount -t smbfs -o username=Administrator,password=yourWindowsPassword //192.168.0.2/MyFiles /media/myfiles

```

Alternatively if you want to use the hostname instead of IP you could do this:

```

mount -t smbfs -o username=Administrator,password=yourWindowsPassword //windozebox/MyFiles /media/myfiles

```


Obviously you need to substitute your Windows user ID and password into the command.  Also make sure there are NO SPACES anywhere in that -o option though; if you try to put a space after the comma and then password= it will complain about incorrect syntax.

See if that works and if so, then you can just cd into /media/myfiles and copy files into/out of this directory.

If you get it to work manually then we can look at adding an entry into the /etc/fstab file.  A syntactically correct entry in /etc/fstab will cause the system to mount the directory during startup, so you never have to manually run the above commands anymore.

---

### Post by snorbens on 2009-05-15
Hi Gamblor,

Thank you for your help.

I will try that later as I have re-installed Vista:oops:

I am also going to re-install Ubuntu later today and go back to dual booting for a while or at least until I feel more confident with Ubuntu.

I am determined though to eventually revert to just having Ubuntu as my main OS. It was probably too early to switch to Ubuntu as my only OS until I learned sufficiently about Ubuntu.

I will be adding Ubuntu as my dual boot later on today so will give your suggestions a go.

Thanks very much

Snorbens

---

### Post by dcstar on 2009-05-15
> **snorbens said:**
> So I cannot backup my Ubuntu Laptop System to a Folder on my Windows Vista Desktop in one of my other rooms using Grsync or something similar??
.......

You **cannot** "backup" individual Linux files/folder to any Windows filesystem because the full set of permissions are not supported and the legal filenames are different.

You can package Linux files (into a tarball or some other format that preserves things) and put that onto a Windows filesystem.

---

