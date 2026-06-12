---
title: "clamav?"
date: 2008-04-02
forum: Dell  Ubuntu Support
---

### Post by arvadawest on 2008-04-02
Hi,
We want to use clamav as our virus checker.  When we go to add new programs, the only one that shows up is:  clamtk (not clamav)

We are newbies so we need help in a step-by-step way.  Thank you.

---

### Post by notwen on 2008-04-02
Have you checked out ClamAV's website for detailed instructions?  Click [here]("http://wiki.clamav.net/Main/WebHome#ClamAV_for_beginners") for more info regarding first time installation and upgrades.  

I'm guessing this is your 2nd attempt being your [first]("http://ubuntuforums.org/showthread.php?t=735238") was not very successful?

---

### Post by arvadawest on 2008-04-02
> **notwen said:**
> Have you checked out ClamAV's website for detailed instructions?  Click [here]("http://wiki.clamav.net/Main/WebHome#ClamAV_for_beginners") for more info regarding first time installation and upgrades.  

I'm guessing this is your 2nd attempt being your [first]("http://ubuntuforums.org/showthread.php?t=735238") was not very successful?

Hello, we installed clamav:

sudo apt-get install clamav 

then we went to update definitions and this is what we got (it went on much longer than what I am posting):

[I]~$ sudo apt-get install clamav
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
clamav is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
sector0@ssdnp-ulx001:~$ sudo freshclam
ClamAV update process started at Wed Apr  2 12:56:34 2008
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.90.2 Recommended version: 0.92.1
DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)
main.inc is up to date (version: 45, sigs: 169676, f-level: 21, builder: sven)
Downloading daily-6541.cdiff [100%]
Ignoring mirror 155.98.64.86 (too often connections with outdated version)
ERROR: getpatch: Can't download daily-6542.cdiff from db.local.clamav.net
Downloading daily-6542.cdiff [100%]
Ignoring mirror 208.67.80.27 (too often connections with outdated version)
ERROR: getpatch: Can't download daily-6543.cdiff from db.local.clamav.net[/I]

This has happened before and we do not know what to do.  thanks.

---

### Post by arvadawest on 2008-04-02
I'm guessing this is your 2nd attempt being your [first]("http://ubuntuforums.org/showthread.php?t=735238") was not very successful?[/QUOTE]

Yes, no one ever responded to my problem in the end.  So I thought I would try again.  thank you.

---

### Post by arvadawest on 2008-04-02
> **notwen said:**
>   

I'm guessing this is your 2nd attempt being your [first]("http://ubuntuforums.org/showthread.php?t=735238") was not very successful?

We are sorry, we keep messing this up.  Yes, we need help, but unfortunately we are not getting the help we need or a response to the problem we posted earlier.  Thank you.

---

### Post by Kevbert on 2008-04-02
Hi.  Please take a look at this:
[http://www.ubuntugeek.com/howto-install-clam-antivirus-with-gtk-frontend-gui.html]("http://www.ubuntugeek.com/howto-install-clam-antivirus-with-gtk-frontend-gui.html")

Please note that this will only find Windows viruses.  So unless you are using a Windows emulator or a dual boot (Windows/Linux) system it won't be of much use.
To update virus definitions, run terminal and enter 'sudo clamtk'.  Clamtk will open and from there select Help and then update from the displayed submenu.
Hope this helps!

---

### Post by heartburnkid on 2008-04-02
Installing ClamTK from Add/Remove Programs will likely install ClamAV as well.  That's been my experience with the frontends in there, anyway; installing the frontend will also install the backend.  Worth a shot, anyway, and will give you an easy-to-use GUI.

---

### Post by santiagoward2000 on 2008-04-02
> **heartburnkid said:**
> Installing ClamTK from Add/Remove Programs will likely install ClamAV as well.  That's been my experience with the frontends in there, anyway; installing the frontend will also install the backend.  Worth a shot, anyway, and will give you an easy-to-use GUI.

Exactly! clamtk is a GTK gui for clamav. If you install it, it installs clamav too, and you can use both clamtk or the CLI clamav.
Cheers!

---

