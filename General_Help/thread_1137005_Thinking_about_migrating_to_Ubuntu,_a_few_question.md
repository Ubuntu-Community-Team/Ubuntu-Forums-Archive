---
title: "Thinking about migrating to Ubuntu, a few questions"
date: 2009-04-25
forum: General Help
---

### Post by mikeymikec on 2009-04-25
I've played with Ubuntu and other UNIX variants on a number of occasions over the years, so I'm not a complete newbie, but I have a few questions as I am considering altering the setup of my primary PC to have Ubuntu as my primary OS.

1) Should a 19 or 20GB partition be enough for Ubuntu?  I have a separate partition that I will keep my data on, FAT32 most likely (unless Ubuntu can reliably write to NTFS now) as I will still have Win2k as a backup and games OS.

I have three partitions on my 400GB disk:

20GB NTFS, Vista
4GB NTFS, Win2k
rest of disk, NTFS, Apps Data

If I just do a installation of Ubuntu into that 20GB partition, overwriting Vista (which currently does the boot management), will Ubuntu notice Win2k and insert it into its boot management system automatically?  Although I think I will have to back up then wipe everything due to the file system change on the data partition.

I guess I'll chop up the 20GB into 19GB Ubuntu and 1GB swap.

2) My applications needs are as follows:

Firefox, Thunderbird, Sunbird, OpenOffice, VLC (I realise these are all on Ubuntu or can be easily installed)

Nero, Trillian, XnView (image browser program), Picasa (which is more user-friendly for printing).  Suggestions for substitutes please, and I would rather not use WINE.

Is XMMS still a good Winamp substitute?

3) Perhaps this should be asked on mozillazine.org, but I would like to share Firefox, Thunderbird and Sunbird profiles.  I'm used to messing around with these profiles, but not with another non-MS OS.  Has anyone done this successfully?

I recently considered that I have a laptop I hardly use, so my company database-app which runs on Access can go on the laptop, alongside my desktop when I need it, until I migrate the code to ASP onto my server.  Please don't suggest OpenOffice Base, I tried it and thought it was bloody awful compared to Access :)

---

### Post by sanderd17 on 2009-04-25
20 GB is enough to install ubuntu if you keep your own files in a separated partition, Ubuntu will standart recognize all your partitions you have made so also Win2k. only 1 GB swap is a little small but it should work, i would propose 2 or 3 GB swap.

about those programs: picasa works on linux (download it via the google site, not via apt-get), If you use nero for burning dvd's and cd's and for no other uses, Brasero is a good program and it's standard installed in ubuntu. Other work you can do with nero must be done in other applications. About Trillian and XnView I don't know.

XMMS isn't such a good substitute for winamp, I use rhythmbox and I think it's pretty good: you can minimize it to the dock, it responds well to your MultiMedia-keys.

For the rest I can't help you.

---

### Post by cariboo on 2009-04-25
You may run into a problem booting Win2K if you install Ubuntu on the first partition, as Windows needs it's boot loader to be on the first partition of the first hard drive. You may have to rethik your patitioning scheme.

---

### Post by ashmew2 on 2009-04-25
Hi , 

I've used Nero For Linux and i didnt find it as impressive as the one for Windows.But I agree with sanderd17 in the matter that if you just use it for burning stuff and nothing else , you'd be content with Brasero.

As far as Trillian is concerned , as far as i know , its somewhat of a messenger isnt it ? Pidgin could replace it but i dont think pidgin is as good as ive heard about Trillian.
But that's what the LiveCD is for..Just burn a CD , pop it in and try to use Pidgin and other software on it ..You can also download and install stuff you'd like to test on the Live CD. ;)

I am sure someone will reply with the answers you need.
PS - I dont know if you'd be interested to know this , but there is no Macromedia Shockwave for Linux.

---

### Post by mikeymikec on 2009-04-25
re: no shockwave

How about Flash?

---

### Post by ikacer on 2009-04-25
A few comments about program choices:

You may want to try Evolution as an alternative for Thunderbird and Sunbird. Pidgin is a good alternative to Trillian. As for your multimedia needs, a good guide to them can be found here: 

[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

VLC is a pretty good media player, but the best one on Linux really is MPlayer. Unfortunately the version in the repositories is a bit outdated, a guide to setting up the newest version can be found here:

[http://ubuntuforums.org/showthread.php?t=1081070]("http://ubuntuforums.org/showthread.php?t=1081070")

As for music players, I use two. First of is Audacious, which is like a newer version of xmms. It is very lightweight and I use if I just want to open a single music file. For a devoted music player which can manage a large music collection, I use Exaile. Other good alternatives include Amarok and Songbird.

ps flash works fine on linux

edit: I don't know about sharing profiles for firefox etc, but I know Google toolbar can save your settings so it (and your bookmarks) will be shared.

---

### Post by murderslastcrow on 2009-04-25
VLC runs beautifully on Ubuntu, and Pidgin has all the capabilities you'd look for in Trillian, plenty of plugins. The only things not yet implemented in Pidgin are webcam and voice chat, but there are similar programs that do support these features.

XnView has a Linux version, but not in the repositories yet, so you'll likely have to download the deb/bin file from the official website and setup from there.

OpenOffice's Access alternative is probably the most functional one to find so far, but I'll keep an eye out for a better solution.

Also, you may be able to migrate a lot of files/setting directly from your Windows installation as you install Ubuntu, so I recommend that. Then you can just add any files or settings that may not have been added as you notice them.

A good resource for a comprehensive guide to Switching, along with links to Alternatives, can be found [here]("https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows").

---

### Post by edm1 on 2009-04-25
> **cariboo907 said:**
> You may run into a problem booting Win2K if you install Ubuntu on the first partition, as Windows needs it's boot loader to be on the first partition of the first hard drive. You may have to rethik your patitioning scheme.

But surely he/she'll be using grub to boot windows so it won't matter. I swear i've run a windows partition at the end of my HD before without problems.

Also, NTFS support in linux is now very good so no need for FAT32. It sounds like you're ready to go. Most of the software you've mentioned already runs natively on linux and those that don't have alternatives that are just as good if not better. No need to struggle with XMMS when you have the likes of rhythmbox, banshee, songbird and exaile.

---

### Post by kwacka on 2009-04-25
Firstly, space.  This is a laptop with 40 GB harddrive - 8GB for /, 2 GB swap, and 30 GB for /home.

There seems to have been no problem with NTFS for the past couple of years - I had a partition on desktop which was read/writeable (its gone now - I realised I hadn't booted into Windows for over a year).

Trillian - see Pidgin, if you require more from it check out the plugins.
Nero - I prefer K3B (its a KDE application, but you only need some of the libraries, not the full setup)
Winamp - XMMS is just one of numerous media players -you've mentioned VLC (my favourite), Rhythmbox has been mentioned, there's also mplayer, amarok (possibly more whistles & bells than any other) Beep, Totem. 

Settings in Firefox/Thunderbird - see instructions at the 'lifehacker' site [http://preview.tinyurl.com/yvgaye](http://preview.tinyurl.com/yvgaye)

---

### Post by 3Miro on 2009-04-25
20GB is enough.

Don't use Nero under Linux (it is fine for windows, but not Linux). Use either K3B or the Gnome native one (the Gnome one is kind of basic, but gets the job done).

XMMS is fine, I prefer Kaffeine. It has better search options and has direct access to the file system.

There are many image viewers for Linux, pick and choose.

Firefox and Thunderbird rum much better under Linux. This is their "native" environment, I have never used profiles, but those would work the same or better than on windows.

For Access, unless you can migrate to the Open Office Database, I would suggest using windows under Virtual Box.

---

### Post by mikeymikec on 2009-04-26
I inadvertently booted off the latest release live CD this morning (I burnt the ISO last night and left it in the drive :-) ), and noticed a few things:

1) My partitions weren't auto-mounted.  Is this because of it being a live CD, or is this because I'm using a Sil3112 SATA controller?

2) I have a GeForce 7600GS AGP graphics card and a 1280x1024 LCD monitor.  It was running at 800x600 and wouldn't let me increase the resolution through the UI.

3) Damn, I should have checked sound and network while I had it up and running :)  Standard AC97 and an nforce 2 NIC.

PC spec here:  [http://mikeymike.org.uk/mikes/mypc.txt](http://mikeymike.org.uk/mikes/mypc.txt)

---

### Post by Tindytim on 2009-04-26
> **mikeymikec said:**
> 1) My partitions weren't auto-mounted.  Is this because of it being a live CD, or is this because I'm using a Sil3112 SATA controller?
Neither, it doesn't mount the partitions automatically. It does with external drives though.

> **mikeymikec said:**
> 2) I have a GeForce 7600GS AGP graphics card and a 1280x1024 LCD monitor.  It was running at 800x600 and wouldn't let me increase the resolution through the UI.
You'll have to install drivers when you install the OS.

---

### Post by mikeymikec on 2009-04-26
> **Tindytim said:**
> Neither, it doesn't mount the partitions automatically. It does with external drives though.

I did some searching for my SATA / RAID controller (sil3112a, Asus A7N8X-E Deluxe onboard), and I found some guides for mounting existing RAID arrays, but nothing for me just using it as a way of using a SATA disk on my ageing system.  I suppose it will be enough for it to be shown in the install sequence.

> You'll have to install (nvidia) drivers when you install the OS.

I noticed that under the system menu and hardware drivers, is it just a case of going through that UI?

---

### Post by mikeymikec on 2009-04-26
Ok, I've confirmed that Ubuntu uses my sil3112 SATA controller without any further setup required - it recognised it in its partition manager UI, then I noticed my partitions already mounted in the home menu (I think that's what it is labelled).  Also, sound and network work.

So my remaining question is whether getting my GeForce 7600GS AGP going is purely a case of clicking on the driver in the 'hardware drivers' UI and enabling it.

---

### Post by edm1 on 2009-04-26
Yep, easy as that.

---

### Post by mikeymikec on 2009-04-26
Should it detect my PnP-capable 17" LCD monitor and set the res to 1280x1024 full colour automatically? :)

(hopes)

---

