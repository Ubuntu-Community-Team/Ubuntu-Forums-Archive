---
title: "xubuntu 18.04 Screen lock + lid close suspends the system"
date: 2018-05-02
forum: Desktop Environments
---

### Post by alt.dot-travelling on 2018-05-02
I think this is a bug but not sure.

When the screen is locked using either ctrl+alt+l or through power manager settings (when laptop lid is closed selection) and the laptop lid is closed, the system suspends.

It doesn't happen when screen is locked but left open or when lid is closed with no screen lock and screen is set to "switch off display" in laptop close lid settings in power manager.
After long periods it can become very tricky to log back in.

Any suggestions or help appreciated.
If it is a bug could I have some help with the bug reporting for xubuntu.  I've had a try but it doesn't crash the system but i have needed to do a hard shutdown.

---

### Post by kazakore on 2018-05-02
I've NEVER got screen locking to work in XFCE Ubuntu (Xubuntu/Ubuntu Studio.) It's part of the reason I'm considering a migration to MATE.....

---

### Post by alt.dot-travelling on 2018-05-02
XFCE is my favourite desktop so I'm reluctant to switch..
I only go for the LTS versions as I like stability (and not having to upgrade too often).  It was working fine in 16.04.04

---

### Post by kazakore on 2018-05-02
XFCE always been my favourite as well. Having given a few another go lately I have found MATE to be pretty decent too.

Although screen locking is kinda working for me at the moment for the first time in XFCE (Ubuntu Studio 18.04.) It gives me an error message on screen saving none of the installed screen lockers activated but then it turns out it is in fact locked....

(EDIT: hmmm well sometimes it does, sometimes it doesn't lock but always I get a message saying it hasn't.)

---

### Post by noxeternal on 2018-05-03
I'm having an extremely similar issue. Unable to get the system back up after locking.

Xorg.0.log shows all my USB devices dropping when the screen locks (manually or after idle timeout). I can't even add a new one, dmesg shows it attach, but I get no usage out of it.

---

### Post by alt.dot-travelling on 2018-05-03
I've tried and *sometimes* if I close the lid again for a few seconds, I can log back in after that.
Sometimes...
It's worth a try though

---

### Post by junaidahmed2 on 2018-05-03
xfce4-power-manager is verry buggy. When screen off on sleep is on, it can't turn off screen on lid close while running on battery power it'll always go to sleep. On AC power, it can turn off the screen but the option "Swith off display" has to be selected for both battery and AC power mode.

---

### Post by alt.dot-travelling on 2018-05-04
I have filed a bug report
[https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1769061](https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1769061)

If it's affecting you as well feel free to mark it as so

---

