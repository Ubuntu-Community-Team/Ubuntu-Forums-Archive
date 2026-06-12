---
title: "New Monitor - display shifted off-screen"
date: 2005-08-25
forum: Desktop Environments
---

### Post by Optiker on 2005-08-25
I installed Kubuntu for the first time with minimal problems and was pleased with the result. Then  I replaced my monitor with a new one and have a problem.

The old was a Dell (Sony) 20" crt, and the new is a Sony 20" flat panel. When Kubuntu boots, the display is shifted to the right so that about 2/3 of it is displayed, and the rest is off-screen to the right. No distortion or anything like that.

I tried using the monitor controls to shift it back, but no success.

Suggestions?

Thanks!
Optiker

---

### Post by nickpaton on 2005-08-25
I am not familiar with the Sony flat screen, but is there an auto setting within, say the monitor menu, which allows the monitor to automatically self-centre the picture to correctly fit the screen?

The reason why I mention this, is that with my Sharp flat screen using the analogue input, the picture was slightly off to one side, however using the auto command within the main menu allowed the monitor to self centre the picture.

If this does not help, can you give more info like what graphics card you are using, and whether you are using analogue or digital into the monitor; also the monitor model.

Someone else then may be able to help.

---

### Post by Seth on 2005-08-25
[QUOTE=nickpaton]I am not familiar with the Sony flat screen, but is there an auto setting within, say the monitor menu, which allows the monitor to automatically self-centre the picture to correctly fit the screen?

The reason why I mention this, is that with my Sharp flat screen using the analogue input, the picture was slightly off to one side, however using the auto command within the main menu allowed the monitor to self centre the picture.

If this does not help, can you give more info like what graphics card you are using, and whether you are using analogue or digital into the monitor; also the monitor model.

Someone else then may be able to help.[/QUOTE]
 Use xvidtune to generate a scanline, then paste that into xorg.conf :)

---

### Post by Optiker on 2005-08-26
Nick...tried the autoadjust setting on the monitor - nothing. It's analog RGB, but don't have the graphics card or monitor model here - will reply with that on Monday from work where the computer is located.

Seth...am Linux newbie, so not sure I can handle that, but will try on Monday.

Thanks both!
Optiker

---

### Post by Optiker on 2005-08-29
Nick...graphics card is NVIDIA Quadro FX 500, and monitor is Sony SDM-S204/B.

Seth...nope...too newbie...ran xvidtune both in a terminal (?) and gui, but didn't know what to do with it...didn't see a "line" to copy and paste, didn't know where to find xorg.conf, and finally don't know how to copy and paste in Linux anyhow. Besides, the warnings that came up with xvidtune promised permanent damage if a guy didn't understand what he's doing - describes me perfectly - so essentially scared me off from trying anything. Only solution is step-by-step walk through of how to do this, and that may be asking too much.

This is very discouraging...seems to be exactly the kind of thing that happens that discourages newbies from switching to Linux on their desktop. Always seems to be one essential element of the setup that doesn't quite work, and newbies usually aren't quite up to fixing. The past several times I've tried, it's been graphics problems, printers, modem, printers again, graphics again...that doesn't include difficulties in installing new apps. I've tried Red Hat, Mandrake, Debian, Libranet, Mandrake again, and now Kubuntu - mostly with the promise of being "different" and more friendly to newbies than the previous one, and always with the assurance that it will work. Knoppix live almost worked, but still had trouble with printers.

Thanks anyhow for replies! I'll probably let it sit unused again till the next time I am feeling especially enthusiastic about switching.

Optiker

---

### Post by maruchan on 2005-08-29
I have the exact same thing happening, but it only shifts the KDE load screen down and to the right. The normal KDE desktop is just fine, as is the GNOME login manager. I have an FX 5500 and a Samsung 19" monitor.

It's probably more a KDE problem than a Kubuntu problem.

---

### Post by incinerator on 2005-08-29
I don't think this is a problem specific to kde. Switching monitors often requires some slight adjustments to the x-servers configuration. If you switch from an crt to a lcd monitor the gfx card simply has to do things slightly differently. That starts with picking the right display re-fresh frequency and probably involse other, more subtle things, too.

It is clear that you will need to adjust your /etc/X11/xorg.conf file some way or another in order to reflect the new configuration. However, it may be sufficient to let the box reconfigure the x-server automatically. In order try that, do this:

1.) Make a backup copy of /etc/X11/xorg.conf
2.) log off kde and log into a console
3.) sudo /etc/init.d/kdm stop
4.) dpkg-reconfigure xserver-xorg
5.) sudo /etc/initd./kdm start

Another, more complicated way is running the kubuntu livecd and, once kde is running, copying its /etc/X11/xorg.conf onto a USB stick or floppy, then booting your installed kubuntu and replacing the file, making a backup copy of the old one in case anything goes wrong.

---

### Post by KPingus on 2005-08-29
Optiker,

I assume you have the Nvidia drivers compiled and installed properly.
Your new monitor probably has different specs. The relevant information that you should try to find about it are:

- the horizontal and vertical refresh rates
- the display size

You can usually find that either in your monitor user's manual, on the manufacturer's website (in some knowledge base of some kind), or, if you're lucky, it is already in the X.org log file. To make sure, type the following at a command prompt:

% grep 'Image Size' /var/logXorg.0.log

My system responds:

(II) I810(0): clock: 108.0 MHz   Image Size:  357 x 286 mm

% grep 'HorizSync' Xorg.0.log
(II) I810(0):   HorizSync 30-83

grep 'VertRefresh' Xorg.0.log
(II) I810(0):   VertRefresh 50-75

Your values will likely be different. If those commands don't produce any result, you'll have to find out those values from, e.g., your vendor's website.

Edit the text file /etc/X11/xorg.conf and look for a section called "Monitor". Insert (or replace) the lines

        HorizSync       30-83
        VertRefresh     50-75
        DisplaySize     357 286

(substitute the values that you observed earlier). Save and exit.

Exit all X applications (including the X server): press [Alt][F1] to escape to a console and say:

% sudo /etc/init.d/kdm stop
% startx

you will see if the nvidia driver now has correct adjustments.

If the above doesn't seem to work, edit your /etc/X11/xorg.conf and replace the line

     driver     "nvidia"

by

     driver     "nv"

start X, then look through /var/log/Xorg.0.log for the above info.

Let us know.

---

### Post by Optiker on 2005-08-30
Y'all...What's the emoticon fro a sheepish grin? Following that, I owe y'all an apology for an unnecessary rant!

I decided to give it some more thought, and while I don't think I got to the root of the problem, I have gotten it working. I decided to try 1600 x 1200, the resolution set for Kubuntu (I think that was the default when I installed?), in WinXP and got the same behavior, namely, the desktop appearing as if it was shifted to the right by about 1/4 to 1/3 of it's width. This suggested that perhaps that resolution was not compatible with either WinXP or Kubuntu on my hardwre as it was set up. I checked the monitor's specs and it is supposed to support that resolution, but haven't checked the graphics card yet. In any case, it works. I would like to find out what the source of the problem is just in case I am just missing a setting someplace that is keeping me from using 1600x1200.

Thank you all for your response to my discourteous rant yesterday. You are very gracious for sticking with it.

I continue to be cautious about switching to Linux until I find I have a clean and working system, oruntil I am too frustrated to continue, but perhaps next time I'll remember to save the rant.

My next "problem" is that from Kubuntu, using Konquerer, I can get to where I see icons for all drives, including my Windows drives, but when I click on them and select to mount them, I get a message that they aren't found. I want to automount them when I start Kubuntu. I saw a recent post on this forum that said that the guy mostly missed Mandriva's graphical tools for configuring - this is one of those situations. In Mandrake (Mandriva), for some reason the default installation set up to automount all drives.

I searched the man pages, but only turned up stuff on mounting floppies, and while the man pages might be fine for more Linux literate folks, I had trouble following...just not verose enough for me.

 No need to reply regading mounting drives in this thread. I saw a post someplace addressing automounting, so will do my homework first and try to find it again, then if I haven't been able to get it done, will post for help.

Hopefully, one of these days, the basics will be in place and working and I can start using Linux to get some work done.

Appreciatively...
Optiker

---

### Post by incinerator on 2005-08-30
Check [this](http://ubuntuguide.org/#windows) section of the ubuntuguide. I don't really like their approach, though. I use an fstab line like this:

/dev/hda2       /media/hda2     ntfs ro,user,noauto,uid=1000,gid=1000 0 0
(/dev/hda2 being my windows partition)

That won't mount the windows partition automatically, but will allow konqueror to do it. Also, unlike the setup at the ubuntuguide, this will allow only the primary user (the one you set up during installation) to have access to the partition. You can use other uids or gids (look up /etc/passwd and /etc/group for cross-matching) if you want.

---

### Post by Optiker on 2005-08-30
incin...

I'll check the guide, but will also take a look at fstab. The few times I've looked at fstab, I've always been uncertain as to which drive is named what, but will have a go at it.

Thanks!
Optiker

---

### Post by incinerator on 2005-08-30
The name of the drive is easy to find out. In konqueror, just point the mouse at the icon of the "storage medium" you want to mount and wait a second or two. A wee info popup should appear and the last line contains the name of the device node.

---

### Post by Optiker on 2005-08-31
incin....

The two drives are /dev/sda1 for the C-drive (NTFS) and /dev/sda5 for the D-drive (fat32). The D-drive is the more important for my purposes.

I went in and tried to edit fstab, but it wouldn't let me save the edited version. I assume it's a problem with permission - need to be logged in as superuser? How do I do that?

However, using a EXT filesystem utility I was able to access, edit and save it in a text editor in Windows. But, I had just copied the lines from the ubuntuguide (for NTFS aread only and fat32 read/write) and changed the numbers, so still don't know if that will work. I am sending this from Konqueror in Kubuntu, so can't change from the \hda that Iput in per the guide to the \sda that I get as the drive name in Konqueror as you suggested.

Why sda instead of hda?

That's the status...I'll make the changefrom hda to sda and try again when I reboot back into Windows.

Thanks!
Optiker

---

### Post by incinerator on 2005-08-31
Well, if your /etc/fstab says /dev/hda? then you should keep it that way. If it says /dev/sda? then you should keept it that way, too.

For superuser access when running the livecd, just use sudo as normally.

I don't recall exactly, but if the livecd mounts your hard disks, it will mount them read-only. You will have to change that if you want to actually change files.

---

### Post by Slackitude on 2005-08-31
If your drive is showing as sda that should mean you have a serial ATA hard drive. Either that or scsi but it's unlikely you have scsi and don't know it whereas serial ATA is becoming common enough that a store bought Dell or something might quite possibly have it and not make a big deal about it. In my case my hard drive partitions are sda and my dvd rom and dvd burner are hda and hdc respectively. If I use the Ubuntu guide, or any other for that matter, I have to change it to sda for it to work on my drive. If one way doesn't work try the other I don't think it will hurt anything but someone with more knowledge than me might be able to correct me on that. Oh and probably the quickest way to edit fstab is to open /etc in konqueror and right click on fstab and under "actions" choose "edit as root" I don't know if any of that helps but hopefully so, sorry if I'm just telling you stuff you already knew.

---

### Post by Optiker on 2005-09-01
incinerator...I am running Kubuntu installed, not liveCD. As for using sudo "as usual", as a newbie, there is no usual - I don't know what using sudo as usual means. I'm still confused about root, admin and su. In Windows, if I had admin permissions, I could do whatever. Here, in the user manager thingy, it shows me in the admin group, but still can't edit and save fstab. Also, the names that show up when I hover over drive icons are sda. I used the lines from the guide, but changed numbers, then when that didn't work, changed the hda to sda. That didn't work either.

Slackitude...yes, the drive is a Maxtor DiamondMax Plus9 160 GB HD, model 6Y160M0, SATA interface. I initially just used the line from the guide but replacing the zero in the name with the correct numbers. When that didn't work, I got the name of the drive from the mouse-over of the icon in Konqueror, oer incinerators reply, and replaced the hda with sda. At this point, still not working. Still, when I try to mount in Konqueror, get a "not found" error.

Still listening for anybody still willing to offer suggestions.

Thanks!
Optiker

---

### Post by incinerator on 2005-09-01
Editing files as root: [check this](http://kudos.berlios.de/kf/kf1.html#rootedit)

---

### Post by Optiker on 2005-09-01
Incin...I think I can handle that. Am in the middle of task in Windows, but when I finish, will try that.

Of course, based on my last post, I'm not sure what to do next since I did edit fstab from Windows using the EXT utility, and it still doesn't work, so not sure what to change next.

Here's the current fstab wher the last two lines are my Ca nd D windows drives respectively...
-------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
/dev/sda5       /media/windows  vfat    iocharset=utf8,umask=000   0       0
-------------------
Other htan the names, I copied the lines from the respective lines in the guide that apply to NTFS read only and fat read/write. The names are those shown when I mouse-hover over teh icons in Konqueror.

See anything wrong?

Thanks!
Optiker

---

### Post by Slackitude on 2005-09-01
Ok this is weird, i just now pasted the lines right out of the guide into my fstab and mounted my windows partition with it, save for changing the h to s like you. Is there any chance that the ntfs and fat partitions are backwards? I'm not trying to be a jerk it's just the only thing I can think of.

---

### Post by incinerator on 2005-09-02
optiker, I hope you are aware that this fstab of yours mounts two partitions to one single mount point. both the vfat and the ntfs partitions get mounted to /media/windows. This will produce unpredictable, interesting but not particularly funny results :-0

Everything else in the fstab seems to be ok, though.

---

### Post by Optiker on 2005-09-02
Slackitude...It is possible that they are reversed...I've done dumber things. I have checked that several times, but that doesn't mean I've got it right. Will check again.

incinerator...clearly shows my ignorance of Linux...so do I just choose arbitrary names for mount points...like Fred and George, or really creative like CDrive and DDrive?  :)  And if so, is the syntax then...  

/dev/sda1 /media/CDrive ntfs nls=utf8,umask=0222 0 0

...or does it need something else in place of "media" like...?

/dev/sda1 /winstuff/CDrive ntfs nls=utf8,umask=0222 0 0

Seems like, if there was enough motivation, open source programmers could develop a configuration tool that could implement a working default for dummies, but offer flexibility to folks who know what they are doing. If it's so easy to read the system and see what's there so as to be able to report the names of partitions/drives, what's to prevent the next step of a default - or even check box - that offers "automount all drives" at startup using that info. I guess that's called "plug 'n play".  :)

Enough pontificating...I'm away from my work computer where Kubuntu is installed, so will have to wait till Tuesday to verify which is which, and to change names, but will do so then. In the meantime, I still have Mandrake 10.1 on my home computers, and am still floundering around with it...winner take all so to speak!  :)

Thanks both for your continued willingness to help!

Optiker

---

### Post by incinerator on 2005-09-02
Well, you can thank me by adding some "reputation". I need more cups *ggg*

---

### Post by Optiker on 2005-09-06
"Well, you can thank me by adding some "reputation". I need more cups *ggg*"

Incin...sorry...don't know what that means.

Optiker

---

### Post by Optiker on 2005-09-06
Slackitude....maybe they were reversed! I just switched the 1 and 5, and while they still won't mount, the error message says only root can mount. So, now, from Konqueror, how do I mount as root, and then back to the original question, is there a way to automount at least one fo those automatically since it is the data drive that I'd use almost every session?

incinerator...I changed the mount point names to /media/winc and /media/wind respectively. However, as above, it still won't mount via the Konqueror giu.

Thanks!
Optiker

---

### Post by Slackitude on 2005-09-08
Wow...the root thing ought to be a permissions problem (ok that's obvious I suppose) but I don't know how it got borked...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda3       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1       /media/windows  ntfs    nls=utf8,umask=0222 0      0

That's my entire fstab, (I only have the one windows partition) and I don't see enough different from yours to explain the trouble. I wish I had more experience but I'm at a loss here. I do remember cutting and pasting from the guide and having to do a bit of deleting and moving to get everything lined up with the other entries, I don't know if that's even needed but I'm a neat freak. And I noticed when I cut and pasted here it's all out of wack. Might be something there?

---

### Post by Optiker on 2005-09-08
Slack...so here's my complete fstab...see anything wrong?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda5       /media/winc  ntfs    nls=utf8,umask=0222 0       0
/dev/sda1       /media/wind  vfat    iocharset=utf8,umask=000   0       0

One thing I notice and it could be he problem...during boot, lines come up saying that the mount points /media/winc and /media/wind can't be found. I guess that means that I need to do something to create those mount points...right? If so, how do I do that? I've searched several FAQs, Guides, etc, but haven't found anything that tells me in a way I can usnderstand how to create mount points.

Then, that probably brings me back to the question of permissions. In looking through KUDOS Unofficial Kubuntu FAQ, when I looked at the section on "How to "sudo" without prompt for password? (insecure!)" I got into visudo using kedit as instructed in the FAQ, but I don't find my username in the file. He says to find the line...

sami ALL=(ALL) ALL

assuming the user is sami. My file reads...
-------------------------------
# User privilege specification
root ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
-------------------------------

Any thougts on that? It's starting to look like I should just wipe the Kubuntu installation and start fresh. But, I'd rather fix it if I can. Seems I'm learning a few things...albeit very slowly.

Thanks!
Optiker

---

### Post by Optiker on 2005-09-08
Slack, incin...

Inconceivable! It almost works!

Turns out, I did not have the two drives reversed as previously suggested, and as I thought. I also finally figured out that /media/winc and /media/wind are folders, and to create mount points, I just create them in the right place...ie, in the /etc/media path. Is that supposed to be intuitive from looking at fstab...that those are folders?   :)

Then, after creating those two folders and doing the "remount without reboot" as described by the KUDOS FAQ (sudo mount -a), and getting error messages that even to me suggested that maybe the names were switched (as mentioned above), I reversed them and tried again. Inconceivable! It worked!

However, there was an error message - or I should say, warning message as follows...
--------------------------------
[mntent]: warning: no final newline at the end of /etc/fstab
--------------------------------

I've been getting that all along, and as long and hard as I look at my original (before tampering) fstab and the current version, I can't see any differences other than the two added lines. Oh...incidentally, I did put the devices in order (I'm a neatnik also!) but that didn't seem to make any difference. Other than the order, and the fact that the names sda1 and sda5 are really NTFS and fat respectively. So, I still can't figure out that warning. Any help on that? Doesn't seem to prevent it from working, but warnings make me nervous.

Thanks for the help...finally getting close I think.

Optiker

---

### Post by Slackitude on 2005-09-09
Now that you mention it, it's not intuitive at all. The first directions I ever read for that sort of thing had me create the folders first and I remembered that and it never occured to me to ask if you had. I think the thing about "final newline" is because you haven't put a blank line at the end of your fstab file. (Assuming you haven't that is) for reasons known to somebody somewhere but certainly not to me the system gets cranky if fstab doesn't end in a blank line. Just open fstab as root, go the last entry than hit enter to put the cursor below that, I.E: leaving a blank line below the last entry than save the file like that, creating a "final newline" at the end of fstab.

---

### Post by Optiker on 2005-09-12
Slack...Cool!

OK - I've added the blank line (no, didn't have one) to the end of fstab. I am working in Windows right now, and will test it later when I have a chance to reboot, but assume it's going to work.

Incidentally, having the EXT2 filesystem utility is so handy. If I want to do something in my Linux partition while in Windows - like add that blank line - it is so handy and quick to just do it from Windows rather than have to save and close what I'm doing, reboot into Linux, make the change, then reboot back into Windows and open up before I can get back to what I was doing.

I think that it's time to let this thread rest. If I run into anything else, I will open a new thread.

Thanks very much for your help and persistence in staying with me. I'm sure I'm not quite done yet, but am ready to try replacing my Mandrake 10.1 installation with Kubuntu at home. I DLed the new 5.10 Breezy over the weekend, but didn't get around to installing yet. Will install first on my backup computer, then if all goes well, onto my primary computer. For now, will continue to dual boot to Windows as a default, but things are headed in the right direction to increase my use of Linux.

Thanks again!
Optiker

---

