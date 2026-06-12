---
title: "KDE K menu and Plasma Desktop freeze (12.04)"
date: 2013-09-29
forum: Desktop Environments
---

### Post by colt2x on 2013-09-29
Hi,

I have ran into a strange problem. Last day i switched off my desktop machine, without any problems. Today morning when Kubuntu started up, i clicked on the K menu and nothing happened, but the KDE tray (whole Plasma Desktop) freezed too. Other programs runned fine (restored from previous session, Firefox, terminal window, etc). (Using Kubuntu 12.04 for a half year without any problems.)

I have tried restarting the computer for a several times, but this strange behavior continued. 
If i try to run any KDE programs from command line, they doesn't start. I get the "QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.  " message, but afaik it is not related to this error.
On KDE tray, i can click everything, when it isn't frozen, and widgets are working (until i click the K menu :D ) 
The error appears with effects turned off, and effects turned on, too.

I have tried to create a test user, and log in with that, the Plasma Desktop is working fine with a new user.

Does anyone know that what can be causing this problem? Any help would be appreciate :)

---

### Post by SeijiSensei on 2013-09-29
Did you shutdown the machine from the menu, or just turn off the power?  Shutting off a running Linux box can result in corruption of the drives.  I'm surprised that Kubuntu didn't report that it was checking the drives when you rebooted.

Reboot the machine using the Kubuntu installation disk, then open a terminal ("Konsole") and run fsck against the partitions on your hard drive. I don't think you need sudo for this when running off the installation disk, but if you get a permission denied, use "sudo fsck".

---

### Post by colt2x on 2013-09-29
Hi,

Thanks for your reply, but i shutted it down drom the menu as i do this in the last few years since i'm using Linux :) So after a few reboots and logoff-logons KDE worked OK again. I cannot find any root causes.
Then i shutted down the machine again and now K menu and Plasma Desktop is dead again.

Very annoying...

I will run fsck as i have time, and i will notify you.

---

### Post by colt2x on 2013-09-29
For addition, the Shutdown point is missing from K menu. I can't log off, because the Log off button does nothing. I can log off only with the kdeint4_shutdown command, and the shutdown. The Dolphin windows doesn't appear when started from the K menu, but when logging in, the restored ones from previous session are OK.


With the test profile, these functions are working.

---

### Post by speartip on 2013-09-30
This may be unrelated, but I had a similar problem a few weeks ago.
I kept all my data, on a separate partition, & for some unknown reason lost ownership of that partition causing a plasma desktop freeze.
Once i got ownership of the partition back the problem was solved.
May be similar depending on your setup.

---

### Post by colt2x on 2013-09-30
Hi,

I had to run fsck, and it succeeded, all OK. The error haven't gone, so i deleted my user, and i want to create a new one.

My /home is on the system partition. And from my earlier Linux experiences, if a user's rights aren't OK, then it can't log in... But i speak about when he has none of the rights, you partially had some.

---

### Post by colt2x on 2013-10-01
Strangely i suggest that x11vnc logging caused the problem.
I had a KDE startup file, which starts the x11vnc server after login. I enabled logging in it, and it created a logfile, which KDE wanted to open every time at loin. For some reasons, it can't open the file, and i think this were the root cause... don't know why. But after i disabled VNC logging, everything went OK.

---

