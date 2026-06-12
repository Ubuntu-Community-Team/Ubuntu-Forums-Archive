---
title: "gdesklets problem"
date: 2005-07-07
forum: Desktop Environments
---

### Post by ReiKn on 2005-07-07
I was using two desklets: LTCandy Weather Desklet and Rhythmlet down left control. They were fully working until I during some configuration rebooted gnome-panel by killall gnome-panel. After the reboot neither of the desklets work anymore. Weather desklet is not showing anything and rhythmlet misses some buttons. Also the configurate desklet from right button menu has lost its effect. Completely removing and reinstalling gdesklets and gdesklets-data didn't fix it. All other desklets run just fine. I'm out of ideas...

So it looks like this:
[Screenshot](http://www.students.tut.fi/~apajalah/Kuvakaappaus.png)

---

### Post by negatory on 2005-07-07
Have you removed the desklet and tried to restart it?
If everything fails remove the .gdesklets directory in your home directory and start again...that worked for some strange bugs that I had using gdesklets.
And by the way I first installed gdesklets-data via apt-get but the desklets that came were too buggy so I've installed only gdesklets and downloaded the desklets that I wanted,that took care of some strange things happening in my gdesklets.
Hope that helps
Pedro Carrico

---

### Post by ReiKn on 2005-07-07
Restarting the desklet doesn't help.  Neither does removing .gdesklets directory and "removing with configuration" gdesklets and gdesklets-data and then reinstalling them. The almost same rhythmlet-desklet whitch goes to the bottom right corner works well. I tried also downloading the corresponding desklet from the web and using it instead of the gdesklets-data one -did't help.

---

### Post by negatory on 2005-07-08
I have no idea... removing the .gdesklets directory shoud erase every gdesklet configuration.Maybe some weird bug in python I don't know....
Try to download the latest gdesklets from their site or something....maybe that should do the trick.
Sorry I couldn't help  :-| 
Pedro Carriço

---

### Post by Morimando on 2005-07-08
I also don't have an idea what went wrong, but since it uses python, maybe a reinstall of the python package would help? Maybe it got corrupted because it was working when gnome-panel got killed and now has problems? Apart from that i have no clue :(

---

