---
title: "Remove Trinity Deskstop?"
date: 2014-03-22
forum: Desktop Environments
---

### Post by ravensmac on 2014-03-22
Running 12.04 LTS.  Installation of Trinity appeared to go as expected.  However getting crashes.  Attempted to shutdown in normal fashion, after 3 minutes of waiting had to hit the reset button.

How can one remove?

Thanks

---

### Post by Frogs Hair on 2014-03-22
Hello and Welcome

Can you describe how Trinity was installed ?  I see no such package in the ubuntu repository , but I am using 13.10 and it might have been available for 12.04.

---

### Post by ravensmac on 2014-03-22
The Trinity Web site has detailed instructions; [ Click to access]("http://www.trinitydesktop.org/wiki/bin/view/Documentation/UbuntuBinaryInstallation")   Detailed.  I used the Precise

---

### Post by Frogs Hair on 2014-03-22
I was just looking there . :o    Try the following .

```
sudo apt-get remove kubuntu-default-settings-trinity kubuntu-desktop-trinity
```

---

### Post by ravensmac on 2014-03-22
The above worked, the TDE no longer exists.  However even after shutting down, reboot, I still get the TDE log in, have to do log in, then select my preferred deskstop, Gnome, then I am taken to that.

---

### Post by Frogs Hair on 2014-03-22
The following will remove un-needed packages which would marked as autoremovable in synaptic  . ```
sudo apt-get autoremove
```

---

### Post by ravensmac on 2014-03-22
That cleaned up a lot of pkgs, however still had to go through TDE when shutting down and starting up.

---

### Post by Frogs Hair on 2014-03-22
I am not certain if Trinity uses KDM which is the KDE login screen and one way to find out is to install synaptic if you don't have it and look for and remove the package/s. I have tried the KDE desktop in the past and as I remember it was difficult to remove everything without some manual cleanup using the synaptic package manager.

---

### Post by ravensmac on 2014-03-22
Removed Trinty KDM via Synaptic, which I had to access via terminal, which is a new problem, did a removal, clean, reinstall twice.
Shut down stalled so had to hit reset button.
On restart got msg that Trinty KDM failed, then was taken directly to Trinty Desktop, no log in, logged out, was able to log onto Unbuntu.
This is like a snowball!

---

### Post by ravensmac on 2014-03-22
Removed Trinty KDM via Synaptic, which I had to access via terminal, which is a new problem, did a removal, clean, reinstall twice.
Shut down stalled so had to hit reset button.
On restart got msg that Trinty KDM failed, then was taken directly to Trinty Desktop, no log in, logged out, was able to log onto Unbuntu.
This is like a snowball!

Went back in got Synaptic working, removed all the installed Trinity packages
Logged out, then shut down normal fashion
Started up again, long crash list related to Trinty

---

### Post by Frogs Hair on 2014-03-22
I am confused as where you are at, but make sure all the Ubuntu desktop packages are installed . There may have been packages affected when removing Trinity. I don't why KDM is in use and not Light GDM.
 ```
sudo apt-get install --reinstall ubuntu-desktop
```

---

### Post by ravensmac on 2014-03-22
1.  Ran Ubuntu Tweak to clean up
2.  Reinstall ubuntu desktop as you rec
3.  Had to reinstall gdm as was beng logged directly into Ubuntu

Looks like I am back to pre Trinty, thanks for all the help, learned a lot!

---

### Post by Frogs Hair on 2014-03-22
You're Welcome 

KDE was the most difficult to remove of all DEs Ive tried.

---

