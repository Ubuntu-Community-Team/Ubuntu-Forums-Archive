---
title: "Mezzo / Symphony OS Packages for Ubuntu 7.04"
date: 2007-06-14
forum: Desktop Environments
---

### Post by gtmaneki on 2007-06-14
Hi, guys.  I'm interested in [Symphony OS]("http://www.symphonyos.com/cms/") -- more particulary, in its nifty Mezzo desktop.  

The latest version (2007.6) of Symphony OS is based on Ubuntu 7.04, and I was wondering if it was possible to just install the packages relating to mezzo on my Ubuntu 7.04 system without having to install the full Symphony OS.  I've checked the Symphony OS forums, but haven't seen anything.

---

### Post by gbesso on 2007-06-14
A quick search found [http://fak3r.com/?p=44]("http://fak3r.com/?p=44")
I'm not sure if it works as I haven't tried it.

---

### Post by gtmaneki on 2007-06-14
I've used the instructions in that link before to install an older build of Mezzo on Ubuntu, but that version of Mezzo was still a bit buggy.

The latest release of Symphony OS, however, has an updated version of Mezzo.  The version on the LiveCD certainly seems to work better than the older one.

I'm hoping there's a way to pull the appropriate packages off the LiveCD or off the internet.  I added the CD to the list of repositories using Synaptic (I'm using Kubuntu 7.04), but I couldn't find any packages named "mezzo" when I ran a package search.

---

### Post by gtmaneki on 2007-06-20
I ran across a post in another thread about Mezzo on Ubuntu that gives a how-to:

[http://ubuntuforums.org/showthread.php?t=474934](http://ubuntuforums.org/showthread.php?t=474934)

I'll give it a shot over the weekend.

---

### Post by llamakc on 2007-06-20
Be sure to come back and update us. Thanks.

---

### Post by yotama9 on 2007-06-20
is there a chance for someone to post a quick how to in a more conventional way?
I'm a bit afraid to try and guess what to do every stage

thanks

---

### Post by gtmaneki on 2007-06-28
> **llamakc said:**
> Be sure to come back and update us. Thanks.

Quick update here.  The executive summary is that I haven't been able to put Mezzo on my system yet.

Here's how things have been going:
[LIST]
[*] Installed metatheme using the instructions on [http://fak3r.com/?p=44]("http://fak3r.com/?p=44")

[*] Searched the Symphony OS CD for mezzo.  I was hoping there would be a .deb file somewhere I could just yank, but no luck.  Everything important is in one massive file that uncompresses when you boot off the live CD.

[*] I booted off the CD and before I started looking, but ran out of time (I ended up having to help with a baby shower my wife was throwing).  I did find the FVWM directory, though.
[/LIST]

So I still have to find the proper directories on the LiveCD, copy it to a HD or USB stick, and then set things up.

It'd be nice if we knew where the Symphony OS repository is, and could just pull down the packages directly.

Anyone else have any luck?

---

### Post by gtmaneki on 2007-07-09
I managed to get Mezzo copied over from the SymphonyOS 2007.06 LiveCD onto my Kubuntu 7.04 system.  Here's the howto, based on a thread from the  [Symphony OS forums]("http://www.symphonyos.com/forum/viewtopic.php?t=255&highlight=repository&sid=9603436eb2e7dc876e3fe8559f06e33c").

In order to do this, you'll have to familiarize yourself with editing your /etc/fstab file and using the mount command to manually mount filesystems from the command line.  This is probably the toughest part of the procedure for a novice user.  

[LIST=1]
[*]Know what hard disk partition Ubuntu is installed on.  For my computer, it's /dev/hda7
[*]Install the following packages: fvwm, libxml-simple-perl, libio-all-perl, rox-filer and libxml-rss-perl
[*]Install [metatheme]("http://www.metatheme.org/")
[*]Shut down your computer and boot off the SymphonyOS 2007.06 live CD
[*]Open a terminal.  You'll have to do a lot of work as root in the next few steps, so I typed "sudo su" to become root.
[*]Make a directory to mount your linux partition.  I made the directory /media/linux.
[*]Use your favorite editor to open the file /etc/fstab, and add a line to mount the linux partition on your hard disk.  My line was 
```

/dev/hda7 /media/linux defaults 0 0

```
 then save /etc/fstab.

[*]Mount your linux HD partition.  For me, the command was "mount /media/linux" . 
[*]Copy the folder /usr/Applications from the live filesystem to [/media/linux]/usr on your linux HD partition
[*]Copy the file /usr/share/fvwm/.fvwm2rc to [/media/linux]/usr/share/fvwm on your linux HD partition
[*]Copy the hidden folders /home/ubuntu/.mezzo and /home/ubuntu/.orchestra to your home directory on your linux partition ([/media/linux]/home/gtmaneki for me)

[*]Go to [/media/linux]/usr/share/xsessions/ on your linux HD partition and create the file mezzo.desktop.  In this file, copy the text 

```

[Desktop Entry]
Encoding=UTF-8
Name=Mezzo
Comment=Start mezzo for the desktop.
Exec=/usr/Applications/System/desktop-init
#no icon yet
Icon=
Type=Application 

```

[*]Shut down the computer, remove the Symphony disc, and boot from your normal linux partition.  If you did everything correctly, you will now see Fvwm and Mezzo as desktop environment choices at the logon screen.  But don't select them just yet!  Log on using your normal desktop, and change the permissions for ~/.mezzo, ~/.orchestra, and /usr/share/fvwm/.fvwm2rc so that they are owned by you, not root.
[*] Now logoff and log back on with Mezzo selected as your desktop environment.

[/LIST]

Mezzo should run, and it'll be a little more responsive than on the Live CD.  One thing I noticed, though, is that I'm missing the icon pictures for the four corners, as well as the clock in the top middle of the screen.  I'll keep working on that as time permits; meanwhile, maybe someone else may have a take on it.

Have fun!

---

### Post by yotama9 on 2007-07-18
Is there any update regarding the symphony os icons?

---

