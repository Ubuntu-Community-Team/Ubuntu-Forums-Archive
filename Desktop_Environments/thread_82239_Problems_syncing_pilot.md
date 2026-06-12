---
title: "Problems syncing pilot"
date: 2005-10-26
forum: Desktop Environments
---

### Post by stormy on 2005-10-26
Since upgrading to breezy I have been unable to sync my palm (zire 71).  Dmesg shows that it picks up the zire (ttyUSB0 or ttyUSB1), symbolic link is in place, permissions are ok... I am not sure what else to do.  I have tried gpilot, kpilot and multisync.  My normal configurations (carried over from hoary) do not work.  Is anyone else having this problem too?  Any ideas?
:confused:

---

### Post by timczer on 2005-10-26
Have you tried jpilot.  I tried with a pocket pc and now my new sony clie to sync with all of those programs and never could get them to work.  I tried jpilot a few days ago and after putting the correct usb connection in settings, it worked like a charm.

---

### Post by scubajeff on 2005-10-26
In my Breezy, since udev dynamtically create the /dev/ttyUSB0 and /dev/ttyUSB1, and the /dev/pilot never link to the correct devices file, I put /dev/ttyUSB1 in gpilot configure directly, and it sync like a charm.

Or you can create the ttyUSB* all by yourself. Using the following:
 sudo mknod ttyUSB1 c 188 1
 sudo chmod 0666 ttyUSB1

But don't create this file under /dev, since udev will refresh the directory on the fly, that means it will remove anything under it and re-populate it after reboot.

---

### Post by SWAT on 2005-10-28
In Breezy I just plugin my palm zire and it works.
* Press the HotSync button (or cradle button or whatever)
* Check if it's connected with "lsusb"
* Check if /dev/pilot exists with "ls -a -l | grep pilot" within the /dev directory. On my computer /dev/pilot is a symlink to /dev/ttyUSB1
* Set your Palm client to use /dev/pilot

If /dev/pilot exists when your Palm isn't connect you should remove it. I had to do it because it referenced itself (pilot -> pilot)
DO NOT USE UBUNTUGUIDE! (this was the cause of my problem in Breezy)

scubajeff, just make your own symlink to /dev/ttyUSB1 :P

---

### Post by Roadrunner777 on 2005-11-11
jpilot worked for me right out of the install, no settings, it just works!

---

### Post by David Valentine on 2005-11-30
The good news is that my Sony Clie UX50 successfully communicates with gnome pilot and backs all of its info up into my backup directory.  I'm syncing wirelessly, and it's working great.  

The first problem I'm running into is that I don't see any "conduits" in gnome pilot to jpilot--only to Evolution.  But I don't think I want to use Evolution for my Calendar/ToDo/Address stuff, and would prefer to use jpilot because it's nice and simple.

My second problem is that I have been unable to get jpilot to do anything when I hit its sync button other than giving me this error message > ****************************************
 Syncing on device /dev/pilot
 Press the HotSync button now
****************************************
pi_bind error: /dev/pilot Too many levels of symbolic links
Check your serial port and settings
Exiting with status SYNC_ERROR_BIND
FinishedThis happens with or without the UDEV trick mentioned in the Easy Palm Setup post.  So I guess my question is really a two-fer:  

1.  How do I get jpilot to do its sync thing correctly?  Or,
2.  How do I get gnome pilot to direct data to jpilot?

PS  I'm a total noob on Ubuntu and Linux, though I'm liking both more and more.  Thanks for your help!

UPDATE:  I feel like an idiot, but I think I've solved the problem with jpilot.  In the UDEV rule in the "Easy Palm Device Setup" article on the Ubuntu Wiki (sorry, I tried to put in a link), I had to substitute "Sony Handheld" for "Palm Handheld".  I didn't think it would know the difference, but evidently it does.

---

### Post by Sokraates on 2005-12-04
I had the same problem with my Tungsten E. gnome-pliot, jpilot and kpilot refused to sync after upgrading to Breezy. And they all complained that ttyUSB1 didn't exist. Before ht eupgrade, it worked like a charm.

The solution:

[HTML]$ sudo gedit /etc/udev/rules.d/10-custom.rules[/HTML]

Delete the following line:

[HTML]BUS="usb", SYSFS{product}="Palm Handheld*", KERNEL="ttyUSB*", NAME{ignore_remove}="pilot", MODE="666"[/HTML]

Right. Just the one we all entered to make syncing work with Hoary. :???: 
I figured it out after trying to sync with a breezy live-cd and it worked.

If there are no other entries, you can probably delete the whole file.

**Edit:** Forgot to say, that it now works with jpilot and kpilot, using /dev/pilot or /dev/ttyUSB1.

---

### Post by David Valentine on 2005-12-09
I removed the 10-custom.rules file as you suggested, then completely uninstalled jpilot (including the .jpilot directory) and re-installed it again.  After several attempts, it suddenly worked when I hit my Sony's sync button and typed "jpilot-sync" on the console in pretty rapid succession.  Is this how it's supposed to work?  Isn't there some daemon that I can start that waits for the sync from my pilot?:???: 

Thanks

---

### Post by Sokraates on 2005-12-09
[QUOTE=David Valentine]I removed the 10-custom.rules file as you suggested, then completely uninstalled jpilot (including the .jpilot directory) and re-installed it again.  After several attempts, it suddenly worked when I hit my Sony's sync button and typed "jpilot-sync" on the console in pretty rapid succession.  Is this how it's supposed to work?  Isn't there some daemon that I can start that waits for the sync from my pilot?:???: 

Thanks[/QUOTE]


I regularyly use kpilot and syncig worked as soon as I've removed the line from 10-custom.rules. Only later I removed the whole file, but it didn't make any difference.

As far as I know, you first have to start gnome-pilot, then jpilot will work. So I first tried kpilot, then (for science's sake) started gnome-pilot (worked) and then jpilot (ditto).

The only (possible) explanation coming to my mind is, that you have a bunch of USB-devices and your palm does not always use the same port.

First check, which device /dev/pilot is linking to. It should be ttyUSB1 (usually).

Plugin your palm, push hotsync and type

```
ls /dev/ttyUSB*
```

If the output shows you ttyUSB0 and ttyUSB1, use ttyUSB1 (alway the higher number). Should after a few tries ttyUSB2 and ttyUSB3 appear, some other device is using ttyUSB1 and your palm will not be recognized, if jpilot searches ttyUSB1.

There's a solution for this, too (other than manually telling jpilot to look for ttyUSB3), but I can't remember. Sorry. :( 

For further info, look here:

[http://ubuntuforums.org/showthread.php?t=77387](http://ubuntuforums.org/showthread.php?t=77387)

---

### Post by David Valentine on 2005-12-11
Thanks for all your help on this.

Here's the series of steps that seems to work consistently:

1.  Connect Sony UX50 (my palm device) to USB port.
2.  On PC, launch jpilot (/dev/pilot works fine); on Sony UX50, launch the hotsync applet.
3.  On Sony UX50, tap the hotsync button.
4.  In 1-2 seconds, click the hotsync button in jpilot.  If I time it right, they sync.

What I'd like to do is to not have to launch jpilot or worry about timing things right; I think I should be able to sync successfully simply by initiating the hotsync from my Sony.  I've used gnome-pilot successfully (even with a network sync), but gnome-pilot only has conduits for Evolution (and I don't wish to migrate from Thunderbird).  Even better would be some way of syncing jpilot over a network (is that possible?).

[EDIT]
Yes, it is possible, and easy once I found out how.  In jpilot, select file/preferences/settings, then set the serial port to net:any.  Worked like a charm, and I am one happy camper.

---

### Post by nikolai.m on 2005-12-11
well....i'm using Kpilot. as for recognizing my Tungsten T everything going well. syncing at first glance goes well too. but then i found this strange problem: when i delete entry from Kcontact and hit sync - sync goes without a hitch - but same entry in palm is not deleted!!! i can't find any error messages, or anything?!! please help me if you know how to ....
thnx

---

### Post by Sokraates on 2005-12-12
@ David Valentine:

There has to be a way to launch a daemon when you login, so that you can sync without having to manually start jpilot. It's the way I use kpilot, though kpilot has an option to run a daemon when you login.

Since I use KDE only, I can't tell you how to make this daemon start or what daemon has to be run in the first place.

Also, I'm slightly disturbed by you having to "launch the hotsync applet". On my Tungsten E I only have to tap the hotsync-button.

@ nikolai.m:

There are some settings in kpilot, where you can configure which infos should be synced and whether deleted entrys should be kept on you Palm or in kontact.

Don't know the exact name of these options.

---

### Post by David Valentine on 2005-12-12
OK, glad to hear there likely is a daemon.  Now to find it...

As for the Hotsync applet, the Sony UX50 doesn't actually have a cradle with a button on it.  The user must select that applet from the main Palm OS launcher screen, then tap the picture of the hotsync button.  I think other (older?) Palms work the same way in their travel mode (i.e., without their cradles).

---

### Post by Sokraates on 2005-12-13
[QUOTE=David Valentine]OK, glad to hear there likely is a daemon.  Now to find it...

As for the Hotsync applet, the Sony UX50 doesn't actually have a cradle with a button on it.  The user must select that applet from the main Palm OS launcher screen, then tap the picture of the hotsync button.  I think other (older?) Palms work the same way in their travel mode (i.e., without their cradles).[/QUOTE]

Got it. It indeed works the same way on the Tungsten E, too. the only difference is, that my Palm has a shortcut to hotsync, so I usually "just tap the button". ;)

---

### Post by JackandJohn on 2006-03-05
Here's one of the main reasons people are getting tripped up on this:

In Breezy, the file:
```
/etc/udev/rules.d/udev.rules
```

Already contains the line that is mentioned for creating the "/dev/pilot" symlink.
Therefore, creating it yourself duplicates it, and messes up the whole works.

Personally, I had to change the ttyUSB section to ```
"ttyusb[13579]"
```, and then I was able to sync with jPilot..

Evolution sync: worked great once before all this bit, and now refuses (worked fine, then sync started taking 100% cup and never complete.. not at all related to these udev settings since it happened months ago :))

---

### Post by alpa on 2006-06-18
May be it is not the right place for my question, but I try...

Anybody knows how to syncronize mails, contacts, tasks, calendar between KDE Groupware suite and WinCE ?
I know I can do using Evolution but I prefer to use KDE apps...

Thanks a lot.

Alpa

---

