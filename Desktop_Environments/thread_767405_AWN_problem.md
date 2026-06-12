---
title: "AWN problem"
date: 2008-04-25
forum: Desktop Environments
---

### Post by dondad on 2008-04-25
Running AWN in Hardy with all updates. I can't seem to get it to keep the Firefox Icon on the tray. I have tried dragging one from the desktop, and also adding a launcher from the preferences menu. I add it (from either method), do a refresh and try it out. It works fine. I then close awn and restart it through the run menu and it is still there. If, however, I reboot the system, no more Firefox, even though I see it in the preferences menu. The other icons seem to stay OK.

Any idea what to check?

---

### Post by SaddaGocaraRupa on 2008-04-25
I had the same problem in Gutsy. Just upgraded to Hardy and haven't been able to install it yet. Any pointers?

---

### Post by dondad on 2008-04-25
> **SaddaGocaraRupa said:**
> I had the same problem in Gutsy. Just upgraded to Hardy and haven't been able to install it yet. Any pointers? Try here for install. Still having the problem.

[https://launchpad.net/ubuntu/hardy/+source/avant-window-navigator]("https://launchpad.net/ubuntu/hardy/+source/avant-window-navigator")

---

### Post by lemoutonvert on 2008-04-26
I installed awn 0.3.1 from the repo:
```
deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
```

I can add launchers but I've got some other troubles... 
You can try...

---

### Post by dondad on 2008-04-29
bump

---

### Post by andrewsomething on 2008-04-30
Original comment deleted by poster. Misunderstood the question..

---

### Post by bjornie on 2008-07-25
I'm having the same problems over here. I can add applets but not launchers. If I drag launchers from the desktop to the awn bar they will not stick when I reboot my laptop, and creating launchers from awn manager doesn't work either - nothing gets added to the bar when I add them in the manager.

Anyone with a clue?

---

### Post by moonbeam on 2008-07-25
> **bjornie said:**
> I'm having the same problems over here. I can add applets but not launchers. If I drag launchers from the desktop to the awn bar they will not stick when I reboot my laptop, and creating launchers from awn manager doesn't work either - nothing gets added to the bar when I add them in the manager.

Anyone with a clue?

start awn-manager.
exit awn.
Remove the Launcher/Taskmanager applet if it is present
Add the Launcher/Taskmanager applet.
start awn.

---

### Post by bjornie on 2008-07-26
That didn't help, unfortunately. Running Hardy if that makes any difference. Thank you for your reply, though!

---

### Post by moonbeam on 2008-07-26
> **bjornie said:**
> That didn't help, unfortunately. Running Hardy if that makes any difference. Thank you for your reply, though!

My suggestion:

1) If you're using the "official" Ubuntu packages you might want to try installing either the from the awn-testing ppa ( [http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive](http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive) ) or from reacocard's ppa ([http://ubuntuforums.org/showthread.php?t=762363&highlight=awn](http://ubuntuforums.org/showthread.php?t=762363&highlight=awn) )

2) If you're already using one of those ppa's then I'd suggest:  a) if using awn-testing open a bug [https://bugs.launchpad.net/awn](https://bugs.launchpad.net/awn)   b) if using reacocard's post on the support thread [http://ubuntuforums.org/showthread.php?t=762363&highlight=awn](http://ubuntuforums.org/showthread.php?t=762363&highlight=awn)

And double check that the Launcer/Taskmanager applet is among the installed applets list in awn-manager :-)

---

### Post by diego898 on 2008-07-26
How do I add a launcher? where is the windows equivalent of a .exe for firefox? Where is the windows equivalent of "prgoram" files?

---

### Post by MedellinManDem on 2008-07-27
Dragging launchers to the dock only works while you're still booted in. As soon as you reboot (your pc or the dock itself) the go away. To keep a launcher stuck to the dock you must go into the AWN manager and add the launcher that way. It's pretty simple. The command for firefox should be 

```
firefox %u
```

But it might be different on different distros, not sure.

---

### Post by diego898 on 2008-07-27
but what are the commands for the rest of programs? Like pidgin?

---

### Post by ash05 on 2008-07-28
just upgraded it

[Didihat]("http://www.didihat.com")

---

