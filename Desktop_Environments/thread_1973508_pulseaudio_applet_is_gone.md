---
title: "pulseaudio applet is gone"
date: 2012-05-04
forum: Desktop Environments
---

### Post by Park Bom on 2012-05-04
I was having trouble playing sound on Xubuntu 12.04 (it worked for weeks then suddenly stopped), so I deleted pulseaudio and all of its related files. A reinstallation seems to have fixed the sound issue, but how can I re-add the applet? Thankfully I have a screenshot to help explain it:

What I'd like to have it look like
[IMG]http://i.imgur.com/kyoNK.png[/IMG]



What it currently looks like
[IMG]http://i.imgur.com/AmXYg.png[/IMG]


I'm new to Linux, so an explanation in layman's terms is preferred :]

Any help would be greatly appreciated!

---

### Post by Toz on 2012-05-04
Do you have indicator-sound installed? Look for it in the software centre or from a terminal window:
```
apt-cache policy indicator-sound
```
...to see if its installed, and if not:

```
sudo apt-get install indicator-sound
```

---

### Post by RJARRRPCGP on 2012-05-04
> **Park Bom said:**
>  I deleted pulseaudio and all of its related files. A reinstallation seems to have fixed the sound issue, but how can I re-add the applet? 

It's possible that even when the volume control isn't part of Pulse Audio itself, APT ended up deleting it. 

The APT package manager may claim a program is related to another program and thus just goes ahead and deletes it! 

You must use **apt-get** with caution and read the list of stuff it plans to remove, before hitting **y**!

I dunno how to re-add it. Sorry.

---

### Post by Park Bom on 2012-05-04
> **Toz said:**
> Do you have indicator-sound installed? Look for it in the software centre or from a terminal window:
```
apt-cache policy indicator-sound
```
...to see if its installed, and if not:

```
sudo apt-get install indicator-sound
```

It was not installed, so I downloaded it. However, I do not see it as an option when I try to add a new applet to a panel. I also tried removing then re-adding the indicator plugin, but to no avail.

---

### Post by Toz on 2012-05-04
Looks like its tied into dbus. Try logging out and back in again. Maybe even rebooting.

---

### Post by Toz on 2012-05-04
And if still no luck, have a look at the log file ~/.xsession-errors for some clues.

---

### Post by Park Bom on 2012-05-05
> **Toz said:**
> Looks like its tied into dbus. Try logging out and back in again. Maybe even rebooting.
Rebooting did not add the option for the applet, but I installed xfce4-mixer and it works just as well, with more features :]
Thank you for the help everyone!

---

