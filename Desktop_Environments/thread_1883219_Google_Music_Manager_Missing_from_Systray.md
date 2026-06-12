---
title: "Google Music Manager Missing from Systray"
date: 2011-11-18
forum: Desktop Environments
---

### Post by flloyd on 2011-11-18
I am using Unity (3D?) and have systray-whitelist set to ['all'] yet when I launch Google Music Manager I can use the login screen for the application but as soon as I log in, it disappears. I can see that it is still running form the System Monitor but I cannot control it as it is invisible in both the launcher and systray. What can I do in order to operate this?

Thanks so much for any input.

---

### Post by gordintoronto on 2011-11-18
Does it show up if you click the speaker icon?

---

### Post by flloyd on 2011-11-18
It doesn't, nor should it though since it's the music uploader and not a player.

I forgot to mention that it used to work before updating from Ubuntu 11.04 to 11.10 and Google Music Manager 1.18 to 1.22.

---

### Post by temporos on 2011-12-19
I don't think it's an upgrade issue.  I installed Google Music Manager on my system running 10.04 Netbook Edition.  It worked after installation, uploading all my music.  The next time I restarted, however, the panel icon disappeared, and the application is not in the UNE app launcher.  Now, I can't start the app anymore, and it's no longer uploading or monitoring my music directory.

---

### Post by temporos on 2011-12-19
Not sure if this will solve the OP's problem, but I've created a work-around for my issue.  I created a launcher item in the *Main Menu* control panel using the path
```
/opt/google/musicmanager/google-musicmanager
```
Then, in the *Startup Applications* control panel, I added an entry with the same path.  The application now launches upon log-in, and it stays in the panel, monitoring my music folders.

---

