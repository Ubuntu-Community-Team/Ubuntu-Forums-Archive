---
title: "Update to 2.6.32-24 screwed up my graphics"
date: 2010-07-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by the_poolster on 2010-07-27
Today I had an odd problem. I had updated my linux headers during a usual update (see bottom of post for log). On restart(required) my display had gone wrong. I have a Dell Optiplex 980/ATI graphics with two monitors with one of them rotated 90 degrees. 

Messages appeared like "low graphics mode", "fglrx(0) Hasn't established DRM connection", "atiddxDriScreenInit failed", "XMM failed to open CMMQS" etc etc. I was given the option to change to a default and upon restart: black screen = me very sad. :-((

Restarted back into 2.6.32-23 with grub and display was two cloned monitors. Still sad, but less so. :-(

Trying to load up ATI catalyst control centre caused a message that I had no ATI drivers installed! Under Hardware drivers it was installed.

Clearly, then this is a case for uninstall/reinstall (Windows taught me something ;-) But fglrx would not reinstall. Still sad, slightly more now, but not as much as before, with a little bit of confusion. :-S

Problem was solved (I have no idea why!) by unistalling gcc, reinstalling gcc, reinstalling fglrx and restarting into 2.6.32.24.

Is there some conflict between the proprietary ATI drivers and the new headers? Anyone? 


Commit Log for Tue Jul 27 08:07:21 2010


Upgraded the following packages:
apt (0.7.25.3ubuntu9) to 0.7.25.3ubuntu9.1
apt-transport-https (0.7.25.3ubuntu9) to 0.7.25.3ubuntu9.1
apt-utils (0.7.25.3ubuntu9) to 0.7.25.3ubuntu9.1
base-files (5.0.0ubuntu20) to 5.0.0ubuntu20.10.04.1
firefox (3.6.7+build2+nobinonly-0ubuntu0.10.04.1) to 3.6.8+build1+nobinonly-0ubuntu0.10.04.1
firefox-branding (3.6.7+build2+nobinonly-0ubuntu0.10.04.1) to 3.6.8+build1+nobinonly-0ubuntu0.10.04.1
firefox-gnome-support (3.6.7+build2+nobinonly-0ubuntu0.10.04.1) to 3.6.8+build1+nobinonly-0ubuntu0.10.04.1
icedtea-6-jre-cacao (6b18-1.8-0ubuntu1) to 6b18-1.8-4ubuntu3
linux-generic-pae (2.6.32.23.24) to 2.6.32.24.25
linux-headers-generic-pae (2.6.32.23.24) to 2.6.32.24.25
linux-image-generic-pae (2.6.32.23.24) to 2.6.32.24.25
linux-libc-dev (2.6.32-23.37) to 2.6.32-24.38
openjdk-6-jre (6b18-1.8-0ubuntu1) to 6b18-1.8-4ubuntu3
openjdk-6-jre-headless (6b18-1.8-0ubuntu1) to 6b18-1.8-4ubuntu3
openjdk-6-jre-lib (6b18-1.8-0ubuntu1) to 6b18-1.8-4ubuntu3
thunderbird (3.0.5+build2+nobinonly-0ubuntu0.10.04.1) to 3.0.6+build2+nobinonly-0ubuntu0.10.04.1
ureadahead (0.100.0-4.1) to 0.100.0-4.1.2
xulrunner-1.9.2 (1.9.2.7+build2+nobinonly-0ubuntu0.10.04.1) to 1.9.2.8+build1+nobinonly-0ubuntu0.10.04.1

Installed the following packages:
linux-headers-2.6.32-24 (2.6.32-24.38)
linux-headers-2.6.32-24-generic-pae (2.6.32-24.38)
linux-image-2.6.32-24-generic-pae (2.6.32-24.38)

---

### Post by jimbarfield on 2010-07-27
2.6.32-24-generic updates with success on Compaq CQ60-211DX.  Firefox, Python, and gcc all updated at the same time, along with Drop Box.  However, I had 3 copies of my gDesklets upon reboot on my desktop...

---

### Post by dodoknight on 2010-08-18
I had the same problem with my xubuntu I uninstalled and reinstalled gcc and fglrx but It didn't solved my problem. Then I thought I should reinstall Ati's drivers. However, when I started "hardware drivers" from settings I saw that my ati driver was not activated. I activated the driver and restarted system. Everything worked fine no low graphic mode error.

---

### Post by liedan on 2010-08-18
Same problem here, although  I don't remember details.
I simply reverted to 2.6.32.23 and will wait for 2.6.25 hoping that it will be solved.

---

### Post by hamsandwich on 2010-09-18
Sorry to post on an older thread, but for the sake of those running into this problem now (like me) I think the word SOLVED at the top of the thread is misleading. I also updated at the prompting of the update manager gui, just agreeing to whatever it was suggesting, which happened to include the upgrade to 2.6.32-24, and on next boot, the proprietary ATI fglrx driver was not working. I can tell because without it, my 5800 series card's fan runs full blast, noisy as hell. Graphics were full resolution, and "Hardware Drivers" control panel showed the driver as available but not installed! I tried to install it and got an error about fglrx-installer failing, and to check /var/log/jockey.log. So the driver would not install on 2.6.32-24. I reverted to an earlier working version and everything was fine. 

The proprietary fglrx driver does not seem to play nice with 2.6.32-24, and like somebody else here said, maybe it will be fixed in 2.6.32-25.

---

