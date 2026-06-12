---
title: "Ubuntu or not Ubuntu"
date: 2006-07-24
forum: Desktop Environments
---

### Post by Mr_ on 2006-07-24
Hey there. Over the past week I've tried valiantly to install Ubuntu. I must have downloaded all of the different versions; 

Ubuntu-6.06-alternate-amd64.iso
Ubuntu-6.06-desktop-amd64.iso
Ubuntu-6.06-alternate-i386.iso
Ubuntu-6.06-desktop-i386.iso
Ubuntu-6.06-dvd-amd64.iso
Kubuntu-6.06-alternate-amd64.iso
Kubuntu-6.06-desktop-amd64.iso
Kubuntu-6.06-alternate-i386.iso
Kubuntu-6.06-desktop-i386.iso
also in desperation edgy-alternate-amd64.iso for both Ubunto and Kubuntu

thank the geniuses who invented rewritable media!

Each install has failed at some point firstly [it was this bug]("https://launchpad.net/distros/ubuntu/+source/ubiquity/+bug/48017"), I didn't log that bug, I didn't see the point as it was exactly the same, down to the logs. Then after about 3 nights of trying to install any of the various installations and reading on this very forum that there seemed to be a problem with the gparted in the installer. After realising this I started to install using the oem or text based installers. The installation was successful on all occasions only when I came to boot up for the first time there were problems with various programs loading. Unfortunatly, being tired, grumpy and fed up of installing time and time again I lost my patients and failed to save any bug or system logs, please forgive me Ubuntu peeps. 

In final leap of faith I'm currently as I type this downloading Ubuntu 5.10 and I'm hoping it installs and then I'll update once I'm in. 

I'm quite determined to install Ubuntu, I've spent a lot of time and effort trying to get the damn thing to work and I don't want to be beaten.

I guess the problems are hardware related as none of the installs seem to work. Here's a list of my hardware:

Abit av8 Motherboard
Nvidia 6800 Geforce gfx card
NEC DVD-RW ND 3520A
1 GB RAM
160 gb SATA HDD
10 gb IDE HD

I use all of the onboard stuff sound, ethernet, usb etc etc. I'm installing onto the 10 gb drive and letting the installer be it oem or live erase the whole disk and install as it chooses best. I have tried to install on the 160 gb drive but I get the same results.

I hope maybe someone can help me out, I'm tired of and I bet my ISP is of me downloading .iso's.

Failing any help could anybody suggest a good Linux distribution with good support and regular updates that may work on this godforsaken PC of mine?

tia

PS: great community you have here, one of the reasons I'm so determined to install Ubuntu, that and it looks like a great package.

---

### Post by Ziox on 2006-07-24
i suggest that you do not use rewritable media. From my experience, Rewritable media is much less reliable than CD-Rs.  Burn a CD-R at a slow speed, and usually that would work out for you.  And what sort of problem are you encountering when you install? Can the CD boot?

---

### Post by Johnsie on 2006-07-24
I agree it what the guy above me said. When burning Operating Systems you should use high quality cdr disks. CD-RW probably isn't the best option. Make sure you burn them at a slow speed.

I've had the same problem and it turned out that either the cd's were crap or the cd drive was no good.

---

### Post by Mr_ on 2006-07-24
> **Ziox said:**
> i suggest that you do not use rewritable media. From my experience, Rewritable media is much less reliable than CD-Rs.  Burn a CD-R at a slow speed, and usually that would work out for you.  And what sort of problem are you encountering when you install? Can the CD boot?

The cd's have been booting fine, and I've also gotten into the habit of checking cd's integrity using the Check CD for defects option on the cd boot menu. Only twice has the cd failed in which case I've rebooted windows and re burnt the iso. When I burnt the DVD image I didn't use rewritable media, I checked the dvd's integrity and it seemed ok according to the checker.

---

### Post by Mr_ on 2006-07-24
Just to add. I have just tried installing ubuntu 5.10 and 6.06 on non rewritable media and failed. I managed to get a little bit further into the initial startup of ubuntu adter install but it crashed with errors from a gnome program and nautilus. I managed to save a bug report but i wasn't sure what log file I needed to save. 

var/log ?? not sure after that any help would be appreciated so I can get this bug looked at. In the meantime I'll submit what I have already(see attached) and I'll submit it to launchpad when I get chance though there isn't much info there so I could really do with finding out which log will be benificial to the dubugging people :)

---

### Post by jISh on 2006-07-24
Okay, the  FIRST bug you are getting there is from the Ubquity partitioner. The best way around this is simply to use the alternate install (text based), which I'm assuming you tried at one point and got installed.

So get yourself to that point again, then tell us what problems you have with programs loading.

EDIT: Do burn yourself a copy of it on a non-RW media.

---

### Post by Mr_ on 2006-07-25
Right after reading through the install and upgrade threads I've found our what files I need to post

> /var/log/Xorg.0.log and ~/xsession-errors log files. Post the result of $lspci and post your /etc/apt/sources.list.

When I get home from work I'll see if I can get far enough into the boot to retrieve those files.

---

### Post by wpshooter on 2006-07-25
Dear Mr_

I notice in your hardware listing that you have both a SATA and a very small (apparently, relatively old) 10gb IDE drive.

It seems to me that I have ran across posts on here that have mentioned that there may be problems with installing on systems that had a mixture of SATA and IDE drives.  Why don't you try unhooking that small 10gb drive and see if that cures your install problems.

Also, are you trying to install Ubuntu along with (dual boot) another O/S or is this going to be strictly a Ubuntu machine ?

If the above suggestion regarding unhooking the 10gb drive does not work, I would consider getting a good hard drive WIPING utility and blank (this is assuming that you do NOT have anything on the drive you do not want to loose) your 160gb drive and then retry installing from the Ubuntu DESKTOP 6.06 CD.

P.S. Also, I don't think there is any major problem with using CD-RW media as long as you use a relatively low burning speed.  I have done all of my burns on HIGH QUALITY CD-RW media and I have had zero problems.  But still make sure you run the sum check utility on the CD at the Ubuntu bootup menu.

Good luck.

---

### Post by Mr_ on 2006-07-25
wpshooter, thanks. I plan on having this as a dual boot os for a while then when I'm happy with the way ubuntu runs I'll move on to just ubuntu. If I install onto the 10 gb drive alone I'll have to amend to MBR and I can't for the life of me remember how to do when both drives are hooked up.

Secondly I have a quite alot of stuff on the 160gb sata I need to keep, at least for another week until i get my [new NAS device]("http://www.freecom.com/ecproduct_detail.asp?ID=2348&CatID=8070&sCatID=80703&ssCatID=80703") woohoo! but once I've got that I may just dump the 10gb drive and reinstall everything onto my 160gb sata drive. 

I must admit while I was installing ubuntu I did find the manually edit partitions section rather confusing, I'm going to look in the wiki for help and advice on that.

---

### Post by wpshooter on 2006-07-25
Well I am sort of glad to see that I am not the only one that found it confusing.  As a matter of fact I finally just gave up on trying to manually edit anything, got rid of M/S altogether (basically the only things I do with my systems is internet, e-mail and distributed computing) and then used the gparted section of the desktop install CD version to partition/format my hard drives.

Good luck.

---

### Post by yustabeme on 2006-07-25
have you tried booting the dvd "live"? You might also consider other live distros such as Knoppix, DSL, Mandriva, et al, to narrow down to Ubuntu/hardware specific probs. In the past when I've had problems with an installer's partitioning phase I've even resorted to booting another live distro, partitioning, then installing the problem distro, accepting my by now existing partition scheme. Trinity is a good, small forensics/rescue cd w/ qtparted:

[http://trinityhome.org/Home/index.php?wpid=1&front_id=12](http://trinityhome.org/Home/index.php?wpid=1&front_id=12)

or take your pick

[http://www.frozentech.com/content/livecd.php](http://www.frozentech.com/content/livecd.php)

since you're installing to the IDE, why not unplug the SATA, install, make a boot floppy, re-plug SATA, boot w/ floppy or choose IDE in bios, then write new (include SATA) grub to SATA mbr? /usr/share/doc/grub-doc/html/grub.html on my Breezy, also the Webmin Grub module might do the trick.

I ran Mandrake, now Mandriva (and others) for years; has strong user community and tends to be bleeding edge, but K/X/Ubuntu IMHO  gets so many things right... it's the tidal surge of Linux distros ;-)

---

### Post by Mr_ on 2006-07-25
right, It won't let me boot into ubuntu at all. It says something along the lines of *you have been logged in to ubuntu for less than 10 seconds* I can't remember the rest of the speel and I wish I could because I know it would the ubuntu developers but I have the worst memory EVER! any how I'm going to reinstall and unplug my sata hdd while I reinstall and hope for the best.

Thankls for all the help that has been offered it is appreciated.

---

### Post by Mr_ on 2006-07-25
ok, back to square 1.

I tried installing with just my ide drive installed and I got pretty much the same response. It anstalled fine, then when it came to booting I get to the login stage, login then I get a message that says:

you have been logged in for less than 10 seconds etc etc, I didn't write the rest down but I did write the log down from the /.xsession-error file that came up with the same error msg.

```

/etc/gdm/presession/: deafault: registering your session with wtmp and utmp
/etc/gdm/presession/: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/log/utmp
/etc/gdm/xsession: beginning session startup...

```

This was using the Ubuntu-6.06-dvd-amd64.iso. But I pretty much get the same error with whatever .iso I use. I hope that helps with respect to why I cannot start ubuntu. That is as far as I can get. Occasionally after installing I can get further but only once and I can't seem to view any files.

---

### Post by Scunizi on 2006-07-25
I had the same issues and finally figured out how to make it work.  I've posted before on this so I reitterate.  I have 2 SATA drives and one IDE.  The first drive is 80 gig NTFS windows xp only.  The second is 130 gig and partitioned for 60 g NTFS and the rest Ubuntu.  In order to get it to work correctly I had to disconnect the IDE from power and the IDE cable. 

Next after booting the live CD I followed the notes on [www.ubuntu.com/download/releasenotes/606](www.ubuntu.com/download/releasenotes/606) - Ubuntu Linux which basically said I had to turn RAID off even though I'm not using it and the CMOS is configured not to use RAID.  

Here's the commands from terminal after booting the live cd. **<sudo mdadm --stop --scan ... then... sudo /etc/init.d/mdadm stop .. then.. sudo vgchange -a n>**  

If you find the release notes online you'll notice I switched the first two commands because I got an error after trying it in the suggested order.  After all is said and done and you can boot into Ubuntu, shut everything down and reconnect your IDE and boot again.  I should run fine.

---

### Post by Mr_ on 2006-07-25
> **Scunizi said:**
> I had the same issues and finally figured out how to make it work.  I've posted before on this so I reitterate.  I have 2 SATA drives and one IDE.  The first drive is 80 gig NTFS windows xp only.  The second is 130 gig and partitioned for 60 g NTFS and the rest Ubuntu.  In order to get it to work correctly I had to disconnect the IDE from power and the IDE cable. 

Next after booting the live CD I followed the notes on [www.ubuntu.com/download/releasenotes/606](www.ubuntu.com/download/releasenotes/606) - Ubuntu Linux which basically said I had to turn RAID off even though I'm not using it and the CMOS is configured not to use RAID.  

Here's the commands from terminal after booting the live cd. **<sudo mdadm --stop --scan ... then... sudo /etc/init.d/mdadm stop .. then.. sudo vgchange -a n>**  

If you find the release notes online you'll notice I switched the first two commands because I got an error after trying it in the suggested order.  After all is said and done and you can boot into Ubuntu, shut everything down and reconnect your IDE and boot again.  I should run fine.

Scunizi, thanks. Is this even if I don't have any raid arrays at all?
2nd question; how do I enter those commands in the terminal(I'm a Linux newbie ;). eg in windows to open dos i would go start-->run-->cmd

---

### Post by yustabeme on 2006-07-26
> **Mr_ said:**
> ok, back to square 1.

I tried installing with just my ide drive installed and I got pretty much the same response. It anstalled fine, then when it came to booting I get to the login stage, login then I get a message that says:

you have been logged in for less than 10 seconds etc etc, I didn't write the rest down but I did write the log down from the /.xsession-error file that came up with the same error msg.

```

/etc/gdm/presession/: deafault: registering your session with wtmp and utmp
/etc/gdm/presession/: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/log/utmp
/etc/gdm/xsession: beginning session startup...

```

This was using the Ubuntu-6.06-dvd-amd64.iso. But I pretty much get the same error with whatever .iso I use. I hope that helps with respect to why I cannot start ubuntu. That is as far as I can get. Occasionally after installing I can get further but only once and I can't seem to view any files.


Q- did you try booting from the dvd in live mode? Why not?

" gdm provides the equivalent of a "login:" prompt for X displays- it
 pops up a login window and starts an X session." You've actually booted Ubuntu, now you're trying to load X (the GUI stuff).

I'm using kdm, but IIRC there's an option to boot to a command prompt in gdm also. Do so. If you don't have that option, press ctrl-alt-f1, log in as user, "$ sudo -i", now you're root- saves typing that silly sudo ad nauseam. Look at your logs - "# dmesg | more" would be a good place to start. See anything suspicious? Write it down, or do you have a floppy? If it's in /etc/fstab ("# cat /etc/fstab"), you can mount it directly to /media/floppy (or however it's listed) eg mine mounts /dev/fd0 at /media/floppy0, so I can "# mount /media/floppy0", or lacking an entry in fstab "# mount -t msdos /dev/fd0 /media/floppy0", or another valid mount point (IOW, the mount point must already exist). Now you could "# dmesg >> /media/floppy0/dmesg", which will write the output of dmesg to a file on your floppy. You might copy other log files from /var/log to the floppy such as Xorg.0.log "# cp /var/log/Xorg.0.log /media/floppy". Unmount the floppy "# umount /media/floppy", boot into Win and report back- now you can open the files on your floppy and copy/paste errors rather than relying on memory and/or tiresome scribbling. BTW, all the quoted stuff are actual commands to enter, minus the """" of course. You might also install midnight commander which will make your life in CLI a bit easier "apt-get install mc", then "# mc".

---

### Post by Mr_ on 2006-07-27
Thanks I have no idea what that means but thank you!

Seriously I was to to do something along them lines but I have no experiance with sudo and I couldn't find any documentation along those lines...maybe I was using the wrong search string. 

Can I grab the files I need if I boot the dvd in live mode? that would solve a few probs if I could

again thanks

---

### Post by Mr_ on 2006-07-28
Thank you yustabeme. I would have never been able to copy them files without your help.

Ok I managed to get some of the recommended files, please find attached. And I hope whoever looks through them has a clue what it means because it's gibberish to me :eek: 

I had to zip xorg.0.log and dmesg they where too big

I hope someone can help identify the problem

tia!

---

