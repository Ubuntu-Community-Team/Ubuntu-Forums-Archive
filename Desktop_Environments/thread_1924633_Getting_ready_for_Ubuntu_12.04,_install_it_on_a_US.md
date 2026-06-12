---
title: "Getting ready for Ubuntu 12.04, install it on a USB key first?"
date: 2012-02-13
forum: Desktop Environments
---

### Post by lucacerone on 2012-02-13
Dear all,
as Ubuntu 12.04 is closer to its release I'm getting really excited about it and can't see the moment I can install it on my laptop.

However, since I've had a few issues with the last distro upgrades this time
I'd like to have a fresh install. The main drawback is that my laptot has not a big enough HD so that I can install it alongside my existing installation and since I use my laptop to work I can't waste a lot of time
deleting and reinstalling everything.

I was wondering if I'd be able to install it on an external HD, and when everything is configured and working fine I can move the installation
on my computer.

Would that be possible? If so can you provide a basic tutorial (or link to it) on how to do it?
I already know how to create an USB installation, what I don't know is how to move everything on my laptop replacing the existing installation
and how to configure grub to make the new OS start.

Thanks a lot in advance for your help :)
Luca

---

### Post by sudodus on 2012-02-13
The short answer is yes. It might be slower at the start, because the communicaton with USB is slower than that of SATA, but you should get a good feeling of how it works.

Is this correct: you want to install Ubuntu 12.04 alpha to a USB drive (not a live or persistent live system, instead a regular installation, but not to an internal drive). The safest way to do it would be to remove the internal drive. Otherwise you might overwrite grub or something else.

The following link describes step by step to make a full install of 11.04 or 11.10 to USB device.
[[COLOR="Red"]_http://ubuntuforums.org/showpost.php?p=11680312&postcount=22_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11680312&postcount=22")

---

### Post by lucacerone on 2012-02-13
Hi Sudosus,
yes it is correct that I want to install Ubuntu 12.04 on an external hdd(I was thinking more to the stable, when it comes out in April, but I might play with the beta first a little bit).
But I'd like to have it as a live installation rather than a static one.
When everything works fine I'd like to "move" the installation
on my hdd and make it become my only installation.
I hope it is a bit clearer now.
Thanks for the link and for the quick reply!

---

### Post by sudodus on 2012-02-13
If you avoid proprietary drivers, your installation on a USB drive should be rather portable, if that is what you want. Or would you want a persistent live system (with a casper-rw file or partition?

It might even be an alternative to boot from an iso file residing on your hard drive, so that you can easily test various new versions of the developing 12.04.

See the following threads

[[COLOR="red"]_http://ubuntuforums.org/showthread.php?t=1885392_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1885392")

[[COLOR="Red"]_http://ubuntuforums.org/showpost.php?p=11227153&postcount=349_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11227153&postcount=349")

---

### Post by lucacerone on 2012-02-13
Thanks again sudoers,
as you might have understood I'm not really a Computer expert,
so I'm sorry if I ask for silly questions.

I don't know what casper is, maybe it is the solution.

My scenario is very simple, actually.

When the new Ubuntu is released I'd like to have it on my machine.
Unfortunately in my experience I've had a few issues when upgrading
to the new release, so I've decided that this time I want to have
a fresh install.
As I use my computer to work I can't waste much time to make a fresh install
straight on my laptop and then reconfigure and reinstall everything.
Instead I'd like to install the new version on an USB hdd, so that I can slowly configure it and customize to my needs.

When the Ubuntu on the HDD works fine, I just would like to replace
the old installation, moving the new installation from the USB HDD to the
laptop HDD.

I don't want to have a portable installation. I could install Ubuntu 12.04 alongside the existing installation, but unfortunately my laptop doesn't
have a disk capable enough to contain two installations and a duplicate of all the softwares and data I use for work.

So the question really is: can I move an USB installation to the main hdd of my laptop?

Thanks a lot again,
I'll go through the links you have suggested to me and hopefully I'll be able to understand how to do it.

Cheers, -Luca

---

### Post by sudodus on 2012-02-13
> **lucacerone said:**
> I don't know what casper is, maybe it is the solution.
...
I'd like to install the new version on an USB hdd, so that I can slowly configure it and customize to my needs.

When the Ubuntu on the HDD works fine, I just would like to replace the old installation, moving the new installation from the USB HDD to the laptop HDD.
...
So the question really is: can I move an USB installation to the main hdd of my laptop?
...
The persistence is achieved by saving the personal data, tweaking and installed programs in a file system in a casper-rw file or partition. You can read details about that on the internet.

But I think you should stick to your original idea, to ***install*** to a USB drive (instead of installing to an internal drive). I think that, later on, you can clone it into your internal drive, as long as you are using less or equal space compared to what there is on the internal drive. Maybe without any problems at all, maybe you would have to change some address in a few files to point to the correct drive.

Anyway, it is important, that you install onto the USB drive when the internal drive is unmounted. Ideally, the USB drive should be regarded as ***/dev/sda*** during the installation, but it might be OK, if you use the ***UUID ***to point to the partitions even if the device designation is different. When you clone the drive and partitions, the UUIDs are also copied.

---

### Post by lucacerone on 2012-02-13
Thanks :) as you can imagine on a laptop is not really feasible to remove 
the internal hdd... 

But I can run an os and work on it, so I guess that shouldn't be a problem.

So say I have a working OS on my USB HDD... How do I clone it one the computer HDD and make it boot?

Thanks a lot for your help,
Cheers, Luca

---

### Post by oldfred on 2012-02-13
I would do a full install to the external drive. But make a separate /home. Then you can just copy the /home from the USB drive to your internal drive and do a new install to the internal. Only if you make a system wide change then you may want a file or two from /etc. And if you add programs, you may want to export a list of installed apps and reinstall. A new clean install is often easier than the image copy if you have high speed Internet. Either way you have some re-configuration required.

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

My backup assumes I will do a clean install, so you can just copy the same data from the USB install to the full install on a drive.
[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---

### Post by sudodus on 2012-02-13
> **lucacerone said:**
> Thanks :) as you can imagine on a laptop is not really feasible to remove 
the internal hdd... 

But I can run an os and work on it, so I guess that shouldn't be a problem.

So say I have a working OS on my USB HDD... How do I clone it one the computer HDD and make it boot?

Thanks a lot for your help,
Cheers, Luca
I have removed  and replaced the internal HDD in laptops. Usually there is a small lid for it, and it is not that difficult. Just look at the manual for your laptop :-)

You can clone it (booted from a USB or CD drive) using a ***Clonezilla ***boot drive or ***dd*** run from an ubuntu live sesssion with the Ubuntu install drive.

Browse the internet to read about Clonezilla and dd. (Clonezilla is safer, dd is simpler)

---

### Post by lucacerone on 2012-02-15
> **sudodus said:**
> I have removed  and replaced the internal HDD in laptops. Usually there is a small lid for it, and it is not that difficult. Just look at the manual for your laptop :-)


I haven't said I can't :) I don't want to remove any hdd..
I want my computer keeping working as it is, till I have a new working
installation on my hd that can replace the existing one...

As I told you, I need my laptop for work :) that is why I'm looking
for ana lternative way to make an installation :)

---

### Post by lucacerone on 2012-02-15
Hi Oldfred, thanks for your reply :)
My problem is that I have some software to install that is not in the repository
and that requires some extra configuration.

I just would like to know, if I have a working installation on an external drive,
cloning it to the laptop hdd would work?

If not what is the reconfiguring that has to be made?

---

### Post by oldfred on 2012-02-15
I think it depends on how you clone it, those that use dd seem to have the biggest issues, but that can also work. dd is also known as Data Destroyer as any typo causes damage that cannot be repaired. I do not recommend dd for backups.

With dd all internal structures are also copied and it is only a same size drive to same size drive. All UUIDs and /dev/sdaX settings then are preserved. But if still using old drive UUIDs are duplicated which makes for big issues.

Full image copy will work but then you have to edit fstab and possibly grub entries. Anthing that uses /dev/sdaX or UUID will have to be updated. Grub also has an entry on the drive to reinstall to on updates, so that has to be updated. 

I only do the partitial backup and assume a new install. But many suggest clonezilla or old school tar.

discussion of alternatives/strategy:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

Full image backups
[http://clonezilla.org/](http://clonezilla.org/)
Free Imaging software - CloneZilla & PartImage - Tutorial 
[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)
Tar backup script:
[https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html](https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html)

---

