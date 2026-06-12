---
title: "Can't get my laptop to stop suspending when I close the lid."
date: 2014-10-13
forum: Desktop Environments
---

### Post by stretch4 on 2014-10-13
Computer: Lenovo G570 Laptop
Distro: Xubuntu 14.04 LTS

I'm having problems with closing the lid on my laptop.

I don't want anything to happen when I close the lid. (Other than shutting off the screen obviously.)

So the first thing I did was open Power Manager and set the "When laptop lid is closed:" option to "Nothing" for both "On AC" and "On Battery."

I close the lid and it suspends. When I open the lid, it asks for my username and password. After I enter them, the system resumes, but the screen goes black.

So I opened Light Locker Settings and set "Lock on suspend" to OFF.

It still suspends when closing the lid. Upon resuming, it asks for my login info, and after I enter them, black screen. No change.

So the next thing I did was:
```
$ sudo aptitude purge light-locker light-locker-settings
```

Now it doesn't ask me to log in again after closing the lid, so I don't get a black screen after opening the lid back up. However it's still suspending when I close the lid.

The next thing I tried was editing /etc/systemd/logind.conf and changing 
```
#HandleLidSwitch=suspend
```
to
```
HandleLidSwitch=ignore
```

No change. It still suspends when I close the lid.  I'm all out of ideas, and searching hasn't turned up anything I haven't already tried. How can I stop it from suspending when I close the lid?

---

### Post by stretch4 on 2014-10-13
It's working now. Apparently I just needed to reboot... duh.
[IMG]https://dl.dropboxusercontent.com/u/94399016/duh-award.jpg[/IMG]

---

