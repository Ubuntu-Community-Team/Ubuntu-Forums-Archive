---
title: "2nd try - DVDs will not play"
date: 2006-02-08
forum: Desktop Environments
---

### Post by cetol on 2006-02-08
Whenever i insert a dvd in my drive I get the following message:

[ATTACH]5958[/ATTACH]

I ran the automatix script, and I think that all the libs are installed, ran the css script and still nothing.

Help please

---

### Post by Zeroangel on 2006-02-08
Try opening up Totem, then using the _F_ile menu to load the DVD. If you get a message about it not being able to read some file, follow the instructions posted on [this thread](http://www.ubuntuforums.org/showthread.php?t=126776).

Most specifically:
[quote=JakeSpeare]try installing libdvdcss2 from [http://seveas.ubuntulinux.nl/dists/breezy-seveas/all/](http://seveas.ubuntulinux.nl/dists/breezy-seveas/all/) if you cannot play dvd at all. IF dvd is slow, you should install proper drivers for your videocard.[/quote]

---

### Post by cetol on 2006-02-08
Installed the libs. Still nothing. Also if I try to browse the disk there is no files shown like the disk is blank.

---

### Post by cetol on 2006-02-09
Is there no solutions out there???

---

### Post by wrtrdood on 2006-02-09
Are CDs mountable/readable?  Are the DVDs prerecorded or one's created by another computer?  Check the logs in /var/log.  There may be some helpful info there.  Look at messages, kern.log, daemon.log, and debug in particular.  When I have trouble like this I'll open a terminal window and tail the log file *(tail -f /var/log/messages)* while inserting the disk to see what sort of errors it generates.  You need more info to figure this one out.

---

### Post by cetol on 2006-02-09
> Look at messages, kern.log, daemon.log, and debug in particular. When I have trouble like this I'll open a terminal window and tail the log file (tail -f /var/log/messages) while inserting the disk to see what sort of errors it generates. You need more info to figure this one out.


Here is the output from the tail:

```
Feb  9 09:39:09 localhost -- MARK --
Feb  9 09:59:09 localhost -- MARK --
Feb  9 10:19:09 localhost -- MARK --
Feb  9 10:36:50 localhost kernel: [4299367.087000] cdrom: This disc doesn't have any tracks I recognize!

```

It seems I am missing something - but what I dont have a clue.:-k

---

### Post by cetol on 2006-02-10
Still need help, any suggestions?

---

### Post by Master Shake on 2006-02-10
I see yuo ran AUtomatix.  That should do it.  However, perhaps you could try running EasyUbuntu?

---

### Post by Perfect Storm on 2006-02-10
You could try this if you don't mind using another DVD player.

```
sudo apt-get install wxvlc
gnome-volume-properties
```

Pick multimedia tab. In the 'Video DVD Disc' command box:

```
wxvlc dvd:///dev/dvd
```

---

### Post by cetol on 2006-02-10
OK, I have ran Automatix, Easy Ubuntu, changed the player from Totem to VLC and still nothing.

Is it possible the dvd drive is configured wrong? It is a Plextor PX-708 DVD -+ RW drive. The system still does not see any files on the disc (see tail output above).

---

### Post by wrtrdood on 2006-02-14
In my experience the "This disc doesn't have any tracks I recognize!" message indicates that an attempt was made but there's a *read* problem with the drive.  That also fits with the first message you mentioned.  Don't suppose you have another drive or computer to check it on, eh?  Again, can it read a CD?  For that matter, will the computer boot from the CD?  If not, check BIOS settings but it sounds like the drive may be hosed.

One other possibility comes to mind - filesystem support.  You may be missing something there so it can't figure out what the media is.  Are you using a standard Ubuntu install?  That is, no kernel changes or the like?  Something may have been left out.  Just an idea...

---

