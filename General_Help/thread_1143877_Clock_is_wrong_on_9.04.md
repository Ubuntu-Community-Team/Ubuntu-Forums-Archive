---
title: "Clock is wrong on 9.04"
date: 2009-04-30
forum: General Help
---

### Post by Michael Steinberg on 2009-04-30
I can reset the clock on 9.04 but it always drifts off, going fast. Synching doesn't seem to help. Any ideas?

---

### Post by leonardo_neo on 2009-04-30
Have you synchronized it with local internet server? That way it will synchronize itself automatically with local time?

---

### Post by SentientFluid on 2009-04-30
You're not dual-booting with Windows, are you?

---

### Post by prem1er on 2009-04-30
> **SentientFluid said:**
> You're not dual-booting with Windows, are you?

Dual boot with windows always makes my clock go out of sync.  Why is that?

---

### Post by Michael Steinberg on 2009-04-30
1) I'm supposedly synched with the server at Cornell.

2) No windows software on this machine. And I had no clock problem at all under any earlier version.

---

### Post by SentientFluid on 2009-04-30
> **prem1er said:**
> Dual boot with windows always makes my clock go out of sync.  Why is that?

By default Windows uses local time so when you adjust the time it sets your BIOS time to match.  Ubuntu (and all other *nix distros I know of, including OS X) use UTC time.

Last I checked you could tell Ubuntu not to use UTC time by using the following steps:

In Terminal...
```
sudo cp /etc/default/rcS /etc/default/rcS_backup
sudo gedit /etc/default/rcS
```The first command backs up the file, the second opens it for editing.

Change...
```
# Set UTC=yes if your system clock is set to UTC (GMT), and UTC=no if not.
UTC=yes
```
to...
```
# Set UTC=yes if your system clock is set to UTC (GMT), and UTC=no if not.
UTC=no
```

I haven't tested that in a long time, though.

---

### Post by Michael Steinberg on 2009-04-30
But that wouldn't account for the 20-25 minute difference I've got. All it would do is change the time zone, which is a matter of hours, right?

---

### Post by prem1er on 2009-04-30
> **SentientFluid said:**
> By default Windows uses local time so when you adjust the time it sets your BIOS time to match.  Ubuntu (and all other *nix distros I know of, including OS X) use UTC time.

Last I checked you could tell Ubuntu not to use UTC time by using the following steps:

In Terminal...
```
sudo cp /etc/default/rcS /etc/default/rcS_backup
sudo gedit /etc/default/rcS
```The first command backs up the file, the second opens it for editing.

Change...
```
# Set UTC=yes if your system clock is set to UTC (GMT), and UTC=no if not.
UTC=yes
```
to...
```
# Set UTC=yes if your system clock is set to UTC (GMT), and UTC=no if not.
UTC=no
```

I haven't tested that in a long time, though.

Thanks.  Trailer Park Boys by any chance?

---

### Post by Thelasko on 2009-04-30
> **Michael Steinberg said:**
> But that wouldn't account for the 20-25 minute difference I've got. All it would do is change the time zone, which is a matter of hours, right?

You likely have a worn out BIOS battery.  I just changed one a few weeks back for the same issue.  It works great now.

Way back in Feisty and Gusty, certain processors used to have clock problems with Ubuntu.  They were mostly AMD processors that ran too fast, but my Core 2 Duo ran too slow.  This bug was fixed long ago.

P.S. [I managed to find the trouble shooting guide for the old clock speed bug from 2005.]("http://ubuntuforums.org/showthread.php?t=53094")

---

### Post by CatKiller on 2009-04-30
> **SentientFluid said:**
> By default Windows uses local time so when you adjust the time it sets your BIOS time to match.  Ubuntu (and all other *nix distros I know of, including OS X) use UTC time.

Actually, as of 9.04, Ubuntu defaults to UTC=no.

---

### Post by SentientFluid on 2009-04-30
> **prem1er said:**
> Thanks.  Trailer Park Boys by any chance?


Know of the show, don't understand the question. :)


> **CatKiller said:**
> Actually, as of 9.04, Ubuntu defaults to UTC=no.

Thanks, didn't know that.  Like I said I haven't had to do it in a long time. Ubuntu is single boot now. :)

> **Michael Steinberg said:**
> But that wouldn't account for the 20-25 minute difference I've got. All it would do is change the time zone, which is a matter of hours, right?

Correct, though my response was to the poster who mentioned he was having the issue with Windows and you hadn't mentioned what the time difference was.

Replaced your BIOS battery yet?  Have you verified you are definitely connecting to a time server?  Does it happen when you turn off the auto-update for the time?

[Would this apply]("http://www.ubuntu.com/getubuntu/releasenotes/904#Real-time%20clock%20driver%20not%20loaded%20on%20ARM%20NSLU2")?

---

### Post by dtuza on 2009-05-07
> **Michael Steinberg said:**
> But that wouldn't account for the 20-25 minute difference I've got. All it would do is change the time zone, which is a matter of hours, right?

To tell the truth, I'm actually having the same problem, and have been since Intrepid - I think even since Hardy.  I had hoped with the release of Jaunty that it would fix itself but such is not the way of it, so I've resolved to find a way to fix the problem finally.

When I restart my PC, the time seems correct.  However, after being on for several hours the time starts to lag behind more and more, until I reboot again.  I too am set to sync with internet servers, although they don't seem to actually **do** anything - when I switch to manual mode in the date/time prefs and force a sync, nothing actually happens.

I haven't yet tried replacing my mobo battery, but this computer isn't particularly old so I have yet to be convinced that this could be the issue.

---

### Post by DLG102282 on 2009-05-07
you need to replace the CMOS battery.

---

### Post by ckuter on 2009-05-13
> **CatKiller said:**
> Actually, as of 9.04, Ubuntu defaults to UTC=no.

I installed the full Ubuntu version 9.04 on the usb startup boot disk creator.  It set UTC=yes. Making the change to UTC=no solved my time problem.

---

### Post by CatKiller on 2009-05-13
> **ckuter said:**
> I installed the full Ubuntu version 9.04 on the usb startup boot disk creator.  It set UTC=yes. Making the change to UTC=no solved my time problem.

Fair enough. I was obviously misinformed.

---

### Post by revoltism on 2009-10-25
Yeah, got this problem in intrepid. Did not have it before. Hoped it to be fixed in Jaunty. Now i am running Jaunty 9.10 and still the problem exist. I tried to install the NTP and update through internet with no success. I have been single booting Ubuntu since 9.04.

---

### Post by sheck on 2009-10-31
My system clock was running too fast. 10 seconds ahead every minute. My CPU and RAM were overclocked in BIOS. Once I set them to Auto/Standard speeds, my fast system clock problem was resolved.

---

