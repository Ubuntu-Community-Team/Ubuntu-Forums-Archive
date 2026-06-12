---
title: "NotifyOSD in Gnome Flashback (Metacity)"
date: 2014-05-17
forum: Desktop Environments
---

### Post by chazzyfresh33 on 2014-05-17
I'm running GNOME Flashback as my DE and I've noticed that while the desktop notifications will function just fine in Compliz mode, they will not during Metacity. I would prefer to run Metacity on my machine. Is there anyway to get them running or are they specific to Compliz?

---

### Post by Frogs Hair on 2014-05-17
I don't see compiz as dependency of notify osd and you can run a notify osd test in the terminal with the following command. ```
notify-send test text
```

---

### Post by chazzyfresh33 on 2014-05-17
I tried that with the Metacity environment and could not get a successful test. I also got no notifications for wireless connection, syncing of cloud services, or songs playing. All of these work in Compiz

---

### Post by Frogs Hair on 2014-05-17
Flashback uses the notification daemon and not osd and I'm installing now . I will let you know if I get notifications in metacity.

Edit: I'm seeing song notifications from the Pithos Pandora client but that's all so far. There was no wireless notification upon login .

---

### Post by pfeiffep on 2014-05-17
Ubuntu 14.04 ; Gnome FlashBack Metacity ; "[COLOR=#000000][FONT=Ubuntu Mono]notify-send test text" worked perfectly[/FONT][/COLOR]

---

### Post by Frogs Hair on 2014-05-17
> **pfeiffep said:**
> Ubuntu 14.04 ; Gnome FlashBack Metacity ; "[COLOR=#000000][FONT=Ubuntu Mono]notify-send test text" worked perfectly[/FONT][/COLOR]

Same here, run the following to see if the daemon is installed . ```
sudo apt-get install notification-daemon
```

---

### Post by chazzyfresh33 on 2014-05-17
Again, no joy on the notify-send test text or any other notifications that should have been displayed when logging in.

---

### Post by Frogs Hair on 2014-05-17
Try reinstalling the following. ```
sudo apt-get install --reinstall libnotify-bin 
```

---

### Post by chazzyfresh33 on 2014-05-17
Well that's interesting. Seemed to get the Rhythmbox song notifications working again, but not for Google Drive sync, wireless network, or Thunderbird. Perhaps even more interesting, still no successful [FONT=Ubuntu Mono, monospace][COLOR=#000000]notify-send test text[/COLOR][/FONT]

---

### Post by Frogs Hair on 2014-05-17
My wireless connection notice appears in the login screen before I even choose a session . I'm not seeing any bug reports for the problem although for 13.10 there was a conflict with notify osd reported confirmed. Still looking :confused:

---

### Post by kansasnoob on 2014-05-18
Appears to be working OK here:

[ATTACH=CONFIG]253259[/ATTACH]

---

### Post by chazzyfresh33 on 2014-05-18
I'm pretty stumped then, this installation of 14.04 is 2 days old, I'm not sure what could be causing this.

---

### Post by Frogs Hair on 2014-05-18
Try the following and watch the terminal. If all packages are configured there will be little or no activity. ```
sudo dpkg --configure -a 
```

---

### Post by chazzyfresh33 on 2014-05-18
I got the following 
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory

---

### Post by Frogs Hair on 2014-05-18
> **chazzyfresh33 said:**
> I got the following 
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory

I have not seen this before and not had a memory leak ever that I am aware of , so this problem will require a new thread . I found the following bug but it's not the same. 
[https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/1274680](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/1274680)

---

### Post by chazzyfresh33 on 2014-05-18
Fixed the memory leak with sudo apt-get remove libpam-smbpassI now get no activity in terminal when running sudo dpkg --configure -a

---

### Post by Frogs Hair on 2014-05-18
Run the update manager if you haven't  and try the notify test again.

---

### Post by chazzyfresh33 on 2014-05-18
Still no success on the test

---

### Post by Frogs Hair on 2014-05-19
I have no further suggestions other than reinstalling flashback . The bug linked was petty early in development and that makes  me curious .

---

### Post by chazzyfresh33 on 2014-05-19
The unfortunate thing is that I've already uninstalled and re-installed (inadvertently, but still) flashback. didn't solve it.

---

