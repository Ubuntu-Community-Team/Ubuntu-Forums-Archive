---
title: "Graphical login fails after 10.04 kernel and xorg update on Inspiron 530"
date: 2011-04-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lenveen on 2011-04-29
Hi, I need help with a major issue. I run Ubuntu 10.04 on Dell Inspiron 530 desktop with an Intel quad code chip and Intel graphics chipset (Intel Corporation 82G33/G31 Express Integrated Graphics Controller rev 2).
I never had any issues before, but just a few days ago I let Update Manager install a bunch of packages, including a kernel update and xorg server updates. In /var/log/dpkg.log I see
2011-04-26 09:20:12 upgrade linux-image-generic 2.6.32.30.36 2.6.32.31.37
2011-04-26 11:32:26 upgrade xserver-xorg-core 2:1.7.6-2ubuntu7.5 2:1.7.6-2ubuntu7.6
Update Manager finished without warnings or errors and prompted me to reboot. After rebooting, the
login screen comes up. When I log in, I see a black screen with a few lines of text for a split second, then I 
go back to the login screen. If I press cntr+alt+F1 I can login on the command line.

Of course, in this state my machine is pretty much useless. I would be happy to revert to the previous
configuration and wait for the news LTS release before upgrading anything, but I am not sure how to do that,
especially with only a command line. Right now I am running a live CD to post this message.

Any help would be greatly appreciated.

---

### Post by lenveen on 2011-05-19
Problem solved. As it turned out, this is a recurring problem with a work around.
At the end of the dmesg output I found a line like this:
type=1503 audit(1273121515.902:17): operation="open" pid=1673 parent=1536 profile="/usr/share/gdm/guest-session/Xsession" requested_mask="r::" denied_mask="r::" fsuid=1000 ouid=1000 name="/home/name/.profile"
and in $HOME/xsession-errors there appears a line about .profile not being found. If you search for these messages you will find several similar threads on Ubuntu forums. None of those threads seems to have an explanation, but the work around that saved me was to purge gdm:
sudo apt-get purge gdm
and then reinstall:
sudo apt-get install gdm
sudo apt-get install gdm-session
sudo apr-get install indicator-applet (some packages get purged with gdm but not automatically reinstalled)
then I rebooted and the problem was gone. All this can easily be done from the console or recovery mode.

---

### Post by usna78 on 2011-06-01
I too had this problem after messing with xorg.conf and imwheel.  Purging and re-installing  gdm as described by lenveen worked for me!

---

