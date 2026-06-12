---
title: "Messed up ubuntu, unable to get desktop working"
date: 2009-03-05
forum: General Help
---

### Post by Schok on 2009-03-05
I tried to convert my ubuntu into a Mac OS X look using Mac4Lin and was trying to change the usplash into gsplashy (failed to install gsplashy, so reinstalled usplash) and after a reboot, ubuntu does not reboot into desktop and there was no usplash, only the primitive terminal thingy..sry newbie here.

so how do i get back my normal boot up and my desktop?

btw, when i type startx it showed "fatal server error: could not create lock file in /tmo/.tX0-lock

---

### Post by Nano_ext3 on 2009-03-05
You may want to attempt to reload the desktop, by reinstalling it.  At terminal, if you can, type these commands:

To re-install gnome

sudo apt-get install --reinstall ubuntu-desktop

If that does not work,  backup ALL of your precious data that you need, including files, folders, and modified versions of files you made.

Hope this Helps

Cheers

-Nano

---

### Post by lykwydchykyn on 2009-03-05
Are there any errors prior to the login prompt?  Does it say anything about "dropping to a busybox shell"?

Can you post a link to the guide you were following, if there was one?

---

### Post by Schok on 2009-03-06
they were a few, but here's the one i followed most:

[http://maketecheasier.com/turn-your-ubuntu-intrepid-into-mac-osx-leopard/2009/01/08](http://maketecheasier.com/turn-your-ubuntu-intrepid-into-mac-osx-leopard/2009/01/08)
(followed the procedures with this one but the splashy it provided was not for my 64bit ubuntu)

downloaded splashy and lib files from other guides..but followed this one more thoroughly..btw splashy still wasnt installed due to some other error, so i reinstalled usplash

btw there was no such busybox drop error during login (login was done thru cli too)

---

### Post by Schok on 2009-03-06
"sudo apt-get install --reinstall ubuntu-desktop" returned this error:

W: Not using locking for read only lock file /var/lib/dpkg/lock

E: Unable to write to /var/cache/apt/

E: The package lists or status file could not be parsed or opened

---

### Post by Schok on 2009-03-06
i was told to try "sudo invoke-rc.d gdm restart" but it returned an error saying something like this:
```
*Stopping GNOME Display Manager...
return: 24: Illegal number: Stopping
*Starting GNOME Display Manager...
return: 24: Illegal number: Starting
invoke-rc.d: Initscript gdm, action "restart" failed
```

And i tried to install irssi with apt-get thru the CLI but this error occured(with ANY other applications, not just irssi):
```
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened
```

btw, here are some of the errors that showed before login:

```
usplash: No usable theme found for 1024x768
Screen init failed
19+0 records in
19+0 records out
kinit: No resume image, doing normal boot
```

pleeeaaase help..as reinstalling ubuntu takes SO much time coz i need to get my wireless working back AND fix the sound problem again :(

---

### Post by lykwydchykyn on 2009-03-06
Somehow I'm thinking something has gone wrong at boot time, and the disk is being mounted in emergency read-only mode.

Can you look through the output of this command and see if there is a refernence to mounting the drives read-only:
```

dmesg|less

```
I looked through the howto and I didn't see anything that should necessarily be messing up your boot.  Maybe the hard drive is full?

EDIT: Also, during boot if you hit ctrl-alt-f8 you can see more detailed boot messages.

---

### Post by Schok on 2009-03-06
okay..ill be back in a few mins, have to restart to try that..only 1 laptop is available right now. thanx for the quick reply!

---

### Post by Schok on 2009-03-06
oh dont worry bout the boot msgs, that is all shown during boot up right from GRUB but unreadable as they're scrolled too fast.

anyways i tried dmesg|less without knowing what to look for exactly..lol..too many texts..but here are some of the error that i THINK have something to do with the problem..:

```
PM: starting manual resume from disk
PM: resume from partition 8:6
PM: checking hibernation image
PM: resume from disk failed
kjournald starting. Commit interval 5 seconds.
EXT3-fs: mounted filesystem with ordered data
```

i hope that helps...somehow..lol (newbie here..esp in CLI)

---

### Post by lykwydchykyn on 2009-03-06
None of that seems to be the problem.  Basically it's looking for a hibernate image to resume from and there isn't one (because you're not resuming from hibernate) so it doesn't find one.  

From the command line, can you post the output of these commands:
```

mount 
df -h

```

Sorry if that's a lot to type.  It's hard to know what's going on without more information.

---

### Post by Schok on 2009-03-06
i dont mind the typing, its the reinstallation that will bug me..lol brb in a couple of min

---

### Post by Schok on 2009-03-06
hey i took some pics but its not so clear, i hope it helps a bit. wanted to type but was taking some time..if there is any text thats not clear id be happy do type it down n show it again.

---

### Post by lykwydchykyn on 2009-03-06
Ok, based on what I'm seeing I feel confirmed in my guess that something is causing your system to boot-up in read-only mode.  As for what that might be, and how to fix it, that's going to take some more searching.

It would probably be a good first step to boot to a liveCD and run fsck on all the partitions.

Basically, once you boot to the CD, open a terminal and do this:

```

sudo fsck /dev/sda1
sudo fsck /dev/sda2
sudo fsck /dev/sda3
sudo fsck /dev/sda5

```
That may or may not work on sda1 and sda2, since I'm not clear on what FS is on them.  But it won't hurt to try the command.  sda5 is really the one we are concerned with.

Try that, see if there is any notable output, and then try restarting.

---

### Post by Schok on 2009-03-06
can i run those commands thru the CLI? i dont have a spare live CD around..if i need it to run those commands then i have to download one i guess..

---

### Post by Schok on 2009-03-06
ok i tried fsck thru the CLI:

/dev/sda3:recovering journal
/dev/sda3: clean, blablabla files, blablabla blocks (check in 5 months)

/dev/sda5: clean, blablabla fils, blablabla blocks

---

### Post by lykwydchykyn on 2009-03-06
Does it boot normally now?

---

### Post by Schok on 2009-03-06
nope..still the same :(

---

### Post by Schok on 2009-03-06
so my system goes into read-only state and i cant change it? >.<

---

### Post by lykwydchykyn on 2009-03-06
Yep; it's sort of a safety switch.  The problem is that without knowing what's triggering it, I can't know how to fix it.  The answer is somewhere in the boot output, which should be viewable on vt8 during boot (ctrl-alt-f8), or else in one of these files:

/var/log/syslog
/var/log/kern.log
/var/log/dmesg

The problem is, I don't know exactly what to look for, except that something will say some kind of error, and afterwards it will mount the root partition read-only.

I guess you can try this, too, once it's booted:
```

sudo mount / -o remount,rw

```
That will attempt to remount the root in read-write mode.  If that works, you may be able to do some package management.  I'm retiscent to suggest too many "fixes" without exactly knowing what's wrong, though.

---

### Post by Schok on 2009-03-07
hey "sudo mount / -o remount,rw" worked! but its not connected to the internet. how do i connect it manually? was thinking to get irssi so i can get online help from the irc channel.

btw i tried "sudo gdm start" and it actually starts and shows the login screen! BUT no input can be done thru the mouse or even keyboard..so had to do a force shutdown..any other ideas? 

i will go thru the log files n post if i found any errors related to this problem

---

### Post by lykwydchykyn on 2009-03-07
try:
```

dhclient eth0

```
for networking.  Not sure why the keyboard isn't working, unless maybe hal needs to be started:
```

/etc/init.d/hal start

```

---

### Post by calrogman on 2009-03-08
Or if you are using wifi and the wifi is unprotected, you could use
```
ifconfig wlan0 up
iwlist wlan0 scan #note the essid of your router
iwconfig wlan0 essid $your_router_essid
iwconfig wlan0 mode Managed
```
and that *should* be you connected to a wireless router.  Obviously if you have a wifi interface on eth1 or whatever (as I do) you would use that interface instead of wlan0.

---

### Post by Schok on 2009-03-08
ok i kinda messed up my fstab where i changed any "ro"(read only) found in the file into "rw" (read write) and now i can't mount / as ro as previously using the command "sudo mount -o remount,rw /" (produced an error saying it is already mounted or busy or something like that :(

---

### Post by lykwydchykyn on 2009-03-08
Well, it's like I said earlier, we don't know why it is going into read-only mode, but it is presumably doing so because of an error.  Until we know what that error is, we don't know how to go about fixing it, and trying other stuff at random only complicates the matter.

Can you revert your fstab to the original one?  Or is it lost?  Remember, you can edit those files from a liveCD if they can't be written to from the HDD boot.

---

### Post by Schok on 2009-03-09
ok now i can access my linux partitions from my windows..and i dont have my live CD. is there any way i can fix anything, including fstab from windows?

---

