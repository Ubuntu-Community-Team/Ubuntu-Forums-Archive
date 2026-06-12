---
title: "Constant Beep on Startup"
date: 2009-02-19
forum: General Help
---

### Post by briml3y on 2009-02-19
Not long ago I installed startup manager so that I could change the uSpalsh theme on startup. Not to long afterwards my computer started beeping erratically on startup. Occasionally booting will be normal but for the most part I have force shutdown then start into recovery then just resume startup to get into ubuntu.  
I've already restored to splash screen to the standard start-up screen
Ive Read this thread
[http://ubuntuforums.org/showthread.php?t=1046025&highlight=cant+boot+beep](http://ubuntuforums.org/showthread.php?t=1046025&highlight=cant+boot+beep)
Which suggests taking splash out of the load up process but I like my Splash screen and would like to keep it. Is there any other way to fix the problem?

---

### Post by Yellow Pasque on 2009-02-19
> I like my Splash screen and would like to keep it.
Understood, but you should realize that you may have a more serious issue that you have to resolve before worrying about aesthetic features like splash screens. Unless your system starts and shuts down reliably without the splash screen, then we shouldn't jump to the conclusion that the splash screen is to blame.

For now, I recommend removing the 'splash' and 'quiet' keywords from the regular kernel boot line with:
```
gksudo gedit /boot/grub/menu.lst
```
If your system boots/halts normally (without using recovery mode) for a period of time, then you can go forward troubleshooting the splash issue. If not, you'll be able to see exactly where the process hangs.

---

### Post by briml3y on 2009-02-21
I took out splash from the menu.lst and everything boots up normally, what should I do in accordance with the splash screen

---

### Post by Yellow Pasque on 2009-02-21
> what should I do in accordance with the splash screen
Keep up an eye on this bug report: [https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/279187](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/279187)
In that bug report someone suggested a timing issue, can you post the output of:
```
ls /etc/rc2.d/
```

---

### Post by briml3y on 2009-02-23
Ive posted the output of  ls /etc/rc2.d below
```
$
README                       S20apport              S25pulseaudio
S01policykit                 S20clamav-freshclam    S28NetworkManager
S05vbesave                   S20cups                S30gdm
S10acpid                     S20dkms_autoinstaller  S30system-tools-backends
S10powernowd.early           S20fancontrol          S89anacron
S10sysklogd                  S20hotkey-setup        S89atd
S10xserver-xorg-input-wacom  S20nvidia-kernel       S89cron
S11klogd                     S20powernowd           S91apache2
S12dbus                      S20rsync               S98usplash
S14avahi-daemon              S20ushare              S99acpi-support
S17mysql-ndb-mgm             S20xinetd              S99laptop-mode
S18mysql-ndb                 S24dhcdbd              S99rc.local
S19mysql                     S24hal                 S99rmnologin
S20apmd                      S25bluetooth           S99stop-readahead

```

---

### Post by Yellow Pasque on 2009-02-23
I don't see anything really abnormal/alarming, but I won't claim to be a total expert.

If you want to troubleshoot the bug, you'll need to put the splash keyword back from where you removed it (in /boot/grub/menu.lst). Then you'll have to boot normally, and look at the boot messages with:
```
dmesg
```
dmesg outputs a lot of information, so if you want to share the results, save the output to a file, e.g. to put it on your desktop:
```
dmesg > ~/Desktop/dmesg.txt
```
Then you can copy the text into a pastebin and post the link here (or on that Launchpad bug): [http://ubuntu.pastebin.com/](http://ubuntu.pastebin.com/)

If you don't want to troubleshoot the bug, you can always run without the splash screen (even if it's not pretty). If you usually upgrade to the latest Ubuntu release, it may be fixed when you upgrade to 9.04/Jaunty. Also, usplash is being completely replaced with another boot screen (Fedora's "Plymouth") in Ubuntu 9.10: [http://www.phoronix.com/scan.php?page=news_item&px=NjkzNQ](http://www.phoronix.com/scan.php?page=news_item&px=NjkzNQ)

---

### Post by Chemical Imbalance on 2009-03-13
I have the same problem.

(Nvidia 8300) with latest Jaunty Nvidia drivers

I worked around the bug by uninstalling usplash

No beeping now

---

