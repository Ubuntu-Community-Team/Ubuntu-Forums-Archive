---
title: "What happened to the 'Disks' admin utility in Edgy?"
date: 2006-12-12
forum: Desktop Environments
---

### Post by tomdkat on 2006-12-12
Hi!  Many moon ago, I started [this thread](http://ubuntuforums.org/showthread.php?t=300199) in which I expressed missing the "Disks" admin utility that used to exist in Dapper.  I'm now running Edgy 64-bit and that utility is gone.  I tried connecting an external USB HDD tonight and had to use QTParted to see it.  I was able to see it detected in dmesg output.

I really liked having the "Disks" utility to make it easier to manage partitions and physical drives, etc.

What happened to this utility and how can I get it back?

Thanks!

Peace...

---

### Post by arvindkst on 2006-12-15
try [http://pysdm.sourceforge.net/](http://pysdm.sourceforge.net/) its in edgy

---

### Post by ibanez on 2006-12-15
```
sudo apt-get install pysdm
```

then you will find it under system...Administration.....Storage Device Manager

---

### Post by pjman on 2006-12-19
The documentation for Edgy should be updated to remove the page that says Disks Manager is available under System->Administration->Disks.

[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s02.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s02.html)

---

### Post by az on 2006-12-19
> **pjman said:**
> The documentation for Edgy should be updated to remove the page that says Disks Manager is available under System->Administration->Disks.

[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s02.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s02.html)

I will report this to the docteam.  ([https://lists.ubuntu.com/archives/ubuntu-doc/2006-December/007638.html](https://lists.ubuntu.com/archives/ubuntu-doc/2006-December/007638.html))

As well, disks-admin was dropped from gnome-system-tools because it did not use the newer udev infrastructure.  It needs a rewrite, but perhaps they should just integrate pysdm - which uses udev.

---

### Post by ways on 2006-12-27
in my opinion this new tool can't be compared to disks-admin at all. no matter if it follows new standards or not. anyway to get the old one back?

---

### Post by az on 2006-12-27
> **ways said:**
> in my opinion this new tool can't be compared to disks-admin at all. no matter if it follows new standards or not. anyway to get the old one back?

If it's still part of upstream, you can recompile gnome-system-utils and re-enable it.

Enable the deb-src repository for main and update.

sudo apt-get build-deb gnome-system-tools

sudo apt-get source gnome-system-tools

enter the directory and edit the debian/rules file to enable disks-admin.

Then build the packages.

---

### Post by tomdkat on 2007-01-05
> **ibanez said:**
> ```
sudo apt-get install pysdm
```

then you will find it under system...Administration.....Storage Device Manager

Thanks!

Peace...

---

### Post by msimon1960 on 2007-01-14
> **tomdkat said:**
> Thanks!

Peace...

Don't worry about -- pys doesn't work anyway.

It is incomprehensible to me why disk management would be removed.  FOR THE LOVE OF PETE WHY WOULD ANY SYSTEM DESIGNER REMOVE THE ABILITY TO CONTROL A HARD DRIVE.

I'M NOW STUCK HERE WITH CRITICAL DATA THAT I CAN'T GET OFF THE DISK DRIVE BECAUSE SOME NIMROD REMOVED THE TOOLS IN 6.10!  BY ALL THAT IS HOLY -- WHO CHECKS OUT EACH RELEASE BEFORE IT'S PUT OUT FOR USE?!  DON'T CHA THINK SOMEONE MIGHT HAVE NOTICED!

Pardon me for yelling but I'm having a cow and doubtless in response to my rant some linux propellerhead is going to send me a encycopedia of arcane, obtuse terminal code that I can use to mount a drive.

counting to 10....

counted to 10 again...

Okay -- now that I've suppressed the urge to hunt down and fatally wedgy the nob who authorized the removal of probably the most fundamental, critical tool in any OS - it's time for a serious, and construction question.

Who tests each Ubuntu distro before it's released?  I've got buckets of suggestions on priorities,  useability, and documentation and I'm willing to beta test and provide feedback -- particularly on the OS tools and networking (my #1 all time pet peeve).

How can I help?

---

### Post by msimon1960 on 2007-01-15
Crushed and reload the OS -- psy works now but is inferior to disk admin.  Very limited info and no mount / unmount commands.

---

### Post by msimon1960 on 2007-01-15
> **azz said:**
> If it's still part of upstream, you can recompile gnome-system-utils and re-enable it.

Enable the deb-src repository for main and update.

sudo apt-get build-deb gnome-system-tools

sudo apt-get source gnome-system-tools

enter the directory and edit the debian/rules file to enable disks-admin.

Then build the packages.

How do you enable the repository in 6.10 -- I used to see it in synaptic and now I don't.  Something else been stripped?

---

### Post by Cobikegeek on 2007-01-17
No disk administration tool in Edgy!  That's crazy.  I wish I had known prior to upgrading from Dapper.  Is there a utility in Kubuntu 6.10 with similar capabilities to the disk tool in Dapper?

---

### Post by hikaricore on 2007-01-17
> **msimon1960 said:**
> FOR THE LOVE OF PETE WHY WOULD ANY SYSTEM DESIGNER REMOVE THE ABILITY TO CONTROL A HARD DRIVE.

I'M NOW STUCK HERE WITH CRITICAL DATA THAT I CAN'T GET OFF THE DISK DRIVE BECAUSE SOME NIMROD REMOVED THE TOOLS IN 6.10!  BY ALL THAT IS HOLY -- WHO CHECKS OUT EACH RELEASE BEFORE IT'S PUT OUT FOR USE?!  DON'T CHA THINK SOMEONE MIGHT HAVE NOTICED!

How can I help?

I think you may have mistakenly left your capslock key on during part of your typing episode here.  It is located below the Tab key on the left side of your keyboard, just above your left shift key.  Have a great day.

--Aaron

P.S.  I don't see why you can't mount your drives via fstab at boot time, but to each his own.

---

### Post by sandman652001 on 2007-02-09
Thats exactly how I'm feeling now!

> **msimon1960 said:**
> Don't worry about -- pys doesn't work anyway.

It is incomprehensible to me why disk management would be removed.  FOR THE LOVE OF PETE WHY WOULD ANY SYSTEM DESIGNER REMOVE THE ABILITY TO CONTROL A HARD DRIVE.

I'M NOW STUCK HERE WITH CRITICAL DATA THAT I CAN'T GET OFF THE DISK DRIVE BECAUSE SOME NIMROD REMOVED THE TOOLS IN 6.10!  BY ALL THAT IS HOLY -- WHO CHECKS OUT EACH RELEASE BEFORE IT'S PUT OUT FOR USE?!  DON'T CHA THINK SOMEONE MIGHT HAVE NOTICED!

Pardon me for yelling but I'm having a cow and doubtless in response to my rant some linux propellerhead is going to send me a encycopedia of arcane, obtuse terminal code that I can use to mount a drive.

counting to 10....

counted to 10 again...

Okay -- now that I've suppressed the urge to hunt down and fatally wedgy the nob who authorized the removal of probably the most fundamental, critical tool in any OS - it's time for a serious, and construction question.

Who tests each Ubuntu distro before it's released?  I've got buckets of suggestions on priorities,  useability, and documentation and I'm willing to beta test and provide feedback -- particularly on the OS tools and networking (my #1 all time pet peeve).

How can I help?

---

### Post by Ted_Smith on 2007-02-26
I agree - it was bizarre to remove it. But fear not :

sudo apt-get install gparted 

One thing I have learnt about open-source - if something you like or need is not there, there's almost always an alternative if you have the time to hunt it out :-)

---

### Post by radrick on 2007-03-17
I am new to Ubuntu, but not totally new to Linux. I have been looking at the recent versions of various distributions as I intend to install a system using only Linux on a network with Windows machines.

I had looked at Linux sometime ago and decided as a desktop OS it was not quite ready. I have heard great things about a half dozen new releases so here I am.

Edgy saw my  SATA drive during installation and then totally ignored it when installation was completed. So that is why I am here. I had purposely made the partition FAT32 because I wanted easy access from all networked machines.  I must also point out that this was not the case with MEPIS 6.01 or SUSE 10.2. They recognized the drive and either auto-mounted or asked how to mount it (with a suggestion).

If you do not have Plug and Play capability, or something like it ,for basic devices like storage the OS is primitive (sorry) - unless you only want an OS for power users and geeks. 

A Disk Manager is a utility, not a major application. It should be there because other established OSes have it and this OS will be compared to what exists already - this OS must aim to be better. It may be moved to an out of the way location, but not removed without being noted in the documentation. 

BTW PYSDM worked for me and I used the diskmounter script to fix the missing drive. See: [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions).

Hope I did not sound teachy or preachy, but the basics for a Desktop OS must be maintained or it will not be taken seriously. The typical user does not want to fix the OS when he/she installs it.

I will see how the rest of my experience with Ubuntu plays out. It seems I need a driver for my GeForce video card - getting bird droppings or something when I press  the left and right arrow keys.

---

### Post by 23meg on 2007-03-17
Everyone posting to this thread, make sure you've read [post #5]("http://ubuntuforums.org/showpost.php?p=1906126&postcount=5"), which states the technical reason why it was dropped.

---

### Post by catdriver on 2007-05-14
OK found pysdm, it's a little bit less intuitive, but it works......  ahhhhh learning curve.....

---

### Post by SoloSalsa on 2007-05-14
I miss it, too.  Partition viewing, mounting, and drive capabilities...  All in one EASY place...

---

### Post by motin on 2007-07-11
> **sandman652001 said:**
> Thats exactly how I'm feeling now!

I second that!

I am stuck here with an invalid fstab configuration that mounts my computer's system restore partition in /media making it show up on the desktop...

gparted can't help me. pysdm doesn't recognize the existing /media/sysrestore mount point and as I don't want to risk it not having recognized any other fstab information it cannot help me. 

There is no easy way of installing disks-admin...

What a loss for Linux personal system maintainers!

---

