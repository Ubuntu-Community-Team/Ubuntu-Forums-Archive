---
title: "Multimedia Buttons Dell Studio 15"
date: 2008-12-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by wonderbriefs on 2008-12-14
I have a Dell Studio 1535 with Ubuntu 8.04 preinstalled.
This morning my Multimedia keys all stopped responding. The Eject button is lit up, no matter if I put a CD in or not. The buttons light up and scroll back and forth when I turn the power on, then the Eject button lights up, and they all stop responding.

---

### Post by markoh on 2008-12-16
Sounds like something is broken.

You may try booting from Ubuntu Desktop CD or some other live distro to see if it is related to your Ubuntu installation it's connected to the laptop itself...

---

### Post by bloodofangels302 on 2008-12-16
I have the exact same problem! Except for me it only happens on occasion.  Unfortunately through some searching I found that it is a common problem with all studio 15s.  It apparently has something to do with static buildup on the touch panel.  I read reports that shutting down and taking out the battery for a couple seconds can fix the problem temporarily.  I have learned to live with it because it does not happen to often for me.  Sorry I could not be of more help.  By the way do you happen to know how to get these media controls to work for amarok do you?  They light up when I touch them but I can't get them to become shortcut keys for some reason.

---

### Post by EnergySamus on 2009-01-10
All you have to do is take out the battery, and then hold the power button down for about 30 seconds, that will do the trick!

---

### Post by bellylint on 2009-02-27
I had a similar problem with my new Studio 1535 and the eject button; however, I called Dell and they mentioned it was a known issue with the media control panel itself.

They sent me a replacement control panel which was easily replaced by following the Dell Manual available online ( [http://support.dell.com/support/edocs/systems/1535/en/SM/index.htm](http://support.dell.com/support/edocs/systems/1535/en/SM/index.htm) )

Next thing you also need to do is edit the sysctl.conf file in order to allow the drive to acknowledge eject commands coming from the media control panel...
*Open a terminal and type...*

sudu gedit /etc/sysctl.conf

*add the following command to the bottom of the text...*

#allow eject of cdrom using eject button
dev.cdrom.lock=0

Save & close...and that's it!  By the way Ubuntu runs great on a Dell!

---

### Post by gagnon88 on 2009-03-09
> 
Open a terminal and type...

sudu gedit /etc/sysctl.conf

add the following command to the bottom of the text...

#allow eject of cdrom using eject button
dev.cdrom.lock=0


That did the trick on my Studio 15. Thanks a lot!

EDIT: The problem is back when the system resumes from suspend, and I have to reboot to get that fixed. So it does the trick, but only partially.

---

