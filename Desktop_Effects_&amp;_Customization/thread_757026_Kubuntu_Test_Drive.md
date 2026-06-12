---
title: "Kubuntu Test Drive"
date: 2008-04-16
forum: Desktop Effects &amp; Customization
---

### Post by Virgo53 on 2008-04-16
Hi all- 

I decided to give Kubuntu  a "test drive" to see the differences from Gnome.

So far, I like it- comparatively speaking, but have encountered a snag using the

KleanSweep program along with Konqueror. It seems that now my Maxtor

external hard drive (which is recognized as 203 GB Media (mounted removable

medium)) has read- only permissions through Konqueror and will not allow me to

change the permissions to read and write. I want to create a KleanSweep

Archives directory for storing deleted items on this drive. ( /dev/ sde1)

Any ideas on how this can be accomplished?  :confused:

---

### Post by Zorael on 2008-04-16
Is the drive partition formatted into the ntfs file system? If so, do you have the **ntfs-3g** package installed? At least ntfs-3g is included by default in Ubuntu, but may have been omitted in Kubuntu; I'm not sure. Find and install it along with **ntfs-config**, using either Adept Manager or via a terminal.
```
$ sudo aptitude install ntfs-3g ntfs-config
```
Disconnect your external drive, run ntfs-config - it should pop up under Settings or something in your K menu, alternatively hit Alt+F2 and enter '**kdesu ntfs-config**' - then check the external devices box. If the internal devices box isn't greyed out, check it as well.

Connect the drive again, and hopefully you should have write permissions.

---

### Post by Virgo53 on 2008-04-16
Thanks for your reply Zorael,

In answer to your questions: yes, yes, and yes- the filesystem is NTFS, and I

have both the ntfs-3g package and ntfs-config installed. I tried unplugging

the drive and getting it reconfigured via ntfs-config. Here's what I got:

root@ricvic-desktop:~# ntfs-config

(ntfs-config:29047): Gtk-WARNING **: cannot open display:
root@ricvic-desktop:~# ntfs-config

(ntfs-config:29074): Gtk-WARNING **: cannot open display:
root@ricvic-desktop:~# mount /media/dev/sde1
mount: can't find /media/dev/sde1 in /etc/fstab or /etc/mtab
root@ricvic-desktop:~# mount /dev/sde1
mount: wrong fs type, bad option, bad superblock on /dev/sde1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@ricvic-desktop:~#

I'll keep trying...  :confused:

---

### Post by Zorael on 2008-04-17
Nuh, I wrote a reply to this and posted it last night, but obviously my connection decided to break down on me or something and it never processed.

> **Virgo53 said:**
> root@ricvic-desktop:~# ntfs-config

(ntfs-config:29047): Gtk-WARNING **: cannot open display:
So the configuration application never started, aye? I've had this happen sometimes. You want to try to launch it as *your own user*, but with superuser permissions. GUI programs launched as root sometimes (all of the time?) won't get access to the display you have your X session on. So that'll happen.

What happens if you just run ntfs-config without superuser permissions? Perhaps it'll ask you to authenticate and everything will be fine. Else, try the following.
```
*you*@ricvic-desktop:~$ gksu ntfs-config
```
Try that.

And again, you may want to disconnect your external drive before doing this. At least with internal drives, the checkbox you want to check is greyed out if any ntfs volumes are mounted.


To perform a manual mount, do this.
```
$ sudo mount.ntfs-3g /dev/sde1 *(target folder)*
```
The folder must exist prior to invoking the mount.

---

### Post by Virgo53 on 2008-04-17
Once again, thank you Zorael for your response!

It looks like I need to do some more research on this.

Here's the result from doing a manual mount (I don't

recall having to go through all of this using Gnome!) :mad:

ricvic@ricvic-desktop:~$ gksu ntfs-config


(ntfs-config:31023): libglade-WARNING **: unknown property `deletable' for class `GtkWindow'

(ntfs-config:31023): libglade-WARNING **: unknown property `deletable' for class `GtkWindow'
ricvic@ricvic-desktop:~$
ricvic@ricvic-desktop:~$ sudo mount.ntfs-3g /dev/sde1 /media/sde1
WARNING: Deficient Linux kernel detected. Some driver features are
         not available (swap file on NTFS, boot from NTFS by LILO), and
         unmount is not safe unless it's made sure the ntfs-3g process
         naturally terminates after calling 'umount'. If you wish this
         message to disappear then you should upgrade to at least kernel
         version 2.6.20, or request help from your distribution to fix
         the kernel problem. The below documentation has more information:
         /usr/share/doc/ntfs-3g/README.Debian




ricvic@ricvic-desktop:~$ uname -r
2.6.15-51-686

---

### Post by Zorael on 2008-04-17
You shouldn't need to manually mount it, explore the bookmarks in Dolphin/Konqueror. There's an adress that will get you to a view that'll remind you of the My Computer view in Windows. I think it's system:// and there should be a bookmark to it.

You just needed to get the ntfs-config thing out of the way to get write permissions. Now you can explore ways of accessing the drive itself once attached.

Doesn't it get automatically mounted? Or perhaps that was something else I had set up.

---

### Post by Virgo53 on 2008-04-18
Yes, the external hard drive is now mounted showing ownership of both user

and group as root, with access permissions of owner, group, and others all set

on "can view & modify content". Anyway, I was able to create a directory - folder

naming it "KleanSweep Archives" for storing the results of scans done with the 

KleanSweep program. When I specified to save it to media: /sde1/KleanSweep

Archives/, a window appeared: "Remote Files Not Accepted" along with "You 

Can Only Select Local Files".  :(

I think I'll go ahead soon and upgrade to Gutsy using the recommended

upgrade sequence: Dapper to Edgy to Feisty to Gutsy. Then I'll be all set for 

Hardy!! I'm wondering why Kubuntu won't have LTS with Hardy, while Ubuntu

will have LTS.  :confused:

---

### Post by Zorael on 2008-04-18
This was because of the release of KDE4; it was decided that because of the development focus it will require, Kubuntu 8.04 should be based on it. It received so much negative feedback that they decided to release two versions - one based on KDE3, one based on KDE4. The KDE3 one will still not be LTS, but it will be commercially supported for 18 months. A compromise.

[quote=Kubuntu.org]**Introduction to Kubuntu 8.04**
Kubuntu 8.04, the Hardy Heron, is the next release of Kubuntu, scheduled to be released towards the end of April 2008. This release will introduce the future of desktop computing by incorporating the new KDE 4 desktop as well as providing continued maintenance and support for the KDE 3.5 desktop. With the news concerning the release of the KDE 4 desktop, it was decided by Canonical that Kubuntu 8.04 would not be a Long Term Support (LTS) release.


**Kubuntu 8.04 versions**
Kubuntu 8.04 will consist of two different releases, the commercially supported one featuring the stable KDE 3.5.9 desktop and a remix featuring the latest release of KDE 4.0. The following is a quick breakdown of the type of support and distributions methods which will be made available to Kubuntu 8.04:

Kubuntu[list]
    [*]Rock solid KDE 3
    [*]Commercial support provided by [WWW] Canonical for a term of 18 months
    [*] Release available through ShipIt for everybody as well as downloading[/list]

Kubuntu KDE 4 Remix[list]
    [*]Cutting edge KDE 4.0
    [*]Support provided by the Kubuntu community via [WWW] Ubuntu Forums, [WWW] Kubuntu Forums, IRC, and the [WWW] Kubuntu Users Mailing List.
    [*]Release available through CDs for groups who need it (ie. LoCo teams, conference teams, etc.) as well as downloading[/list]
[/quote]
[Source](https://wiki.kubuntu.org/HardyHeron/Beta/Kubuntu)

---

