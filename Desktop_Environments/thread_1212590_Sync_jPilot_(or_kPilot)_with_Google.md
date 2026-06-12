---
title: "Sync jPilot (or kPilot) with Google"
date: 2009-07-13
forum: Desktop Environments
---

### Post by sloppyc on 2009-07-13
I've got a Palm Centro. I recently ditched Vista 32-bit for Windows 7 64-bit, only to learn that Palm's software doesn't work in 64-bit Windows.

So, since I have two functioning Ubuntu 9.04 boxes that are always on, I figured one of those could take up the syncing duties for me.  

Only problem:  I want my contacts and Calendar synced up to Outlook in Windows.  Syncing Google and Outlook is already sorted.  I just don't have a way to sync between Ubuntu and Google.  

Suggestions?  Links I may have missed in my searching that don't include GooSync?

---

### Post by sloppyc on 2009-07-14
Okay, progress report:

I've managed to use GCALDaemon to create a file that Kontact can sync to.  I've created a symlink in the ~/.kde/.../KOrganizer folder to point to the GCAL-generated .ICS file, which seems to work fine.  

Unfortunately, Kpilot seems to hang at the calendar sync portion of the Hotsync.  The last message I see is the one about starting the calendar conduit, then the message about setting up for the first sync, and how it may take some time... then nothing from KPilot, and my phone says the connection has dropped.


Ideas?  Once I get over this little hump, I should be golden.  

EDIT: Golden except for syncing my contacts.  Dammit.

---

### Post by sloppyc on 2009-07-15
I have purged and reinstalled KPilot, tried syncing to the default ICS file just in case there was an issue with the GCAL-generated, Google-synced file (the file that works fine in Kontact, I might add).  Problem seems to be with the calendar conduit, as it syncs fine with it disabled.  jPilot works fine, but I'd rather use KPilot for its support of the iCalendar format.

[This thread]("http://ubuntuforums.org/showthread.php?t=708713") didn't help.

What's up with KPilot and the calendar sync?  This is beginning to get irritating.

---

### Post by sloppyc on 2009-07-16
No ideas as to why the Akonadi conduit is causing my KPilot to quit on me?

---

### Post by skyjacker on 2009-07-16
> **sloppyc said:**
> Okay, progress report:

I've managed to use GCALDaemon to create a file that Kontact can sync to.  I've created a symlink in the ~/.kde/.../KOrganizer folder to point to the GCAL-generated .ICS file, which seems to work fine.  

Unfortunately, Kpilot seems to hang at the calendar sync portion of the Hotsync.  The last message I see is the one about starting the calendar conduit, then the message about setting up for the first sync, and how it may take some time... then nothing from KPilot, and my phone says the connection has dropped.


Ideas?  Once I get over this little hump, I should be golden.  

EDIT: Golden except for syncing my contacts.  Dammit. I can't solve your problem, but would really like to know how you even got kpilot or jpilot to sync at all.  I have read & tried about every piece of info available on this forum with no luck.  I have a Palm Tungsten E.

---

### Post by sloppyc on 2009-07-17
> **skyjacker said:**
> I can't solve your problem, but would really like to know how you even got kpilot or jpilot to sync at all.  I have read & tried about every piece of info available on this forum with no luck.  I have a Palm Tungsten E.

Firstly, I'm running Ubuntu 9.04 32-bit (sometimes I use KDE as well, but I don't think that makes a difference). 

What I had to do was to edit /etc/modules to add "visor" to a new line at the end of the file:
```

sudo nano /etc/modules

```
Scroll to the end, add "visor"
Save, exit.

Run
```

sudo modprobe visor

```
I actually had to reboot after this, but that may not be necessary.

In the j/KPilot settings, choose "usb:" instead of "/dev/pilot".
I also reduced the baud rate, I think it worked as high as 54,000 o0r whatever the number is.  

This is enough to get jPilot working with my Centro.  Can't vouch for other devices, but from my limited research, this should work for a variety of them.

As for KPilot... I'm stuck.  I just can't get the calendar to sync (as mentioned in a post above; I've narrowed it down to the Akonadi conduit that KPilot uses for the calendar).  Which is a shame, because it uses the iCalendar format that Google uses.  Aside from that, it seems to be good.

Hope that was helpful :)

---

### Post by skyjacker on 2009-07-17
> **sloppyc said:**
> Firstly, I'm running Ubuntu 9.04 32-bit (sometimes I use KDE as well, but I don't think that makes a difference). 

What I had to do was to edit /etc/modules to add "visor" to a new line at the end of the file:
```

sudo nano /etc/modules

```
Scroll to the end, add "visor"
Save, exit.

Run
```

sudo modprobe visor

```
I actually had to reboot after this, but that may not be necessary.

In the j/KPilot settings, choose "usb:" instead of "/dev/pilot".
I also reduced the baud rate, I think it worked as high as 54,000 o0r whatever the number is.  

This is enough to get jPilot working with my Centro.  Can't vouch for other devices, but from my limited research, this should work for a variety of them.

As for KPilot... I'm stuck.  I just can't get the calendar to sync (as mentioned in a post above; I've narrowed it down to the Akonadi conduit that KPilot uses for the calendar).  Which is a shame, because it uses the iCalendar format that Google uses.  Aside from that, it seems to be good.

Hope that was helpful :) Unbelivable!! It worked. Have been trying for several weeks, and finally gave up. THANKS

---

### Post by sloppyc on 2009-07-17
Glad to have helped.  Enjoy :D

---

### Post by sloppyc on 2009-07-19
Ideas as to what's wrong with KPilot's calendar conduit, anyone?

Also, any suggestions on syncing contacts with Gmail?

---

### Post by sloppyc on 2009-07-23
```

14:00:08 Next HotSync will be: HotSync. Please press the HotSync button.
14:00:13 Trying to open device /dev/pilot...
14:00:18 Checking last PC...
14:00:18 KPilot 5.2.2 (KDE 4.2.2) HotSync starting... 
14:00:18 Using encoding ISO-8859-15 on the handheld.
14:00:18 [File Installer]
14:00:18 No Files to install
14:00:18 [Conduit kpilot-conduit-calendar] 
14:00:24 Invalid record mapping. Doing first sync.
14:00:24 Doing first sync. This may take a while.

```
...then it times out on my Centro.  KPilot hangs.

---

### Post by deadtom on 2010-01-15
I know this is a really old thread but I'm having the same exact problem with Kpilot. Hangs on calendar sync. Calendar is trying to sync with google.

Kontact uses the same akonadi resource for kcalendar and works fine before attempting to sync. After attempting to sync the akonadi server repeatedly fails and won't sync kontact with google any more. Restarting akonadi server does no good, have to restart the whole system.

---

