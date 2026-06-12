---
title: "Blank screen as Windows boots"
date: 2006-01-15
forum: General Help
---

### Post by TomPreuss on 2006-01-15
Hi all.

Here's the situation.

sudo fdisk -l

```
Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       16708   134206978+   7  HPFS/NTFS

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38535   309532356   83  Linux
/dev/sda2           38536       38913     3036285    5  Extended
/dev/sda5           38536       38913     3036253+  82  Linux swap / Solaris
```

I've had the Windows drive for a while now, and I just installed Ubuntu on  the SATA drive today.

Ubuntu starts and runs fine, I'm posting from there now.

When I select Windows from the GRUB menu, Windows begins to boot.  I can tell things are starting to happen, but then just before the login screen is supposed to appear, the screen goes blank.  Ctrl+Alt+Delete doesn't respond at that point, and I'm forced to use the reset button.

[This Mircrosoft Knowledge base article](http://support.microsoft.com/?scid=kb;en-us;314503) seems to address the issue, but I'm unsure what steps to take from here.

I'm sure I don't need to tell you guys this, but losing what's on the Windows drive is not an option.

Thank you in advance for your help.

---

### Post by TomPreuss on 2006-01-16
Sorry for the bump, but does anyone have any ideas?

---

### Post by RAOF on 2006-01-16
I don't think that knowledge-base article applies, if it seems to be booting.  Hmm.  Just to clarify - you **do** get the "Windows XP" bootscreen thing, don't you?

You could probably fix the XP install by running the "recovery console" from the XP install disk.  Then run "fixmbr", and it should work.  You won't be able to (easily) boot Ubuntu after that, though - you'll need to boot from a CD to get at Ubuntu.

Alternatively, it's perfectly possible to mount the windows drive in Ubuntu, & copy everything off it.  In fact, that might be a good idea, anyway :)

Finally, did Windows boot after installing the SATA drive, but before installing Ubuntu?  Maybe it's decided that it should be trying to find stuff on the SATA drive?

---

### Post by TomPreuss on 2006-01-17
> **RAOF]I don't think that knowledge-base article applies, if it seems to be booting.  Hmm.  Just to clarify - you **do** get the "Windows XP" bootscreen thing, don't you?[/quote]
I have the [url=http://support.microsoft.com/default.aspx?scid=kb said:**
> /sos switch[/url] enabled, and I do see the list of drivers scroll by.  Just before the login screen is supposed to appear, I get the blank screen.

[QUOTE=RAOF]You could probably fix the XP install by running the "recovery console" from the XP install disk.  Then run "fixmbr", and it should work.  You won't be able to (easily) boot Ubuntu after that, though - you'll need to boot from a CD to get at Ubuntu.
Hmm.  I don't think I'd like to boot from a CD every time.  I'd like for GRUB to continue to do it's job.  Though I think my answer to your previous question my rule out GRUB as the culprit, but I could be wrong.

[QUOTE=RAOF]Alternatively, it's perfectly possible to mount the windows drive in Ubuntu, & copy everything off it.  In fact, that might be a good idea, anyway :)[/quote]
Yes, I have been able to mount the drive just fine and get files from it.  I'd love to not have to ever boot into Windows, and I admit it's been about four weeks since I have, but there are a few things I need to get from there.

[QUOTE=RAOF]Finally, did Windows boot after installing the SATA drive, but before installing Ubuntu?  Maybe it's decided that it should be trying to find stuff on the SATA drive?[/QUOTE]
The first thing I did after installing the SATA drive was install Ubuntu on to it.  I didn't boot into Windows first.  Only after installing Ubuntu and setting it up and rebooting into Ubuntu did I try to boot into Windows.

Thank you very much for your help RAOF.

I look forward to hearing any more suggestions.

---

### Post by RAOF on 2006-01-17
Well, have you tried to boot windows in safe mode?  I think it's F8 at the boot menu (or just after you've loaded Windows from grub, if you don't have a windows boot menu).  Try that, perhaps?

Ubuntu shouldn't be able to mess up your Windows install.  Maybe the addition of the SATA drive is what's messed it up?  Can you disable the SATA controller in the bios, and see if windows will boot then? (If safe mode doesn't work).

---

### Post by TomPreuss on 2006-02-01
I did some testing:

Disconnecting the IDE drive and attempting to boot from the SATA drive does not work.  Nothing loaded after the hardware tests (like one would expect GRUB to), even though the SATA drive was detected by Bios.

Reconnecting the IDE drive and having the SATA drive set as the primary boot device did not work, with the same results as the first test.

Having both drives connected, but having the IDE drive be the primary boot device allowed me to get to the GRUB menu and select Ubuntu from there.  (The same situation as earlier reported though, with Windows being a no-go, but anyway...)

This has led me to the conclusion that GRUB was installed on my IDE drive.  I believe I can fix my problems by doing two things:

1. Install GRUB on my SATA drive.  Right now, I'm not too concerned with dual booting into Ubuntu and Windows, but I'd hope that would be a smaller problem to fix once GRUB is on the SATA drive.
2. Use a Windows recovery CD or somesuch to fix my Windows MBR.

I think I'm capable of working out step two, but can anyone instruct me on the best way to go about step one?

Also, if you spot any flaws in my analysis, please feel free to correct me.  This is all an educational experience.

Thank you in advance for your help.

---

### Post by jocko on 2006-02-01
> 1. Install GRUB on my SATA drive. Right now, I'm not too concerned with dual booting into Ubuntu and Windows, but I'd hope that would be a smaller problem to fix once GRUB is on the SATA drive.
2. Use a Windows recovery CD or somesuch to fix my Windows MBR

Check this out:

[http://www.ubuntuforums.org/showthread.php?t=45492]("http://www.ubuntuforums.org/showthread.php?t=45492")

The last post may help you...

---

### Post by TomPreuss on 2006-02-02
[QUOTE=jocko]Check this out:

[http://www.ubuntuforums.org/showthread.php?t=45492]("http://www.ubuntuforums.org/showthread.php?t=45492")

The last post may help you...[/QUOTE]
Thank you for your reply jocko.

Okay, so here's roughly what I did:

1. Format floppy
2. Make boot floppy
```
sudo mke2fs /dev/fd0
sudo mkdir /media/floppy
sudo mount /dev/fd0 /media/floppy -t ext2
sudo mkdir /media/floppy/boot
sudo mkdir /media/floppy/boot/grub
sudo cp /boot/grub/stage1 /media/floppy/boot/grub
sudo cp /boot/grub/stage2 /media/floppy/boot/grub
sudo cp /boot/grub/menu.lst /media/floppy/boot/grub
sudo cp /boot/grub/device.map /media/floppy/boot/grub
umount /dev/fd0
grub
device (fd0) /dev/fd0
root (fd0)
setup (fd0)
quit
```
3. Shut down
4. Disconnected the SATA drive (leaving the IDE drive connected)
5. Booted with the Windows CD into the recovery console.
6. Ran fixmbr
7. Restarted

This time, no Grub, but Windows loaded exactly as described in my first post (blank screen).

I was then able to shutdown, reconnect the SATA drive, and boot back into Ubuntu using the floppy.

So man, at this point I'm a little more worried.  But I manage to keep it together enough to try to boot into safe mode.  Here's how that went:

1. Shut down
2. Left SATA drive connected (I figure it won't matter, since the IDE MBR is the only thing around.)
3. I start to boot into the Windows drive, but hit F8 and boot into Safe Mode without Networking
4. It works.

Now, I'm pretty hyped.  This didn't work earlier.  After poking around in the Event Viewing and not finding anything out of the ordinary, I did this:

1. Restart
2. Hit F8
3. Choose the "Starts Windows Normally" option (I probably could have just let it boot without going into the boot menu...)
4. Get the blank screen again.

Odd.  I try again.

1. Restart
2. Hit F8
3. Choose the "Last Known Good Configuration" option.
4. Windows starts fine.

Alright, now I think we are okay on the Windows front.  Thank you all for your help.

So how would I go about installing Grub on the SATA drive?

---

### Post by jocko on 2006-02-02
I think this will do it:
```
sudo grub-install /dev/sda
```
or:
```
sudo grub-install /dev/sda --recheck
```

Just check that the entries in /boot/grub/menu.lst are correct before you reboot, when I did grub-install on my computer it changed from hd(1,0) to hd(0,0) and the other way around...

---

### Post by TomPreuss on 2006-02-02
[QUOTE=jocko]I think this will do it:
```
sudo grub-install /dev/sda
```
or:
```
sudo grub-install /dev/sda --recheck
```

Just check that the entries in /boot/grub/menu.lst are correct before you reboot, when I did grub-install on my computer it changed from hd(1,0) to hd(0,0) and the other way around...[/QUOTE]
Yes, I had ended up figuring it out and using the first one you suggested.  Then yes, I had to fix my device.map and menu.lst accordingly.  I removed /dev/hda from the device map and I changed all of the (hd1,0) to (hd0,0) in menu.lst and it worked out fine.

Thank you jocko.

So what do you think the best course of action would be to set up a dual boot, so I could boot into Windows without having to disconnect and connect drives?  The very last entry in my menu.lst is
```
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```I tried changing that to "(hd1,0)" and selecting that from the Grub menu with both drives connected, but that didn't work.  My fdisk -l still looks like it did in my first post, if that helps.

Thanks again.

---

### Post by TechSonic on 2006-02-02
I had this happen to me once, I just hit the restart button on my computer and it loaded fine after that.  I don't think my Windows XP likes being reduced to the only purpose as an Alarm clock and I'm already looking for a Linux app that will let me imput a time for it to sound an alarm to wake me up for work in the morning. Lol  XP hates me now.

---

### Post by jocko on 2006-02-02
So if I understood you correctly your sda1 is (hd0,0), then I guess hda1 must be (hd1,0)? And also you have set bios to boot from sata? If so, I guess you should have the following in device.map:
```
(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/hda
```
and menu.lst should have:
```
title		Microsoft Windows XP Professional
root		(hd1,0)
makeactive
chainloader	+1
```

Try that, but now I remember seeing somewhere that windows needs to be on the first disc (I'm not sure, I've never tried anything else...) If that's true I guess you need to have grub on hda and have hda as first boot device in bios... Then I think the only thing to do is to put grub back on sda (it shouldn't mess up windows, but in case it does it seems like you have learned how to get windows back...)
Good luck

---

### Post by TomPreuss on 2006-02-02
[QUOTE=TechSonic]I had this happen to me once, I just hit the restart button on my computer and it loaded fine after that.  I don't think my Windows XP likes being reduced to the only purpose as an Alarm clock and I'm already looking for a Linux app that will let me imput a time for it to sound an alarm to wake me up for work in the morning. Lol  XP hates me now.[/QUOTE]
Thanks TechSonic, but hitting the restart button isn't going to work.  I need to know how to set up Grub for my computer's configuration.

I'm not using Windows as an alarm clock, so I'm not exactly sure what you're getting at there.  Perhaps [this article](http://ubuntu.wordpress.com/2006/01/22/how-to-use-your-linux-machine-as-an-alarm/ ) would help you?

---

### Post by jocko on 2006-02-02
I just found something that could help if what I said in my last post is true...
If I interpret this thread correctly:
[http://www.ubuntuforums.org/showthread.php?t=116093]("http://www.ubuntuforums.org/showthread.php?t=116093")

This should make windows think it's on (hd0,0):
```
title		WindowsXP Pro
rootnoverify 		(hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1
```

---

### Post by TomPreuss on 2006-02-02
[QUOTE=jocko]I just found something that could help if what I said in my last post is true...
If I interpret this thread correctly:
[http://www.ubuntuforums.org/showthread.php?t=116093]("http://www.ubuntuforums.org/showthread.php?t=116093")

This should make windows think it's on (hd0,0):
```
title		WindowsXP Pro
rootnoverify 		(hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1
```[/QUOTE]
That worked perfectly jocko.  Thank you ever so much for your help.

---

