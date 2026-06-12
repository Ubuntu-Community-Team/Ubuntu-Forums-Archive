---
title: "After updates, GNOME freezes"
date: 2005-03-20
forum: Desktop Environments
---

### Post by jeffus on 2005-03-20
Howdy,

I installed Hoary yesterday and really, really like it.  However, after installing the 200 and some updates, the machine reboots and GNOME hangs--so I see the mouse and can move it, and the brown background is there, but that's it.  Not even sure where to start here....

Thank you,

Jeff.

---

### Post by cdhotfire on 2005-03-20
this happened to me once, i just when to login screen and choose sessions, and instead of choosing last, choose gnome.  Then choose use this as default.  Worked for me maybe ill work for u. :grin:

---

### Post by jeffus on 2005-03-20
Worked.  Thanks a lot.

Jeff.

---

### Post by cdhotfire on 2005-03-20
no problem. :D

---

### Post by jallen7usa on 2005-03-20
I've experienced similar problems.  When I upgrade or install Hoary from scratch all goes fine then within about a minute or to the system hangs.  I though maybe it was the nvidia drivers but I updated my xorg.conf and used the older nv drivers and get the same results.  I'm a linux newbie so I have no idea where to look to trouble-shoot this.  I want to upgrade to Hoary but after a weekend of frustration I'm getting ready to give up.  Any help would be greatly appreciated.

---

### Post by jeffus on 2005-03-20
OK, does it hang completely or can you still ctr alt f1 to a prompt?  

Jeff.

---

### Post by jeffus on 2005-03-20
And now I'm getting the same error as in my first post no matter what session type I try--even the gnome selection as suggested.  However, I did discover that after about 2 or 3 min the rest of gnome loads.  Anyway to figure out what is lagging there?

Jeff.

---

### Post by jallen7usa on 2005-03-20
[QUOTE=jeffus]OK, does it hang completely or can you still ctr alt f1 to a prompt?  

Jeff.[/QUOTE]
It hangs completely.  No mouse movement, no response to ctrl+alt+f1/back-space etc.  I have to do a hard reboot.

---

### Post by pranith on 2005-03-21
hey I am getting the same problem too.But i didnt wait for 3 minutes till it load rest of the gnome but why does this problem come, it was not there in warty right.
I posted the same question in linuxquestions.org. I got no replies. If I find smthing useful I will definitely post it here.Cant we ask this quetion to some experienced user.I am new to this site plz help me.
thanks,
pranith.

---

### Post by cdhotfire on 2005-03-21
maybe you made to many things to start up.  Maybe you logged out and saved you session with a ton of programs open.  You can try upgrading everything
```
$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt-get dist-upgrade
```

If you cant even open command, i dont know how to help u.  :???: .

---

### Post by jeffus on 2005-03-21
OK, fixed it for a second time!  The problem w/ mine was that I didn't deactivate the wireless before logging out.   Therefore, for whatever reason, it took that initial 3 minutes to do something w/ that.  

Cdhotfire is correct in that something is may be loading that is hanging.  What do you have running at startup.  Make sure to load "gnome" when you click on session at the intro screen.

Let us know.

Jeff.

---

### Post by cdhotfire on 2005-03-21
glad i could help you. For the other guy, like he said he could not even open terminal, so i cant see anyway to do anything.  Maybe try Ubuntu Live CD and go from there.

---

### Post by jallen7usa on 2005-03-22
[QUOTE=cdhotfire]maybe you made to many things to start up.  Maybe you logged out and saved you session with a ton of programs open.  You can try upgrading everything
```
$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt-get dist-upgrade
```

If you cant even open command, i dont know how to help u.  :???: .[/QUOTE]
Sorry for the delayed response.  I'm in the process of moving and have had sporadic access to the internet.  My system doesn't lock up immediatly.  I have about a minute or two of Hoary happiness before it freezes.  If I CTRL+ALT+F1 right away I can stop gnome and do all i need from the command line.  How would I find out what is running at start up to further trouble-shoot this?

I did try an apt update, upgrade, dist-upgrade using this method but there was nothing to upgrade.

Thanks for all your help.

---

### Post by cdhotfire on 2005-03-22
from the command, open nautilus
```
$ nautilus
```
then open up gnome-panel
```
$ gnome-panel
```
and add a logout icon to the panel, then log out and choose save this session. Try that out.  If this doesnt work is not a program hanging, must be something else.

---

### Post by jallen7usa on 2005-03-23
[QUOTE=cdhotfire]from the command, open nautilus
```
$ nautilus
```
then open up gnome-panel
```
$ gnome-panel
```
and add a logout icon to the panel, then log out and choose save this session. Try that out.  If this doesnt work is not a program hanging, must be something else.[/QUOTE]
I think I love you!  :oops:  I'd tried the logging in to gnome session and saving session seperatly with no luck.  But last night I did both in succession and no freeze!  Thanks so much **cdhotfire**.

---

### Post by cdhotfire on 2005-03-23
[QUOTE=jallen7usa]I think I love you!  :oops: I'd tried the logging in to gnome session and saving session seperatly with no luck. But last night I did both in succession and no freeze! Thanks so much **cdhotfire**.[/QUOTE]

no problem dude.;)

---

### Post by ggeller on 2005-09-20
I may have the same problem.  It only happens with one of the four machinces I have running ubuntu.  They are all different hardware configurations.  I've seen it with both 5.0.4 and 5.10.0 either with the initial install or after doing apt-get upgrade.

Notes:

The freeze is always in X.  It happens anywhere from a few seconds to several hours after the X session is started.

The freeze is very hard.  The machine does not respond to ping from another box.  The mouse and keyboard are completely useless.

The machine works OK with a debian install, and worked with Fedora Core 3 when I had that installed.

The machine recently passed memtest86, and passed mke2fs -j -c -c on the partition I installed Ubuntu.

After it froze, I booted with Knoppix and checked /var/log/messages, but didn't find anything.

I'd appreciate any suggestions for diagnosing this.  I want to use the machine as my primary server.

The next day:  I followed the instructions at [https://wiki.ubuntu.com/BreezyUpgradeNotes](https://wiki.ubuntu.com/BreezyUpgradeNotes)
and the problem went away.  Maybe it was upgrading to linux-image-2.6.12-8-386 that did the trick.  I don't know.

The next-next day: (9-23-05)  It froze again after running just fine overnight.  I'm going to run Debian from another partition and see how that goes.

Thanks,
George

---

