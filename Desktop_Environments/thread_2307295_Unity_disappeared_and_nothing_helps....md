---
title: "Unity disappeared and nothing helps..."
date: 2015-12-23
forum: Desktop Environments
---

### Post by khurtsiya on 2015-12-23
Hi!

Unity disappeared after this command:

sudo apt-get remove unity-scope-home

or

sudo apt-get remove unity-lens-shopping

Ubuntu 14.04 LTS

I have done all that in this thread [http://askubuntu.com/questions/468204/no-panels-or-menus-after-upgrading-to-14-04](http://askubuntu.com/questions/468204/no-panels-or-menus-after-upgrading-to-14-04)

Nothing helped, except I am on GNOME now, but want back to Unity. Help, please!

---

### Post by CantankRus on 2015-12-23
It didn't disappear... you removed it when you removed unity-scope-home as "unity" depends on this package.
So I'm assuming you reinstalled ubuntu-desktop, logged into the "Ubuntu" session and 
used ccsm to enable the "Ubuntu Unity Plugin" as described in your askubuntu link??

---

### Post by khurtsiya on 2015-12-24
Yes. I enabled all, but still no Unity

[IMG]http://i.imgur.com/Ttzkmih.png[/IMG]

---

### Post by CantankRus on 2015-12-24
See pics...

Here's a[**_[COLOR="#B22222"] LINK[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2252171&p=13163967#post13163967") to help in recovery process.

---

### Post by khurtsiya on 2015-12-24
SOLVED

LINK helped, thanks!

---

