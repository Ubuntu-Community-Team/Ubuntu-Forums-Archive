---
title: "Wireless passphrase not saved in keyring-manager"
date: 2007-12-25
forum: Desktop Environments
---

### Post by MystaMax on 2007-12-25
Hello, I'm running gutsy, and I am being asked to enter my passphrase to my wireless network every time I log onto my computer.

This started after my wifi router lost its settings, and it had to be reconfigured. I set the router up w/ the same exact settings (same SSID and passphrases). Now, every time I log onto my computer its asking for the passphrase.

I checked the keyring-manager and see the keyring entry for the wireless network in question. The keyring-manager states it has access (rwx) to nm-applet. I'm not sure whats going on.

I thought about [deleting one of the keyring files]("http://ubuntu-tutorials.com/2007/07/06/clearing-or-resetting-the-gnome-keyring/") from ~/.gnome2/keyrings, but I'm not sure which one, or if its the appropiate solution. Here are the files in the directory:[LIST]
[*]default.keyring
[*]login.keyring[/LIST]Anyone know why this is happening? How do I fix it?

---

### Post by barrack on 2007-12-26
This helped me out, but I am on Feisty, so I don't know how helpful it will be.

[http://ubuntuforums.org/showthread.php?t=187874](http://ubuntuforums.org/showthread.php?t=187874)

---

### Post by MystaMax on 2007-12-29
Just an update,

I went into ~/.gnome2/keyrings/ folder and renamed default.keyring to default.keyring.OLD. So, the next time nm-applet asked to save to the keyring, fixing my problem.

---

