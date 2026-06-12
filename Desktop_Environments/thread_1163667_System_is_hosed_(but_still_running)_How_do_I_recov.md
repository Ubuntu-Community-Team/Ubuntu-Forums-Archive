---
title: "System is hosed (but still running) How do I recover?"
date: 2009-05-18
forum: Desktop Environments
---

### Post by AKADAP on 2009-05-18
I did some updates, and messed with my video settings, system boots, but display is hosed, and the keyboard is dead.

I can access the hard disk with the live CD, but I can't access my windows share to back up my data to my windows PC (more data than will fit on a DVD ROM, lots of pictures).

If I try "recovery mode" from grub, I can't get to the root login because it is asking for a root password, and the only password on my system, my user password, is not accepted.

The fix graphic problems option does nothing.

The fix packages finds no broken packages.

I'm not even sure that I could back up to DVD using the live CD as it needs that CD to run the system.

Is there a way to re-install Ubuntu without killing the user directory?

---

### Post by StooJ on 2009-05-19
> **AKADAP said:**
> I can access the hard disk with the live CD, but I can't access my windows share to back up my data to my windows PC (more data than will fit on a DVD ROM, lots of pictures).

What's stopping you from accessing the windows share? You might need to install smbfs while using the livecd.
```
sudo apt-get update && sudo apt-get install smbfs
```

> **AKADAP said:**
> 
Is there a way to re-install Ubuntu without killing the user directory?

Depends on how the drives were partitioned & mounted when you installed. Is your /home on a separate partition to /?

I'm pretty sure your system can be saved, but regardless of what you do, a backup of your data would be the best first step (just in case).

---

### Post by AKADAP on 2009-05-19
> **StooJ said:**
> What's stopping you from accessing the windows share? You might need to install smbfs while using the livecd.
```
sudo apt-get update && sudo apt-get install smbfs
```



Depends on how the drives were partitioned & mounted when you installed. Is your /home on a separate partition to /?

I'm pretty sure your system can be saved, but regardless of what you do, a backup of your data would be the best first step (just in case).

Apparently, Windows was being flaky yesterday. I boot up today and find that I can access the windows share through the liveCD. Unfortunately, it won't let me copy the 150 GB of files I wish to back up because none of the directories can be read. I even tried to sudo nautilus, but when I do that it can't access the network.

I need to clarify that. I can read and access the files in the home directory, but when I try and copy the home directory to the network share, I get an error message about not being able to read the files.

The behavior I have is that the splash screen comes up, the progress bar goes to 100%, the screen changes to 3 tiny copies of the splash screen side by side at the top of the display in the wrong colors, and the keyboard stops functioning (caps lock does not toggle). I know the system has not crashed because it shuts itself down 3 minutes later due to noone being logged in and mythTV backend being idle. (this is normal behavior for this computer. It is set up to shut down if MythTV has nothing to do and no one is logged in).

---

### Post by AKADAP on 2009-05-19
Which config files should I edit & what changes should I make (assuming I can do so with the live CD) to get my computer to boot using the generic VGA graphics driver?

---

### Post by StooJ on 2009-05-19
> **AKADAP said:**
> Apparently, Windows was being flaky yesterday. I boot up today and find that I can access the windows share through the liveCD. Unfortunately, it won't let me copy the 150 GB of files I wish to back up because none of the directories can be read. I even tried to sudo nautilus, but when I do that it can't access the network.

I need to clarify that. I can read and access the files in the home directory, but when I try and copy the home directory to the network share, I get an error message about not being able to read the files.

Did you install smbfs? You definitely shouldn't need to run Nautilus as root, but as an aside, if you ever do run any graphical program as su, you should use gksudo, not sudo.

---

### Post by AKADAP on 2009-05-20
> **StooJ said:**
> Did you install smbfs? You definitely shouldn't need to run Nautilus as root, but as an aside, if you ever do run any graphical program as su, you should use gksudo, not sudo.

Turns out I did not need to install anything, the problem was windows flakiness. Windows sometimes just does not make its shares available, and requires a reboot to make them show up. the live CD has samba already installed.

I did finally get my home directory backed up. I installed ubuntu on a second hard drive, then booted that with the first hard drive also attached. This let me access the drive and transfer files to the windows machine. I could not just drag the home folder over, apparently there are some files & links that can't be copied. In any case, I was able to copy the files I knew were important from that directory.

Now I need to find where Thunderbird stores my e-mail so I'm sure that is backed up. And find where MythTV stores the recorded TV shows (I'm a few weeks behind) so I don't miss any episodes.

Then I can start attempting to copy the config files from my newly installed drive to the old drive in an attempt to get the system back where it will boot properly again. (wish I knew which files I needed to copy.)

---

### Post by StooJ on 2009-05-20
> **AKADAP said:**
> I could not just drag the home folder over, apparently there are some files & links that can't be copied.
To back up your home directory (and get everything) try using rsync.

```
rsync -av /path/to/your/old/home/directory /path/to/backup/destination
```

That'll backup your whole home directory to somewhere and you can restore stuff from there later on.

> **AKADAP said:**
> Now I need to find where Thunderbird stores my e-mail so I'm sure that is backed up.

/home/username/.mozilla-thunderbird
If you use the rsync command you'll have it backed up.

> **AKADAP said:**
> And find where MythTV stores the recorded TV shows (I'm a few weeks behind) so I don't miss any episodes.

Not sure about MythTV, as I've never used it. Rsyncing the home directory will be a good step, but I've a feeling mythtv uses a database backend (possibly mysql?)

---

### Post by AKADAP on 2009-05-20
> **StooJ said:**
> To back up your home directory (and get everything) try using rsync.

```
rsync -av /path/to/your/old/home/directory /path/to/backup/destination
```

That'll backup your whole home directory to somewhere and you can restore stuff from there later on.

Not sure about MythTV, as I've never used it. Rsyncing the home directory will be a good step, but I've a feeling mythtv uses a database backend (possibly mysql?)

I decided to just copy individual files & directories. A lot of the stuff in that directory is redundant (f-spots redundant copy of my pictures).

I found where MythTV hides its recordings: var/lib/mythtv/recordings. I'm currently copying 180 GB of .mpg files.

---

### Post by AKADAP on 2009-05-20
I got back in!
I used Putty on the windows box to do a remote login, went to usr/share/ati and ran the uninstall script, logged out, waited for mythTV to automatically shut down, powerd up and was back at a normal login screen with a functioning keyboard.

There is a new version of the ATI driver out, I'm downloading it now. I need this to get the native resolution on my monitor 2560x1600.

---

