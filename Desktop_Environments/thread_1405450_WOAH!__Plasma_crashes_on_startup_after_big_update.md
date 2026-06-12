---
title: "WOAH!  Plasma crashes on startup after big update"
date: 2010-02-12
forum: Desktop Environments
---

### Post by clk99 on 2010-02-12
Something like this has not happened to me in a while.  I just updates about 70 files.  After the update--before restarting the computer--I started getting errors for weird things.  One example is that I couldn't send anything to the trashcan, it said that it couldn't find the trash app or something.  So I restarted to see if that would help.  Nope.  Now plasma won't start.  I just get a black screen and an error popup.  I tried starting in manually from the konsole.  I get this:

```
plasma-desktop(2351): Communication problem with  "plasma-desktop" , it probably crashed.
Error message was:  "org.freedesktop.DBus.Error.ServiceUnknown" : " "The name org.kde.plasma-desktop was not provided by any .service files" "
```

Any ideas?

---

### Post by captaincrook on 2010-02-12
Check and see if plasma-desktop is installed.

EDIT: I am assuming this is similar to my problem (no plasma at boot due to updates borking).

---

### Post by clk99 on 2010-02-12
It is definitely installed: it tries to start and crashes, giving me an error dialog. 

I actually just managed to fix my problem, albeit not the way I would have preferred.  I just reinstalled plasma-desktop.  Now I'll have to reconfigure it, but at least it starts.

---

### Post by lykwydchykyn on 2010-02-12
I had this problem due to third-party plasma widgets I'd installed in 4.3.  When I upgraded to 4.4, the plugins caused things to crash.

If you have binary plugins (not plugin scripts) you've compiled yourself or installed from another source (like kde-look.org), you'll need to recompile them or just not use them (until you can get a 4.4 -compatible version).

---

### Post by Christopher Fritz on 2010-02-13
I had this same problem, and was able to get around it thanks to lykwydchykyn's information.  In ~/.kde/share/config/, I located and moved (to another location) all files which started with "plasma" or "plasmoid".  I moved them all at the same time, rather than going through them one-by-one to see which was the problem.  With all of them moved, I was able to run plasma-desktop without problems.

---

### Post by Dipper on 2010-02-14
Where did you move them to?

---

### Post by kio_http on 2010-02-14
The configuration of previous versions of software components of KDE may not be compatible with the new version.

try deleting all config files of KDE

In terminal cd to your home folder
then
```
rm -rf .kde
```

alternatively delete in a file browser in dolphin or other.

Note: to be able to view the hidden .kde folder in dolphin press ALT + period (.)

By deleting configuration files, you will lose all KDE settings like bookmarks themes etc. KDE will go to default setting. Documents, Music etc will stay.

If this procedure doesn't work upgrade the whole of KDE to version 4.4.

---

### Post by lykwydchykyn on 2010-02-14
> **Dipper said:**
> Where did you move them to?
It doesn't matter where you move them, the idea is that you're renaming the folder so that KDE creates a new default.  You can move them to .kde-old or whatever makes sense to you.

> **kio_http said:**
> 
By deleting configuration files, you will lose all KDE settings like bookmarks themes etc. KDE will go to default setting. Documents, Music etc will stay.

Which is why I always recommend MOVING (renaming) the folder, not DELETING it.  Especially since (at least in the past) kmail stores email under .kde (that might have changed, I hope).

Never delete when you can just rename.  Then delete later when you're sure the new settings are ok.

---

### Post by Zorael on 2010-02-15
Further, only the files beginning with **plasma** in **~/.kde/share/config** contain plasma's configuration. So rename those, log out and back in. Alternatively, restart plasma by entering the following two commands in a run box (Alt+F2) or a terminal.
```
kquitapp plasma-desktop

plasma-desktop
```
You would replace **plasma-desktop** with **plasma-netbook** if you were running the netbook interface.

All in one terminal command, for easy copy-pastage;
```
mkdir ~/plasmabackup && mv ~/.kde/share/config/plasma* ~/plasmabackup && kquitapp plasma-desktop && sleep 2 && plasma-desktop &>/dev/null
```

---

### Post by Gramler on 2010-04-01
Tried all the above. No Luck. In the end I went for the lobotomy... 

sudo apt-get remove kubuntu*
sudo apt-get install kubuntu-desktop

That fixed it.

---

