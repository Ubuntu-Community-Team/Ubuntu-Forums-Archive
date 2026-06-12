---
title: "Panel takes ages to load on login with Lucid"
date: 2010-05-30
forum: Desktop Environments
---

### Post by seanlano on 2010-05-30
On Lucid, using the nVidia proprietary drivers, the panel takes about 15-20 seconds to load after loging in. Everything else works fine, I can use my desktop shortcuts and open other programs, just the panel leaves an empty space at the top and bottom, until it loads.
 
I don't have this problem on a laptop with Intel graphics running Lucid, nor when using Nouveau drivers on this computer. I read somewhere that it could be due to *gdmsetup* not having it's config file, but even after trying the suggested workaround (opening gdmconfig and changing settings so the config file is made) the problem persists. 
If I run *"killall gnome-panel"* the panel disappears (not surprisingly) and then briefly pops back up before disappearing again for about 10 seconds.

Could this be something to do with Compiz? With the Nouveau drivers Compiz is disabled, so Compiz is the only thing I can think of that affects the panel differently between the two graphics drivers.

---

### Post by maraja on 2010-06-10
Hi,

same problem here since a couple of days :(

Have you found a solution yet?

thank you

---

### Post by kerry_s on 2010-06-10
do you have no password set for the login manager?

---

### Post by maraja on 2010-06-10
> **kerry_s said:**
> do you have no password set for the login manager?

I must enter the password at login

---

### Post by kerry_s on 2010-06-10
okay, just wondering cause thats what caused slow panels on mine.

try creating a new panel, move everything from the old panel to the new 1, then delete the old panel, repeat if your using 2 panels.

---

### Post by seanlano on 2010-06-10
I don't have a password set on login. 

I'll try the new panel idea, and see how it goes.

---

### Post by seanlano on 2010-06-15
OK, well I tried the new panel idea, and it didn't work. :( 

I've also tried with some new user accounts, and they have the problem as well. This is very strange. 


Is there some sort of log that the Panel writes to about it's status that might give a clue as to what is happening?

---

### Post by seanlano on 2010-06-19
OK, I think I may have found the problem. It's the **GNOME Keyring Service**. I noticed that on my laptop the problem did not exist for my user, but did for others. I had previously modified the startup applications because the default set-up meant UbuntuOne didn't work. I disabled the three default GNOME Keyring Daemon settings, and made just one, with just *_"gnome-keyring-daemon"_* and no extra settings. After making this change for all users, the panel loads very quickly. 


I have no idea why the GNOME Keyring Service causes the panel to s**t itself, but I've read that there have been many problems with it. I'll file a bug report. 

I have noticed, as a side-effect, that sometimes the computer doesn't shut down with this GNOME Keyring set-up (requiring me to use a *"sudo shutdown now -P"* command at a terminal), and sometimes Ubuntu comes up with a dialogue saying *"GNOME keyring manager is not responding. Shutdown anyway?"* at shutdown. Not sure why this is, but it is only intermittent.

---

### Post by omkrasu on 2010-06-27
Hi!

Thanks for the tip with gnome-keyring! But had to do it another way.

The panel took 20 seconds to load even after killing the panel, and turning off keyring hopefully dodged that out...

But this account was for a guest user and it was too slow to be waiting there. Because usually it fired up the gnome-keyring-daemon somewhere switching users, and even if i shut it down, came back.

So i just set at System - Startup Applications (and it may be a shameful thing to do):

killall gnome-keyring-daemon

And the panels load in a flash like they should be.

My question is that does this hold any threats?

Didn't notice the shuting down problem, and the main user didn't lose his keyring.

(Just... Gnome, Key, Ring, Demon -- i think someone loves fantasy literature.)

---

### Post by berman56 on 2010-06-30
I also can confirm that disabling gnome-keyring-daemon solves the delay in seeing the taskbar.

---

### Post by seanlano on 2010-06-30
Yeah, I'm pretty sure it's GNOME Keyring Daemon that is broken. But I can't just disable it, because without it Ubuntu One doesn't work. 

There is an update for gnome-keyring and gnome-panel in the Lucid/Proposed repository, but I'm not sure yet if it fixes this. I think it is supposed to, however. Try enabling the Proposed Updates repository, and see if it helps for you.

---

### Post by hphde on 2010-07-02
Hi,

this bug will be fixed soon. See [https://bugs.launchpad.net/ubuntu/lucid/+source/gnome-keyring/+bug/583428](https://bugs.launchpad.net/ubuntu/lucid/+source/gnome-keyring/+bug/583428) for details.

As a workaround you may run "killall gnome-keyring-daemon" in the startup-applications.

Cheers,
HP

---

