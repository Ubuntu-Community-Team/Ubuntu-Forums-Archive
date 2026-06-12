---
title: "Best automatic nightly Backup software from laptop to external HD (like EZBackitup)"
date: 2006-07-14
forum: Desktop Environments
---

### Post by engineering.concepts on 2006-07-14
Any help would be greatly appreciated, I am getting confused with all of the different backup options avaiable for Ubunutu. I would like a simple GUI that would perform automatic nightly backups without compression, so if something gets screwed up (like a word doc ) I can just get it off of the back up drive.

On WinXP I used Cobian or EZBackitup, and suggestions?

Thanks in advance:)

---

### Post by llamakc on 2006-07-14
I use backup-manager:

```

ken@dothan:~$ apt-cache show backup-manager
Package: backup-manager
Priority: optional
Section: universe/admin
Installed-Size: 428
Maintainer: Alexis Sukrieh <sukria@sukria.net>
Architecture: all
Version: 0.6-1
Depends: debconf | debconf-2.0, gzip (>= 1.3), ucf (>= 0.08)
Suggests: zip, libnet-perl, perl, perl-modules, ssh, cdrecord, mkisofs, gettext-base, anacron, dvd+rw-tools
Filename: pool/universe/b/backup-manager/backup-manager_0.6-1_all.deb
Size: 73878
MD5sum: 333b0552ecb78ebb7eefc2db5d80f0aa
Description: command-line backup tool
 This is a backup program, designed to help you make daily archives of
 your file system.
 .
 Written in bash and perl, it can make tar, tar.gz, tar.bz2, and zip
 archives and can be run in a parallel mode with different
 configuration files. Other archives are possible: MySQL or SVN dumps,
 incremental backups...
 .
 Archives are kept for a given number of days and the upload system
 can use FTP, SSH or RSYNC to transfer the generated archives to a list of
 remote hosts.
 .
 Automatically burning archives to removable medai such as CD or DVD is also
 possible.
 .
 The configuration file is very simple and basic and gettext is used for
 internationalization.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu


```

I'm using the ssh (scp|sftp?) method with ssh-keys to move stuff over from a Debian server to an extra Ubuntu box in the house. 

If you just want to backup to a local hd I'd just use tar and cron.

---

### Post by Lunar_Lamp on 2006-07-14
If you're not too bothered about a GUI you could very simply write a very basic script to do it for you. 

For example, an overly-basic script would be this:

```
#!/bin/sh

mv /media/usb-backup-drive/Today /media/usb-backup-drive/Yesterday
mkdir /media/usb-backup-drive/Today
cp -a /home/me* /media/usb-backup-drive/Today
rm -rf /media/usb-backup-drive/Yesterday
```

This would backup your home folder to a folder called "today", and then delete the previous backup.  Obviously you would probably want something a little more complex though.  Then you just need to setup the script to be run as a cron-job every night.

I'm just suggesting this as you may not have realised quite how simply it could be achieved.

Edit - I suddenly realised that someone may get the silly idea to use the script that I wrote.  There are probably hundreds of example bash scripts out there on the net that are far better than the one I quickly jotted down - this is the kind of thing that is often used as an example when learning to script in bash.

---

### Post by engineering.concepts on 2006-07-15
Thanks for your help everyone. I was did not realize how easy is actually was to make a backup ..... I just assumed that it would be much more difficult like on WinXP :D 

I found a cool bash file that was easy to customize for my purposes.... simplebashbu.tar.gz
[http://sourceforge.net/projects/simplebashbu/](http://sourceforge.net/projects/simplebashbu/)

I modified the file and got everything working great!:-D 

Just one more quick question - how do I make this reoccur every night? Is there a gui for this in Ubuntu? I thought I might have to modifiy the crontab with crontab -e...... but this does not seem to work, (or I am doing it wrong)

1 5 * * * /root/scripts/simplebashbu/simplebashbu.sh

This tells cron to run the script at 5:01 am everyday.

---

### Post by Spie on 2006-07-16
You might want to take a look at [this thread]("http://www.ubuntuforums.org/showthread.php?t=15082")

---

### Post by engineering.concepts on 2006-07-16
> **Spie said:**
> You might want to take a look at [this thread]("http://www.ubuntuforums.org/showthread.php?t=15082")

Thanks for the like Spie! That's what I needed:D

---

