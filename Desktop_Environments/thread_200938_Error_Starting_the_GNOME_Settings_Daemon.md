---
title: "Error Starting the GNOME Settings Daemon"
date: 2006-06-21
forum: Desktop Environments
---

### Post by cwmccabe on 2006-06-21
I've seen a number of posts about this problem, but no solutions that help me.  I just installed 6.06 and I get the following error message every time I start up:

```
There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The Settings Daemon restarted too many times.

The last error message was:

System exception: IDL:Bonobo/GeneralError:1.0 : Child process did not give an error message, unknown failure occurred

GNOME will still try to restart the Settings Daemon next time you log in.
```

After installing, I ran Synaptic to fetch/install all the updates.  Everything else seems to be working fine except for the GNOME Settings Daemon.

I don't even know where to begin to ask for help on this.  Can someone tell me what info I can supply so someone can help me figure out how to fix this?  I've searched the forums, googled the web, and have found lots of other people with this problem, but no info that fixes mine.

NOTE: One thing I've tried is erasing .gnome* and .gconf* from my home directory.  No luck.

Thanks!

---

### Post by bmgz on 2006-07-04
Have you managed to sort this out? I have one machine that i upgrade from hoary->breezy->dapper and it has this same problem. All my other upgraded systems are fine?

---

### Post by cwmccabe on 2006-07-04
No luck yet, sorry!

---

### Post by eternalsword on 2006-07-15
I had that error.  I updated all of the gnome components to the Edgy repoistory ones, and the error went away.

---

### Post by FRuMMaGe on 2007-11-30
Same problem. HELP!!

---

### Post by coolkid5 on 2007-12-04
I know this thread is old but i see FRuMMaGe just replied.  I also got this error in gutsy.  Does anyone know how to fix it?

---

### Post by dast on 2007-12-06
I just upgraded from 7.04 to 7.10 and I can confirm this bug happened to me

$uname -a
Linux wolf 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

See the following bugs.

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/146946](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/146946)
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/138277](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/138277)

Unlike some people, I found that i could start the daemon from the command line.  So...  I "fixed" the problem by going under System > Preferences > Sessions (in the main Gnome menu) and adding a startup program entry for the daemon.  That does not work for everyone, apparently.  Others have hacked up init.d scripts (i believe) to start this daemon, which I opted not to try.

See also 

[http://ubuntuforums.org/showthread.php?t=587410&highlight=gnome+settings+daemon](http://ubuntuforums.org/showthread.php?t=587410&highlight=gnome+settings+daemon)

---

### Post by Yellowbelly on 2007-12-06
I've gotten that once before on my fresh install of 7.10. But the weird thing is though, probably half the time or more, something doesn't work right whenever I start up ubuntu. This time it didn't mount my windows partition like it usually does. Usually the sound doesn't want to work so I have to restart and then it starts working. Weird. I'm thinking I burned Ubuntu too fast on the CD so I probably need to burn another copy of it really slowly. I had a problem installing it the first time too.

---

### Post by dast on 2007-12-07
I just want to add this to my notes above: I never saw this problem with 7.04, or any previous version.  Not sure if that means anything.  I haven't tried a fresh install of 7.10, only a dist-upgrade.

---

### Post by luke16 on 2007-12-07
I am seeing this as well on about every other start up, even though everything still seems to work after that. It says that the last error reported was that it "did not receive a reply" for it not being able to start gnome settings daemon instead of original posters error.

---

### Post by FRuMMaGe on 2007-12-07
Well I found the problem. (for me at least)

Turns out my gnome security settings file had become corrupt. I looked at it and aparently it was over 500GB. This was obviously wrong because I am only on a 160GB hard-drive.

I reinstalled the gnome-security packages and now everything is fine.

---

### Post by luke16 on 2007-12-11
The thing is, I don't get the error message every time I start up. Maybe only every other or third time. And I don't even know what this thing is supposed to do. Everything seems to work just fine even when I do get the error message.

---

### Post by tinman6700 on 2007-12-11
I am assuming that Daemon has to do, (at least in my particular case,) with screen res, and visual affects. Everything seems to work fine, except for the desktop cube, until I try to adjust above 800x600. Above that, it totally crashes Gnome, and restarting does nothing. I know my card is good, and as old as this laptop is, I find it hard to believe that it's not supporten in Linux.

---

### Post by snappy46 on 2007-12-12
Hi,

I have the same problem as well with a fresh install of ubuntu 7.10.  I am up to date with the upgrade and I have no idea why I am getting this error once in a while.  I can log 3-4 times without any problems and then on the fifth time I get this error message.

Normally if I log out and log back in again everything is fine....weird.

---

### Post by exactopposite on 2007-12-13
the same thing happens sometimes when i login. usually if i logout and back in it goes away.  if not it'll go away after a reboot.

---

### Post by luke16 on 2007-12-19
I think it might be caused by compiz. Anyone have it happen to them with visual effects turned completely off?

---

### Post by snappy46 on 2007-12-21
I have compiz turn off no visual effect and still get that error.

---

