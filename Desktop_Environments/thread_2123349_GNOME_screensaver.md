---
title: "GNOME screensaver"
date: 2013-03-07
forum: Desktop Environments
---

### Post by mayagrafix on 2013-03-07
How can I stop the Xscreen saver from asking for password in Lubuntu? 

When I put the laptop in suspend mode, the GNOME Xsreensaver kicks in and wants my password to open up. If I don't set to suspend mode, the screen turns off via power saving mode after a few minutes and turns back on with no password required. This is the way I want it.-:KS-

---

### Post by Rex Bouwense on 2013-03-07
Go to Menu->Preferences->Screensaver.  Then navigate to Lock Screen After and make sure that there is no check mark there.  Back out and you should be good to go (no password required).  If you suspend the computer it will still ask you for your password.

---

### Post by mayagrafix on 2013-03-11
[IMG]http://i16.photobucket.com/albums/b1/mayagrafix/lockoffpassword_zps93c438d1.png[/IMG]

This is from Ubuntu... is there an equal feature in Lubuntu? 

So far I have gotten around this by rebooting the laptop whenever it will be left on for extended periods of time. On clean start, the screen turns off after 10 minutes and no password is required to resume operations.

Thanks in advance -:KS-

---

### Post by Rex Bouwense on 2013-03-11
What you want to do can be accomplished by going to Menu->Preferences->Power Manager.  You can change your preferences there.

---

### Post by mayagrafix on 2013-03-14
I brought up the System Monitor and killed Xscreensaver process. This works fine for me. Now, the PC will turn off its screen after 10 minutes, awake without asking for a password, and maintain these attributes after being set to Suspend mode.  

So I wont have to kill the Xscreensaver process every time I reboot, I would like to **UN-install** it. Can someone provide me with the appropriate command line necessary to remove this program from my system? or how do I keep it from loading? The control panel does not offer this an option.

Thanks in advance for any and all help -:KS-

---

### Post by mayagrafix on 2013-03-16
I did apt-get remove xscreensaver and this worked for me. Somehow in the begining I would get a message that GNOME screen saver was still in operation and that mislead me in the beginning, but it was Xscreensaver the whole time causing the ruckus. Thanks to all for your input.

---

