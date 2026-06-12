---
title: "drapes won't open anymore"
date: 2009-06-23
forum: Desktop Environments
---

### Post by jr2 on 2009-06-23
Hi,

I updated my file system to ext4 as described [>here<](http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21), with no negative side effects except that my NTFS Vista partition was mounted as /media/sda1 instead of /media/Vista.

No big deal, except I have several links to folders in Vista, one of which is a bunch of pictures I have set drapes to change the wallpaper to.  So, drapes had opened, leaving the blue colored background.

I unmounted /dev/sda1 from /media/sda1 and remounted it to /media/Vista, and my wallpaper showed up... but the drapes config window that I had left open stopped responding.  So I forced it to quit and tried to re-open.

Now the icon won't even come up. So, having changed the mount point for /dev/sda1 to /media/Vista, (I double-checked, yes, it mounts there on system start now) I restarted... tried to open drapes, and got nothing, just the hard drive lights up for a few minutes.

I fully uninstalled (using Synaptic Package Manager), supposedly including config files, drapes... restarted.  re-installed.  Tried to open drapes. Hard drive lights up for a few then stops.

What's going on?  Am I missing some hidden config file that drapes has corrupted somewheres?  I don't know where those config files are, I was kind of hoping that Synaptic Package Manager had done what it said it would do and zapped it.

---

### Post by Paul Miller on 2009-06-23
Try running drapes from the terminal.  What error does it give?

As for the fix, doing 
[php]
sudo apt-get purge drapes && sudo apt-get install drapes
[/php]
will probably fix it.

---

### Post by jr2 on 2009-06-23
Eh, it just waits... I forgot to mention, when I restart, I get a few instances of Drapes not responding.  It's like every time I open drapes, a new instance opens and freezes.  But I can't find it in the process list in the Ubuntu System Monitor, even though I told it to show all processes, not just mine.  Well, the hard disk light is still going from the instance in the command line which is still waiting, so if it returns something I'll post back.  Otherwise I'll try that command to fix it.

EDIT: Hard drive stopped flashing, console still waiting.  I'll try that command you mentioned.

EDIT2: Didn't work.
I tried using your uninstall command line then restarting then installing - same thing.
There is a file /home/<username>/.gnome2/drapes.xml that has a list of wallpapers and stuff that was not removed, I tried deleting that, uninstalling, re-installing. Nothing.  It's all befuddled somewhere.

---

### Post by natrium on 2011-03-13
> **Paul Miller said:**
> Try running drapes from the terminal.  What error does it give?

As for the fix, doing 
[php]
sudo apt-get purge drapes && sudo apt-get install drapes
[/php]
will probably fix it.


it worked for me, but only if i run Drapes as root
i can't see any wallpaper as a user

---

### Post by natrium on 2011-03-13
this one works!


sudo add-apt-repository ppa:crebs/ppa
sudo apt-get update
sudo apt-get install crebs

---

