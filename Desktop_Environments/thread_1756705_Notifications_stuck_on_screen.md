---
title: "Notifications stuck on screen"
date: 2011-05-12
forum: Desktop Environments
---

### Post by tpprynn on 2011-05-12
I use Mobile Broadband, I don't know if this happens with wireless  internet. If for example I disconnect, the Notification balloon, unlike  most other Notification balloons, just stays there until I click its  top-right X. Is there something I can edit to put that right? If I eject  a drive for example the balloon fades out correctly, and I remember  that there was a GUI-represented setting to control the duration of its  staying on-screen, but somehow this doesn't happen for all balloons.
Thanks for any info.

(Xubuntu 11.04, Xfce 4.8, Toshiba laptop with Intel 965 graphics)

---

### Post by tpprynn on 2011-05-12
A screenshot. Unlike the 'This drive was automatically mounted' notification this one stays on the screen.

---

### Post by noah++ on 2011-10-09
Yep, I have the same problem with WiFi. NetworkManager applet's notifications just don't time out. Same thing for Jupiter (a power management daemon). I'm also on Xubuntu 11.04.

[This thread]("http://ubuntuforums.org/showthread.php?p=11148758") provides a method for disabling certain notifications entirely. I just want them to time out, though.

---

### Post by Toz on 2011-10-09
If you go to Settings Manager -> Notifications, you can set the notification display time. What value do you have there?

---

### Post by noah++ on 2011-10-09
I had 0 seconds there. I changed it to 3. Fixed! Thanks.

---

### Post by noah++ on 2011-10-09
Nope, I was wrong. Some notifications from NM, and all from Jupiter, are persisting until I close them. Help!

---

### Post by Toz on 2011-10-09
Which of the following notification daemons do you have installed:
```
apt-cache policy notify-osd
apt-cache policy notification-daemon
apt-cache policy xfce4-notifyd
```

I only have the last one installed. If you've got the others, maybe they're conflicting. Do you have a fresh xubuntu install or did you install xubuntu-desktop on another version of *buntu?

---

### Post by noah++ on 2011-10-09
Thanks for the response. I'm using the Xubuntu Linux distribution. Here is the output from those commands.

```
$ apt-cache policy notify-osd
notify-osd:
  Installed: (none)
  Candidate: 0.9.30-0ubuntu4
  Version table:
     0.9.30-0ubuntu4 0
        500 http://us.archive.ubuntu.com/ubuntu/ natty/main amd64 Packages

$ apt-cache policy notification-daemon
notification-daemon:
  Installed: (none)
  Candidate: 0.5.0-2ubuntu1
  Version table:
     0.5.0-2ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ natty/main amd64 Packages

$ apt-cache policy xfce4-notifyd
xfce4-notifyd:
  Installed: 0.2.1-1
  Candidate: 0.2.1-1
  Version table:
 *** 0.2.1-1 0
        500 http://us.archive.ubuntu.com/ubuntu/ natty/universe amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by Toz on 2011-10-10
What is the contents of your file: **~/.gconf/apps/nm-applet/%gconf.xml**?

I'm also curious whether this happens only to your account or to all accounts on the system. Is it possible to log in with another account and see if the problem persists?

And also, any way you could upload an image of one of the network-manager notifications that are stuck?

---

### Post by noah++ on 2011-10-10
Screenshot attached. Jupiter and NM notifications persist. Xfce Power Manager notifications fade after about 3 seconds, per my setting. Should I maybe disable the Xfce notifications and enable one of the others?

```
<?xml version="1.0"?>
<gconf>
    <entry name="suppress-wireless-networks-available" mtime="1316564364" type="bool" value="true"/>
    <entry name="disable-connected-notifications" mtime="1310707563" type="bool" value="true"/>
    <entry name="stamp" mtime="1292654440" type="int" value="1"/>
</gconf>
```

---

### Post by Toz on 2011-10-11
Lets try reverting your nm-applet gconf file back to default:
```
cp ~/.gconf/apps/nm-applet/%gconf.xml ~/.gconf/apps/nm-applet/%gconf.xml.bak
```

Then edit the **~/.gconf/apps/nm-applet/%gconf.xml** file and delete the first two <entry name> entries so that it looks like this:
```
<?xml version="1.0"?>
<gconf>
    <entry name="stamp" mtime="1292654440" type="int" value="1"/>
</gconf>
```

Any change? If not, try logging out and back in again. Check the contents of the file that it hasn't changed. 

Any change now?

---

### Post by noah++ on 2011-10-12
I switched to notify-osd, which doesn't have this issue for me.

---

### Post by tpprynn on 2011-10-13
Better yet, the issue doesn't exist in Xubuntu 11.10, which I've been trying out today. I did soon change the default from 10 seconds to 5 though (in Settings> Settings Manager > Notifications).

---

