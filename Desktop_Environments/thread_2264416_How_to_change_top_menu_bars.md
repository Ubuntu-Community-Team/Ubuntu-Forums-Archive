---
title: "How to change top menu bars?"
date: 2015-02-07
forum: Desktop Environments
---

### Post by hailholyghost on 2015-02-07
[ATTACH=CONFIG]259787[/ATTACH]

Hello,

I recently did a fresh install of Ubuntu 14.10 and I run gnome-session-fallback.  However, the new top menu bars are really bad (on the bottom of the image), I find them very irritating, buttons I am accustomed to have disappeared.

How can I make the bottom menu bar ("bad") look like the top menu bar ("good")?

thanks so much,
-DEC

---

### Post by mc4man on 2015-02-07
For info purposes the results of - 
```
apt-cache policy libgtk-3-0 gedit
```

---

### Post by hailholyghost on 2015-02-07
> **mc4man said:**
> For info purposes the results of - 
```
apt-cache policy libgtk-3-0 gedit
```

```
con@laptop:~$ apt-cache policy libgtk-3-0 gedit
libgtk-3-0:
  Installed: 3.12.2-0ubuntu15.2
  Candidate: 3.12.2-0ubuntu15.2
  Version table:
 *** 3.12.2-0ubuntu15.2 0
        500 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main i386 Packages
        100 /var/lib/dpkg/status
     3.12.2-0ubuntu15 0
        500 http://us.archive.ubuntu.com/ubuntu/ utopic/main i386 Packages
gedit:
  Installed: 3.12.2-0ubuntu1~trusty1
  Candidate: 3.12.2-0ubuntu1~trusty1
  Version table:
 *** 3.12.2-0ubuntu1~trusty1 0
        500 http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/ utopic/main i386 Packages
        100 /var/lib/dpkg/status
     3.10.4-0ubuntu6 0
        500 http://us.archive.ubuntu.com/ubuntu/ utopic/main i386 Packages
```

I have similar problems with Nautilus:
```

con@laptop:~$ apt-cache policy libgtk-3-0 nautilus
libgtk-3-0:
  Installed: 3.12.2-0ubuntu15.2
  Candidate: 3.12.2-0ubuntu15.2
  Version table:
 *** 3.12.2-0ubuntu15.2 0
        500 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main i386 Packages
        100 /var/lib/dpkg/status
     3.12.2-0ubuntu15 0
        500 http://us.archive.ubuntu.com/ubuntu/ utopic/main i386 Packages
nautilus:
  Installed: 1:3.12.2-0ubuntu1~trusty3
  Candidate: 1:3.12.2-0ubuntu1~trusty3
  Version table:
 *** 1:3.12.2-0ubuntu1~trusty3 0
        500 http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/ utopic/main i386 Packages
        100 /var/lib/dpkg/status
     1:3.10.1-0ubuntu15 0
        500 http://us.archive.ubuntu.com/ubuntu/ utopic/main i386 Packages
```

---

### Post by Frogs Hair on 2015-02-07
I had a similar result when adding the PPA for Gnome 3.12 packages that didn't make it into Ubuntu. That PPA upgrades Gedit to 3.12 and the GUI layout is different. A Gedit 3.10 image is below.

---

### Post by mc4man on 2015-02-07
You are using the gnome3 ppa versions of gedit & nautilus so you're getting how Gnome sets up the toolbar now (or close to

I don't use those gnome ppa's or gnome sessions so can't say if there is a way to get the 'older' styles with these packages.
I'd assume all the toolbar options are there somewhere, just not individually on the toolbar.

The obvious 'solution' would be to use ppa-purge & return gedit & nautilus to 14.10 default versions (3.10

---

### Post by hailholyghost on 2015-02-08
> **mc4man said:**
> You are using the gnome3 ppa versions of gedit & nautilus so you're getting how Gnome sets up the toolbar now (or close to

I don't use those gnome ppa's or gnome sessions so can't say if there is a way to get the 'older' styles with these packages.
I'd assume all the toolbar options are there somewhere, just not individually on the toolbar.

The obvious 'solution' would be to use ppa-purge & return gedit & nautilus to 14.10 default versions (3.10

Hi mc4man,

would you be able to provide a sample of the required command? I could not find a guide on internet search to clarify your answer.

thanks,
-DEC

---

### Post by CantankRus on 2015-02-08
Install ppa-purge...
```
sudo apt-get install ppa-purge
```

To use ppa-purge, the ppa you added must still be enabled.
You can search and open "software and updates" in the dash or open
it via terminal....
```
software-properties-gtk --open-tab 1
```
Check in your sources for the ppa used and if necessary enable it.

In software and updates, choose to edit the ppa and from the "**URI**" line you will get something like....
```
http://ppa.launchpad.net/[COLOR="#FF0000"]ricotz/docky[/COLOR]/ubuntu
```
In this example [COLOR="#FF0000"]ricotz/docky[/COLOR] corresponds to **ppaowner/ppaname**
Highlight and copy this part of the URI
Close software and updates and choose to reload if asked.

To purge a ppa you use ```
ppa-purge ppa:[COLOR="#696969"]<ppaowner/ppaname>[/COLOR]
```
So for this example it would be...
```
sudo ppa-purge ppa:[COLOR="#FF0000"]ricotz/docky[/COLOR]
```

Use the same method to purge your added ppa.

---

