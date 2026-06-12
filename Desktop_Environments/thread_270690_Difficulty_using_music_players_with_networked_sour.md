---
title: "Difficulty using music players with networked sources"
date: 2006-10-03
forum: Desktop Environments
---

### Post by dwasifar on 2006-10-03
Recently I split out the "file server" and "desktop" functions of my Ubuntu box to two different machines.  Now I find that pointing Amarok's collection folder at a shared drive on the network makes things flaky on the desktop, subject to random hangs and other unrecoverable errors.  Originally I thought this was because I was running Amarok under Gnome, but I get the same problem, or a variant of it, with any music player.

The file server shares its directories as Samba shares.  The desktop mounts them in /etc/fstab thus:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb1       /storage        ext3    defaults,errors=remount-ro 0       1
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
//192.168.0.25/mp3 /remote/mp3 smbfs username=****,password=****,dmask=777,fmask=777,auto,rw 0 0
//192.168.0.25/misc /remote/misc smbfs username=****,password=****,dmask=777,fmask=777,auto,rw 0 0
```

Thus they appear in the file system as folders, and Amarok can see them.  And sometimes it works fine, but sometimes not.  Since I set up this arrangement life has not been fun on this desktop.  Amarok will hang, or the desktop will freeze, or various other indignities.  I was able to get to the console and run TOP during one such recent occurrence, and saw that although Amarok was frozen, the highest-load process was smbiod, using between 87 and 98% of CPU.  I killed Amarok, but smbiod remained high.  I then killed smbiod and was unable to access the shares any more until I rebooted; restarting samba and mount -a did not help.  

I tested this arrangement with other machines before I put it into operation, and it seemed fine that way.  The two differences between that test and the final implementation:  1) The machine acting as server is a lower powered machine (800MHz Celeron 512MB) than the one used in the temporary test (Athlon 2200+ 512MB), and  2) in the test, they were on the same network switch, whereas in use, they are on two different switches connected to each other.

Could this just be a server bandwidth issue?  Do I need a higher powered machine in the server position?  Or is it dumb to try to run a music player software on a share in general?  Would it help to use NFS instead of Samba?  The share contains about 19,700 mp3s occupying about 120GB of space.

---

### Post by dwasifar on 2006-10-03
bump

---

### Post by dwasifar on 2006-10-05
bump

---

### Post by ohgod on 2006-10-05
Well, I don't really have any good suggestions to fix this, but I don't think it's a network speed issue or a server issue.  I have a similar setup as you, and have no trouble listening to music over the smb share (I've also used nfs in the past without trouble).  

I really doubt bandwidth is an issue, whether they're on the same switch or not.  Also, my fileserver is not as fast as yours and it works fine, so I don't think that's it either.

I'm assuming your mp3s are divided into separate folders.  I suppose having 19K files in one directory could cause problems...

Do you use beagle?  Could beagle be indexing the music share while you're trying to listen to music?

Also, what does top report on the server when you're experiencing problems?

Sorry I couldn't be more helpful...

---

### Post by dwasifar on 2006-10-05
> **ohgod said:**
> I really doubt bandwidth is an issue, whether they're on the same switch or not.  Also, my fileserver is not as fast as yours and it works fine, so I don't think that's it either.

Damn.  I was hoping for a quick fix.  :)

> **ohgod said:**
> I'm assuming your mp3s are divided into separate folders.  I suppose having 19K files in one directory could cause problems...

They're organized into folders by /artist/album.

> **ohgod said:**
> Do you use beagle?  Could beagle be indexing the music share while you're trying to listen to music?

Not currently using Beagle.  I did turn off the autoscan in Amarok, and that helped some, but I still get the occasional freeze.

> **ohgod said:**
> Also, what does top report on the server when you're experiencing problems?

That is an excellent question.  The problem is that the server is not where I can watch it (it's in the basement) and by the time I run down there and fire up TOP, whatever problem caused the freeze is likely to be over with on the server side.

However - this server also feeds a pair of DLink media streamers.  For this it is running Twonky upnp server.  I notice that once in a while, on the streamers, the music halts momentarily and then starts up again.  I'm theorizing that the server is momentarily unavailable for some reason during those periods, and that the streamers can recover but Amarok can't.

The Twonky application uses up a big chunk of RAM.  Perhaps I should streamline it a bit; remove some indexing so it uses less, and see if that leads to a performance improvement in the server.

---

### Post by dannyboy79 on 2006-10-05
"That is an excellent question. The problem is that the server is not where I can watch it (it's in the basement) and by the time I run down there and fire up TOP, whatever problem caused the freeze is likely to be over with on the server side."

I am a linux newbie but do use the log viewer a lot. couldn't you just open the log viewer and read the messages log? or maybe syslog?

also, a shot in the dark, maybe your mount options are making things a little weird, i don't even have stalls using this, //servername/sharename /mountdirectory smbfs credentials=/home/myhomedirectory/. smbpasswd,uid=mylinuxusername,gid=mylinuxgroupname 0 0

i think it's still similar to you using dmask and fmask but it is different and wouldn't hurt for you to try, right?

---

### Post by dwasifar on 2006-10-05
> **dannyboy79 said:**
> "That is an excellent question. The problem is that the server is not where I can watch it (it's in the basement) and by the time I run down there and fire up TOP, whatever problem caused the freeze is likely to be over with on the server side."

I am a linux newbie but do use the log viewer a lot. couldn't you just open the log viewer and read the messages log? or maybe syslog?

also, a shot in the dark, maybe your mount options are making things a little weird, i don't even have stalls using this, //servername/sharename /mountdirectory smbfs credentials=/home/myhomedirectory/. smbpasswd,uid=mylinuxusername,gid=mylinuxgroupname 0 0

i think it's still similar to you using dmask and fmask but it is different and wouldn't hurt for you to try, right?

Those are good suggestions, thanks.  I will add those to the things I try.  Right now it's behaving.  I think I may have fixed an issue on the server.  I went in to strip out some of the indexes being loaded by the Twonky server, and noticed that at some point its settings had changed from "watch content directories for new files" to "rescan every 60 minutes."  If the Twonky server was kicking off a rescan every hour, perhaps that caused a momentary interruption in file service.  So I changed that setting and restarted the Twonky server, and so far I have not had any further unpleasantness with Amarok on the client.  But I'm not convinced yet that the problem is solved.  I'm going to give it a day or two.

---

### Post by dwasifar on 2006-10-06
> **dwasifar said:**
> I went in to strip out some of the indexes being loaded by the Twonky server, and noticed that at some point its settings had changed from "watch content directories for new files" to "rescan every 60 minutes."  If the Twonky server was kicking off a rescan every hour, perhaps that caused a momentary interruption in file service.  So I changed that setting and restarted the Twonky server, and so far I have not had any further unpleasantness with Amarok on the client.  But I'm not convinced yet that the problem is solved.  I'm going to give it a day or two.

I think it's fixed.  Since the Twonky configuration changes, everything has been stable, so I think the rescan load was interrupting the server and causing Amarok to barf.  Thanks to all who offered help.

---

