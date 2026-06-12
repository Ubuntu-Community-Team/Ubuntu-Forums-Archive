---
title: "Grub takes long time to load"
date: 2006-08-10
forum: Desktop Environments
---

### Post by kshitij on 2006-08-10
Hi,

I just upgraded my system to use Athlon 64 X2 4200 with ASUS A8V motherboard. Actually just changed the motherboard and CPU.
The other specs are:
160GB HDD
1 GB RAM
ATI Radeon 9550 series 8x AGP card

Now Grub takes a very long time to load. Here are the details:

When I power on the system, it does POST and immediately proceeds for booting from the first boot device which is HDD in my case.

Now here it waits for >40Sec to locate grub. (I assume it's trying to find bootloader)
Then it shows message like Loading grub stage 1.5 - Another 30-40Sec
Then Loading grub (don't remember exact msg) - Another 20-30sec
Finally comes up with grub menu
And now after menu timeout (3 sec) loads the default operating system which is Dapper Drake 6.06

has anybody experience similar problem? What could be possible cause and remedy for this? 

Is it something to do with the boot boundary? My partition scheme is:

hda1 25GB NTFS      Windows
hda2 2GB  Swap
hda5 8GB  reiserfs  /
hda6 15GB reiserfs  /home
hda7 10GB reiserfs  /opt
hda8 40GB reiserfs  /backup
hda9 50GB FAT32     /data


Please note I am talking about the time taken for grub to show up and not for booting the OS or boot menu timeout.

Also note that with the same configuration it was working with my old motherboard and CPU (Some ECS mobo with AMD sempron 2500+)

Any help will be much appreciated

Thanks
-Kshitij

---

### Post by kshitij on 2006-08-12
Anyone any clues????

---

### Post by dchenbecker on 2006-09-21
I'm seeing the exact same problem, albeit on some older hardware (PII 450). I had FC 2 on this box previously with grub and it booted very quickly. I'm going to try to dig up the version from that distro and see what changed in grub between them. Booting Ubuntu off of the CD comes up fast, too.

Derek

---

### Post by lagagnon on 2006-09-21
Are you saying that you replaced the motherboard and used the same hard drive with the copy of Ubuntu that was loaded when using the old motherboard?

If so that is a NO NO. The hardware on the new mobo is different from the old mobo. You need to rerun the whole Ubuntu hardware detection scenario again. In fact, if I were you I would reload the whole system. Save your /home partition first before you do it of course.

---

### Post by kshitij on 2006-11-13
The problem was system waiting to locate all the IDE devices.

A new thing for me. For western Digital HDD drives, if you are using just one IDE drive you should not set any HDD jumpers.

Thats it and everything is back to normal.

For your comment about reinstall:
Well it was a new install. But, you can replace motherboard without a complete reinstall. I had done that with a Fedora install. However you have to address hardware changes that are not taken care of automatically. Especially Graphics card or any specific peice of hardware you may have. Not tried on SATA or SCSI devices but i guess that should not be difficult if you have drivers ready. Of course this will not be easy for new users. 

For me  my data is always secure on spare HDD. What I am (and maybe for most of new users are) always worried about is my configured installation. 
Ubuntu (or any linux distro for that matter) is not as easy as windows to reinstall. Windows you will have setup programs for all your required apps and the installation wizard is almost same for them Click Next, Next..., Finish.

On Ubuntu you have to go through all those guides and how-tos on this forum to get back the system to same condition as it was before. In my case BInary Graphics drivers, Mulitmedia, Samba, Printer, User accounts, SSH hardening, Apache Server, Java Setup, Mozilla plugins, NX server, VNC, and XGL/AIGLX. All these need to be downloaded as part of install. The process sometimes takes weeks.

My data will always be available on /data which can be an external drive or a separate partition

---

